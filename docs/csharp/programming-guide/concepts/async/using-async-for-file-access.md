---
title: Použití modifikátoru Async pro přístup k souborům (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: bbaeb14d5c17665308932c26a0630f1e9e5dabdf
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677224"
---
# <a name="using-async-for-file-access-c"></a>Použití modifikátoru Async pro přístup k souborům (C#)
Můžete použít funkci async pro přístup k souborům. Pomocí asynchronní funkce může volat do asynchronní metody bez pomocí zpětných volání a rozdělení kódu mezi více metodách a výrazech lambda. Aby synchronního kódu asynchronní, stačí volání asynchronní metody namísto synchronní metody a do kódu přidat několik klíčových slov.  
  
 Můžete zvážit následující důvody pro přidání asynchronii volání přístup k souboru:  
  
-   Asynchronie urychluje uživatelského rozhraní aplikace odezvu vzhledem k tomu, že vlákno uživatelského rozhraní, který se spustí operace můžete provádět jinou práci. Pokud vlákno uživatelského rozhraní musí být spuštěn kód, který trvá moc dlouho (například více než 50 MS), uživatelské rozhraní může zablokovat až do dokončení vstupy/výstupy a znovu zpracovávat klávesnice a myš události vstupu a jiné vlákno uživatelského rozhraní.  
  
-   Asynchronie zlepšuje škálovatelnost technologie ASP.NET a jiných serverových aplikací tím, že snižuje potřebu vlákna. Pokud aplikace používá vyhrazeném vlákně na odpověď a jsou právě tisíc požadavky zpracovávány současně, nejsou potřeba tisíc vlákna. Asynchronních operací často není nutné používat vlákno při čekání. Na konci stručně používají existující vlákno dokončení vstupně-výstupních operací.  
  
-   Latence operace přístupu k souboru může být velmi nízkou pod aktuální podmínky, ale latence může výrazně zlepšit v budoucnu. Soubor může například přesunout na server, který je po celém světě.  
  
-   Přidaný režijní náklady na použití asynchronní funkce je malý.  
  
-   Asynchronní úlohy můžete snadno spouštět paralelně.  
  
## <a name="running-the-examples"></a>Spuštění příkladů  
 Pro spuštění příkladů v tomto tématu, můžete vytvořit **aplikace WPF** nebo **formulářová aplikace Windows** a pak přidejte **tlačítko**. Na tlačítku `Click` události, přidejte volání metody první v obou příkladech.  
  
 V následujících příkladech, patří `using` příkazy.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>Použijte datový proud souboru třídy  
 V příkladech v tomto tématu <xref:System.IO.FileStream> třídu, která má možnost, která způsobí, že asynchronní vstupně-výstupních operací na úrovni operačního systému. Pomocí této možnosti byste se vyhnout blokování vlákna fondu vláken v mnoha případech. Chcete-li povolit tuto možnost, zadejte `useAsync=true` nebo `options=FileOptions.Asynchronous` argument ve volání konstruktoru.  
  
 Tuto možnost s nelze použít <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter> Pokud otevřít přímo zadáním cesty k souboru. Ale můžete použít tuto možnost, pokud jim poskytujete <xref:System.IO.Stream> , který <xref:System.IO.FileStream> třídy otevřít. Všimněte si, že byla zahájena asynchronní volání jsou rychlejší v uživatelském rozhraní aplikace i v případě, že vláken fondu vláken se zablokuje, protože vlákno uživatelského rozhraní není blokována během čekání.  
  
## <a name="writing-text"></a>Zápis textu  
 Následující příklad zapíše text do souboru. V každé await příkaz, metoda se okamžitě ukončí. Po dokončení vstupně-výstupní operace souboru se bude pokračovat na příkazu následujícímu příkazu await metodu. Všimněte si, že modifikátor async je v definici metody, které pomocí příkazu await.  
  
```csharp  
public async void ProcessWrite()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 Původní příklad obsahuje příkaz `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, což je snížení následující dva příkazy:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 První příkaz vrátí úkol a způsobí, že při zpracování souboru ke spuštění. Druhý příkaz s await způsobí, že metoda okamžitě ukončit a vrátit jiný úkol. Po dokončení zpracování později souborů, spuštění se vrátí k příkazu, který následuje await. Další informace najdete v tématu [tok řízení v asynchronních programech (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Čtení textu  
 Následující příklad přečte text ze souboru. Text je uložená do vyrovnávací paměti a v takovém případě se umístí do <xref:System.Text.StringBuilder>. Na rozdíl od předchozího příkladu, vytvoří hodnocení await hodnotu. <xref:System.IO.Stream.ReadAsync%2A> Metoda vrátí hodnotu <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, takže vytváří hodnocení await `Int32` hodnotu (`numRead`) po dokončení operace. Další informace najdete v tématu [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
```csharp  
public async void ProcessRead()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a>Paralelní asynchronní vstupně-výstupních operací  
 Následující příklad ukazuje paralelní zpracování napsáním 10 textové soubory. Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> metoda vrátí úlohu, která se pak přidá do seznamu úkolů. `await Task.WhenAll(tasks);` Příkaz ukončí metodu a obnoví v rámci metody při zpracování souboru Dokončit pro všechny úlohy.  
  
 V příkladu zavře všechna <xref:System.IO.FileStream> instance `finally` blokovat po dokončení úlohy. Pokud každý `FileStream` místo toho byl vytvořen v `using` příkazu `FileStream` může zrušit, před dokončením úkolu.  
  
 Všimněte si, že všechny zvýšení výkonu je téměř zcela v paralelní zpracování a není asynchronní zpracování. Výhody asynchronie je, že nebude vytížit více vláken a že není vytížit vlákně uživatelského rozhraní.  
  
```csharp  
public async void ProcessWriteMult()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 Při použití <xref:System.IO.Stream.WriteAsync%2A> a <xref:System.IO.Stream.ReadAsync%2A> metody, můžete zadat <xref:System.Threading.CancellationToken>, který můžete použít pro zrušení operace uprostřed datového proudu. Další informace najdete v tématu [Fine-Tuning asynchronní aplikace (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Viz také

- [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
- [Asynchronní návratové typy (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
- [Tok řízení v asynchronních programech (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
