using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Navigation;
//using System.Windows.Shapes;
using Microsoft.Phone.Controls;
using Microsoft.Xna.Framework;
using Microsoft.Xna.Framework.Content;
using Microsoft.Xna.Framework.Graphics;
//using System.Threading;
using System.Windows.Threading;
using System.Threading;
using Microsoft.Xna.Framework.Input;
using Microsoft.Xna.Framework.Input.Touch;



namespace SlXnaApp1
{
    public partial class GamePage : PhoneApplicationPage
    {
        ContentManager contentManager;
        GameTimer timer;
        SpriteBatch spriteBatch;
        Texture2D circle;
        SpriteFont drawFont;
        Vector2 position, mousePosition;
        Rectangle circle1, circle2, circle3, circle4, circle5;
        TimeSpan Start;
        bool YokEt,bitiş;
        bool[] fare = new bool[5];
        int[] sayı = new int[5];
        int[] indis = new int[5];
        int min;
        int[] indeksler = new int[5];
        List<int> liste;

        public GamePage()
        {
            InitializeComponent();

            // Get the content manager from the application
            contentManager = (Application.Current as App).Content;

            Random rnd = new Random();
            liste = new List<int>();
            for (int i = 0; i < 5; i++)
            {
                sayı[i] = rnd.Next(50);
                liste.Add(sayı[i]);
            }


            min = 0;
            for (int i = 0; i < sayı.Length; i++)
            {
                for (int j = 0; j < sayı.Length; j++)
                {
                    if (liste[j] < liste[min])
                        min = j;
                }
                indeksler[i] = min;
                liste[min] = 1000;
            }
            liste.Clear();
            for (int i = 0; i < 5; i++)
                liste.Add(indeksler[i]);
            // Create a timer for this page
            timer = new GameTimer();

            timer.UpdateInterval = TimeSpan.FromTicks(333333);
            timer.Update += OnUpdate;
            timer.Draw += OnDraw;
        }

        protected override void OnNavigatedTo(NavigationEventArgs e)
        {
            // Set the sharing mode of the graphics device to turn on XNA rendering
            SharedGraphicsDeviceManager.Current.GraphicsDevice.SetSharingMode(true);

            // Create a new SpriteBatch, which can be used to draw textures.
            spriteBatch = new SpriteBatch(SharedGraphicsDeviceManager.Current.GraphicsDevice);
            circle = contentManager.Load<Texture2D>("circle");
            drawFont = contentManager.Load<SpriteFont>("Tahoma");
            circle1 = new Rectangle(10, 10, 100, 100);
            circle2 = new Rectangle(370, 10, 100, 100);
            circle3 = new Rectangle(140, 300, 200, 200);
            circle4 = new Rectangle(10, 690, 100, 100);
            circle5 = new Rectangle(370, 690, 100, 100);

            // TODO: use this.content to load your game content here
            YokEt = false;
            bitiş = false;
            for (int i = 0; i < 5; i++)
                fare[i] = false;
            Start = TimeSpan.Zero;

            timer.Start();

            base.OnNavigatedTo(e);
        }

        protected override void OnNavigatedFrom(NavigationEventArgs e)
        {
            // Stop the timer
            timer.Stop();

            // Set the sharing mode of the graphics device to turn off XNA rendering
            SharedGraphicsDeviceManager.Current.GraphicsDevice.SetSharingMode(false);

            base.OnNavigatedFrom(e);
        }

        /// <summary>
        /// Allows the page to run logic such as updating the world,
        /// checking for collisions, gathering input, and playing audio.
        /// </summary>
        private void OnUpdate(object sender, GameTimerEventArgs e)
        {
            if ((e.TotalTime - Start).TotalMilliseconds >= 4500)
            {
                YokEt = true;
            }
        
            foreach (var item in TouchPanel.GetState())
            {
                if (item.State == TouchLocationState.Pressed)
                {
                    mousePosition.X = item.Position.X;
                    mousePosition.Y = item.Position.Y;
                }

                break;
            }
            if (liste.Count > 0)
            {
                switch (liste[0])
                {
                    case 0:
                        if (mousePosition.X < circle1.X + 100 && circle1.X < mousePosition.X)
                            if (mousePosition.Y < circle1.Y + 100 && circle1.Y < mousePosition.Y)
                            {
                                fare[0] = true;
                                liste.RemoveAt(0);
                            }
                        break;
                    case 1:
                        if (mousePosition.X < circle2.X + 100 && circle2.X < mousePosition.X)
                            if (mousePosition.Y < circle2.Y + 100 && circle2.Y < mousePosition.Y)
                            {
                                fare[1] = true;
                                liste.RemoveAt(0);
                            }
                        break;
                    case 2:
                        if (mousePosition.X < circle3.X + 200 && circle3.X < mousePosition.X)
                            if (mousePosition.Y < circle3.Y + 200 && circle3.Y < mousePosition.Y)
                            {
                                fare[2] = true;
                                liste.RemoveAt(0);
                            }
                        break;
                    case 3:
                        if (mousePosition.X < circle4.X + 100 && circle4.X < mousePosition.X)
                            if (mousePosition.Y < circle4.Y + 100 && circle4.Y < mousePosition.Y)
                            {
                                fare[3] = true;
                                liste.RemoveAt(0);
                            }
                        break;
                    case 4:
                        if (mousePosition.X < circle5.X + 100 && circle5.X < mousePosition.X)
                            if (mousePosition.Y < circle5.Y + 100 && circle5.Y < mousePosition.Y)
                            {
                                fare[4] = true;
                                liste.RemoveAt(0);
                            }
                        break;

                }
            }
            else
                bitiş=true;
        
            // TODO: Add your update logic here
        }

        /// <summary>
        /// Allows the page to draw itself.
        /// </summary>
        /// 

        private void OnDraw(object sender, GameTimerEventArgs e)
        {
            SharedGraphicsDeviceManager.Current.GraphicsDevice.Clear(Color.CornflowerBlue);

            spriteBatch.Begin();
            if (!fare[0])
                spriteBatch.Draw(circle, circle1, Color.CornflowerBlue);
            if (!fare[1])
                spriteBatch.Draw(circle, circle2, Color.CornflowerBlue);
            if (!fare[2])
                spriteBatch.Draw(circle, circle3, Color.CornflowerBlue);
            if (!fare[3])
                spriteBatch.Draw(circle, circle4, Color.CornflowerBlue);
            if (!fare[4])
                spriteBatch.Draw(circle, circle5, Color.CornflowerBlue);

            int[] x = { circle1.X + 30, circle2.X + 30, circle3.X + 60, circle4.X + 30, circle5.X + 30 };
            int[] y = { circle1.Y + 30, circle2.Y + 30, circle3.Y + 60, circle4.Y + 30, circle5.Y + 30 };

            if (!YokEt)
            {
                for (int i = 0; i < 5; i++)
                {
                    position = new Vector2(x[i], y[i]);

                    spriteBatch.DrawString(drawFont, "" + sayı[i], position, Color.White);
                }
            }
            if (bitiş)
            {
                position.X = 120;
                position.Y = 400;
                spriteBatch.DrawString(drawFont, "Congratulations\n you won!", position, Color.Yellow);
            }
            spriteBatch.End();


            // TODO: Add your drawing code here
        }

        private void PhoneApplicationPage_Loaded(object sender, RoutedEventArgs e)
        {

        }
    }
}
