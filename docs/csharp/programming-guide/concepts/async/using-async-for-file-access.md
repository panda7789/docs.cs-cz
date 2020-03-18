---
title: Použití aplikace Async pro přístup k souborům (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: e6b0370049d9b9315de6a72d0e84c080aac12481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595544"
---
# <a name="using-async-for-file-access-c"></a>Použití aplikace Async pro přístup k souborům (C#)
Funkci asynchronní můžete použít pro přístup k souborům. Pomocí funkce async můžete volat do asynchronních metod bez použití zpětných volání nebo rozdělení kódu mezi více metod nebo výrazy lambda. Chcete-li synchronní kód asynchronní, stačí volat asynchronní metodu namísto synchronní metody a přidat několik klíčových slov do kódu.  
  
 Můžete zvážit následující důvody pro přidání asynchrony do volání přístupu k souborům:  
  
- Asynchrony umožňuje aplikace uživatelského rozhraní citlivější, protože vlákno uživatelského rozhraní, které spustí operaci může provádět jinou práci. Pokud vlákno uživatelského rozhraní musí spustit kód, který trvá dlouhou dobu (například více než 50 milisekund), uživatelské rozhraní může zamrznout, dokud není dokončeno vstupně-v., a vlákno uživatelského rozhraní může znovu zpracovat vstup klávesnice a myši a další události.  
  
- Asynchrony zlepšuje škálovatelnost ASP.NET a dalších serverových aplikací snížením potřeby podprocesů. Pokud aplikace používá vyhrazené vlákno na odpověď a tisíce požadavků jsou zpracovávány současně, jsou potřeba tisíce podprocesů. Asynchronní operace často není nutné použít vlákno během čekání. Na konci krátce použijí existující vlákno pro dokončení vstupně-doo.  
  
- Latence operace přístupu k souborům může být velmi nízká za aktuálních podmínek, ale latence může výrazně zvýšit v budoucnu. Soubor může být například přesunut na server, který je po celém světě.  
  
- Přidaná režie použití funkce Async je malá.  
  
- Asynchronní úlohy lze snadno spustit paralelně.  
  
## <a name="running-the-examples"></a>Spuštění příkladů  
 Chcete-li spustit příklady v tomto tématu, můžete vytvořit **aplikaci WPF** nebo **aplikaci Windows Forms** a potom přidat **tlačítko**. V `Click` události tlačítka přidejte volání k první metodě v každém příkladu.  
  
 V následujících příkladech uveďte následující `using` příkazy.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>Použití třídy FileStream  
 Příklady v tomto tématu používají třídu, <xref:System.IO.FileStream> která má možnost, která způsobí, že asynchronní vstupně-v.,O dojít na úrovni operačního systému. Pomocí této možnosti se můžete v mnoha případech vyhnout blokování vlákna ThreadPool. Chcete-li povolit tuto `useAsync=true` `options=FileOptions.Asynchronous` možnost, zadejte argument nebo ve volání konstruktoru.  
  
 Tuto možnost nelze použít <xref:System.IO.StreamReader> s <xref:System.IO.StreamWriter> a pokud je otevřete přímo zadáním cesty k souboru. Tuto možnost však můžete použít, <xref:System.IO.Stream> pokud <xref:System.IO.FileStream> jim poskytnete a že třída otevřena. Všimněte si, že asynchronní volání jsou rychlejší v aplikacích uživatelského rozhraní i v případě, že vlákno ThreadPool je blokován, protože vlákno uživatelského rozhraní není blokován během čekání.  
  
## <a name="writing-text"></a>Psaní textu  
 Následující příklad zapisuje text do souboru. Na každém příkazu await metoda okamžitě ukončí. Po dokončení vstupně-videa souboru metoda pokračuje na příkaz, který následuje await prohlášení. Všimněte si, že asynchronní modifikátor je v definici metod, které používají příkaz await.  
  
```csharp  
public async Task ProcessWriteAsync()  
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
  
 Původní příklad má `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`prohlášení , což je kontrakce následujících dvou prohlášení:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 První příkaz vrátí úlohu a způsobí spuštění zpracování souboru. Druhý příkaz s await způsobí, že metoda okamžitě ukončit a vrátit jiný úkol. Po dokončení zpracování souboru se spuštění vrátí do příkazu, který následuje za await. Další informace naleznete [v tématu Řízení toku v asynchronních programech (C#)](./control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Čtení textu  
 Následující příklad přečte text ze souboru. Text je uložen do vyrovnávací paměti a <xref:System.Text.StringBuilder>v tomto případě umístěn do . Na rozdíl od předchozího příkladu hodnocení await vytvoří hodnotu. Metoda <xref:System.IO.Stream.ReadAsync%2A> <xref:System.Threading.Tasks.Task> \< <xref:System.Int32> vrátí>, takže vyhodnocení await vytvoří `Int32` hodnotu`numRead`( ) po dokončení operace. Další informace naleznete [v tématu Asynchronní návratové typy (C#)](./async-return-types.md).  
  
```csharp  
public async Task ProcessReadAsync()  
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
  
## <a name="parallel-asynchronous-io"></a>Paralelní asynchronní vstupně-nosné  
 Následující příklad ukazuje paralelní zpracování zápisem 10 textových souborů. Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> metoda vrátí úkol, který je pak přidán do seznamu úkolů. Příkaz `await Task.WhenAll(tasks);` ukončí metodu a pokračuje v rámci metody po dokončení zpracování souboru pro všechny úkoly.  
  
 Příklad zavře všechny <xref:System.IO.FileStream> instance v `finally` bloku po dokončení úkolů. Pokud `FileStream` byl vytvořen v `using` příkazu, `FileStream` může být uvolněn před dokončením úkolu.  
  
 Všimněte si, že jakékoli zvýšení výkonu je téměř výhradně z paralelní zpracování a nikoli asynchronní zpracování. Výhody asynchrony jsou, že neváže více vláken a že neváže vlákno uživatelského rozhraní.  
  
```csharp  
public async Task ProcessWriteMultAsync()  
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
  
 Při použití <xref:System.IO.Stream.WriteAsync%2A> <xref:System.IO.Stream.ReadAsync%2A> metody a můžete <xref:System.Threading.CancellationToken>zadat , který můžete použít ke zrušení operace uprostřed datového proudu. Další informace naleznete v [tématu Jemné doladění asynchronní aplikace (C#)](./fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Viz také

- [Asynchronní programování s asynchronní a await (C#)](./index.md)
- [Asynchronní návratové typy (C#)](./async-return-types.md)
- [Tok řízení v asynchronních programech (C#)](./control-flow-in-async-programs.md)
