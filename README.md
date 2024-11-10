# prakt_1
 Создание интерактивной игры
using System;

class Game
{
    static void Main(string[] args)
    {
        string playerName;
        bool hasArtifact1 = false;
        bool hasArtifact2 = false;
        bool hasArtifact3 = false;
        bool hasKey = false;
        bool hasLockpick = false;

        Console.WriteLine("Вы просыпаетесь в комнате. Пожалуйста, введите ваше имя:");
        playerName = Console.ReadLine();

        while (true)
        {
            Console.WriteLine($"Что вы хотите сделать, {playerName}?");
            Console.WriteLine("1. Открыть дверь");
            Console.WriteLine("2. Заглянуть под кровать");
            Console.WriteLine("3. Открыть ящик в углу комнаты");
            Console.WriteLine("4. Открыть вентиляцию");
            Console.WriteLine("5. Взглянуть на тумбочку");
            Console.WriteLine("6. Взглянуть на статую рядом с дверью");
            Console.WriteLine("Введите номер действия:");

            string choice = Console.ReadLine();

            switch (choice)
            {
                case "1":
                    if (hasLockpick)
                    {
                        Console.WriteLine($"{playerName}, вы открыли дверь и успешно сбежали!");
                        return;
                    }
                    else
                    {
                        Console.WriteLine($"{playerName}, дверь заперта. Вам нужна отмычка.");
                    }
                    break;
                case "2":
                    if (!hasArtifact1)
                    {
                        hasArtifact1 = true;
                        Console.WriteLine($"{playerName}, вы нашли первый артефакт под кроватью!");
                    }
                    else
                    {
                        Console.WriteLine($"{playerName}, вы уже искали под кроватью.");
                    }
                    break;
                case "3":
                    if (!hasKey)
                    {
                        hasLockpick = true;
                        Console.WriteLine($"{playerName}, вы открыли ящик и нашли отмычку!");
                    }
                    else
                    {
                        Console.WriteLine($"{playerName}, вы уже открывали ящик.");
                    }
                    break;
                case "4":
                    if (!hasArtifact2)
                    {
                        Console.WriteLine($"{playerName}, вы открываете вентиляцию...");
                        for (int i = 0; i < 3; i++)
                        {
                            Console.WriteLine("Пытаетесь открыть вентиляцию...");
                        }
                        hasArtifact2 = true;
                        Console.WriteLine($"{playerName}, вы нашли второй артефакт в вентиляции!");
                    }
                    else
                    {
                        Console.WriteLine($"{playerName}, вы уже искали в вентиляции.");
                    }
                    break;
                case "5":
                    if (!hasArtifact3)
                    {
                        hasArtifact3 = true;
                        Console.WriteLine($"{playerName}, вы нашли третий артефакт на тумбочке!");
                    }
                    else
                    {
                        Console.WriteLine($"{playerName}, вы уже смотрели на тумбочку.");
                    }
                    break;
                case "6":
                    if (hasArtifact1 && hasArtifact2 && hasArtifact3)
                    {
                        hasKey = true;
                        Console.WriteLine($"{playerName}, вы активировали статую и получили ключ от ящика!");
                    }
                    else
                    {
                        Console.WriteLine($"{playerName}, для активации статуи вам нужны все три артефакта.");
                    }
                    break;
                default:
                    Console.WriteLine("Неверный ввод. Пожалуйста, выберите номер действия от 1 до 6.");
                    break;
            }
        }
    }
}
