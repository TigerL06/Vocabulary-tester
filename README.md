# Vocabulary-tester

**Code**
 
 Console.WriteLine();
            int index=0;
            string[] Antwort = new string[19];
           
                for (int Wörter = 0; Wörter == 20; Wörter++)
                {
                    var rnd = new Random();
                    index = rnd.Next(0, 210);

                    Console.WriteLine();
                    Antwort[Wörter] = Console.ReadLine();

                    for (int j = 0; j < dataArray[i].Length; j++)
                    {
                        if ()
                        {

                        }
                        if ()
                        {

                        }
                    }

                }

**code**
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
