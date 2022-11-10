# Vocabulary-tester

**Code**


```c#
namespace Vocabulary_tester
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine();
            int Falsch = 0;
            int index=0;
            int Durchschnitt = 0;
            bool r = false;
            string[] Antwort = new string[19];
           var item = new List<string>();
           var data = new List<List<string>>();
           string file = @"C:\Users\kochl\Desktop\IMS\BBB\Programmier Projekt\Englische Wörter.txt";
           data = ReadFromFile(file);
           string Deutsch = @"C:\Users\kochl\Desktop\IMS\BBB\Programmier Projekt\Deutsche Wörter.txt";
           string[] DeutscheWörter = File.ReadAllLines(Deutsch);
            
           
            string[][] EnglischWörter = data.Select(a => a.ToArray()).ToArray(); 

            for(int Zahl=0; Zahl == 20; Zahl++)
            {
                var rnd = new Random();
                index = rnd.Next(0, 210);

                Console.WriteLine();


                for (int j = 0; j < EnglischWörter[index].Length; j++)
                {
                    Console.WriteLine();
                    Antwort[Zahl] = Console.ReadLine();
                    if (Antwort[Zahl] == EnglischWörter[index][j])
                    {
                        r = true;
                    }
                    if (r == false)
                    {
                        Falsch++;
                    }
                }

                

            }

            Durchschnitt = Falsch / 20;
            Durchschnitt *= 100;
        }

        
        static List<List<string>> ReadFromFile(string filename)
        {
            var fileItem = new List<string>();
            var fileData = new List<List<string>>();
            using (var sr = new StreamReader(filename))
            {
                string line;
                while ((line = sr.ReadLine()) != null)
                {
                    fileItem = line.Split('\t').ToList();
                    fileData.Add(fileItem);
                }
                return fileData;
            }

          
          
        }
    }
}
```

Hier unten ist die aktuelle Version.

**Code 2**
```c#
namespace Vocabulary_tester
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine();
            string[] Antwort = new string[20];
            int[] Antwort2 = new int[20];
            int Falsch = 0;
            int Resultat = 0;
            int index = 0;
            bool r = false;
            int ri = 0;



            string Englisch = @"C:\Users\kochl\Desktop\IMS\BBB\Programmier Projekt\Englische Wörter.txt";
            var englischDaten = ReadFromFile(Englisch);
            string[][] EnglischWoerter = englischDaten.Select(a => a.ToArray()).ToArray();

            string Deutsch = @"C:\Users\kochl\Desktop\IMS\BBB\Programmier Projekt\Deutsche Wörter.txt";
            string[] DeutscheWörter = File.ReadAllLines(Deutsch);



            Console.WriteLine("Herzlich willkommen zum englisch Voci abfrage.");
            for (int Zahl = 0; Zahl < 20; Zahl++)
            {
                var rnd = new Random();
                index = rnd.Next(0, EnglischWoerter.Length);
                Console.Write($"Geben sie das englische Wort von dem deutschen Wort {DeutscheWörter[index]} ein.");
                Antwort[Zahl] = Console.ReadLine();

                bool richtig = false;


                for (int j = 0; j < EnglischWoerter[index].Length; j++)
                {


                    if (Antwort[Zahl] == EnglischWoerter[index][j])
                    {
                        richtig = true;
                    }

                    if (richtig == false)
                    {
                        Antwort2[Zahl] = index;
                        Falsch++;

                    }
                }

            }

            Console.WriteLine();

            ri = 20 - Falsch;
            Resultat = (Falsch / 20) * 100;
            Resultat = Resultat - 100;
            Console.WriteLine($"Sie hatten {ri} von 20 ");
            Console.WriteLine($"Sie haten {Resultat} Prozent richtig");

            for (int x = 0; x < Falsch; x++)
            {

                Console.Write("Das hier ist ihre Antwort:");
                Console.Write(Antwort[x]);

                Console.WriteLine();

                Console.Write("Das hier wäre die richtige Antwort:");
                
                for (int y = 0; y < EnglischWoerter[Antwort2[x]].Length; y++)
                {
                    Console.Write(EnglischWoerter[Antwort2[x]][y]);
                }
            }

        }

        
        static List<List<string>> ReadFromFile(string filename)
        {
           
            var fileData = new List<List<string>>();
            using (var sr = new StreamReader(filename))
            {
                string line;
                while ((line = sr.ReadLine()) != null)
                {
                    var fileItem = line.Split('\t').ToList();
                    fileData.Add(fileItem);
                }
                return fileData;
            }

          
          
        }
    }
}
```
