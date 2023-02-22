using SFML.Graphics;
using SFML.Window;
using System;
using SFML.Learning;
class Program : Game
{ 
    static Random rnd = new Random();
    static int R1;
    static int R2 = 10;
    static int Drow = 1;
    static int speed = 1;
    static int Scor = 0;


    static void Initialize()
    {
         R1 = rnd.Next(120, 180);
         R2 = R1 / 3;
    }
    
    static void DorwSack()
    {
        SetFillColor(Color.Blue);
        FillCircle(580, 380, R1);
        SetFillColor(Color.Red);
        FillCircle(580, 380, R1-10);
        SetFillColor(Color.Yellow);
        FillCircle(580, 380, R1 - 30);
        SetFillColor(Color.Black);
        FillCircle(580, 380, R1 - R1+5);
        SetFillColor(Color.Green);
        FillCircle(580, 380, R2);
    }
    static void  Main()
    {
        InitWindow(800, 600);
        SetFont("comic.ttf");
        Initialize();
        
        

        while (true)
        {
            if (Scor > 10) speed = 2;
            if (Scor > 40) speed = 3;
            if (Scor > 80) speed = 4;
            if (Scor > 100) speed = 5;
            R2 += speed * Drow;

            if (R2 >= R1|| R2 <= 10)
            {
                Drow *= -1;
               // Scor -=2;
             
            }
           
            if (GetKeyDown(Keyboard.Key.Space) ==true)
            {
                if (R2 > R1 - 10)
                {
                    Initialize();
                    Scor = Scor + 10;
                    
                }
                if (R2 > R1 - 30)
                {
                    Initialize();
                    Scor = Scor + 5;
                    
                }
                if (R2 > R1 - 50)
                {
                    Initialize();
                    Scor = Scor + 1;
                    
                }
             

            }
            
            
            //
            DisplayWindow();
            ClearWindow();
            //

            DorwSack();
            

            DrawText(0, 0,$"Счёт: {Scor}", 20);
            DrawText(0, 20, $"Рекорд: {Scor}", 20);

            Console.WriteLine(speed);

            //
            DispatchEvents();
            Delay(1);
        }
    }
}
