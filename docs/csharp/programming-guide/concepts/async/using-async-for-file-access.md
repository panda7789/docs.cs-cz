---
title: "Použití modifikátoru Async pro přístup k souborům (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d6272baa9beae405148185abfebde84ca0cb7d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-async-for-file-access-c"></a>Použití modifikátoru Async pro přístup k souborům (C#)
Můžete použít funkci async pro přístup k souborům. Pomocí funkce asynchronní můžete volat do asynchronní metody bez použití zpětná volání nebo rozdělení kódu mezi více metod nebo výrazy lambda. Chcete-li synchronní kód asynchronní, právě volání asynchronní metody místo synchronní metody a přidejte několik klíčových slov do kódu.  
  
 Můžete zvážit z následujících důvodů pro přidání asynchrony do souboru přístup volání:  
  
-   Asynchrony zadává uživatelského rozhraní aplikace rychlejšího protože vlákna uživatelského rozhraní, která spustí operace můžete provádět jinou práci. Pokud vlákna uživatelského rozhraní musí být spuštěn kód která trvá dlouhou dobu (například více než 50 milisekund), rozhraní může zmrazit až po dokončení vstupy/výstupy a vlákna uživatelského rozhraní můžete znovu zpracovat klávesnice a myši vstupní a dalších událostí.  
  
-   Asynchrony zlepšuje škálovatelnost technologie ASP.NET a dalších serverových aplikací, protože snižuje potřebu vláken. Pokud aplikace používá vyhrazený vlákno na jeden odpovědi a tisíce požadavky jsou právě zpracovávány současně, je potřeba tisíce vláken. Asynchronní operace často není třeba použít během čekání vlákno. Na konci stručně používají existující vlákno dokončení vstupně-výstupní operace.  
  
-   Latence operace přístupu k souboru může být velmi nízkou v aktuální podmínkách, ale latence může výrazně zvýšit v budoucnu. Například může přesunout soubor na server, který je po celém světě.  
  
-   Přidaném režijní náklady na použití funkce asynchronní je malá.  
  
-   Asynchronní úlohy můžete spustit snadno paralelně.  
  
## <a name="running-the-examples"></a>Spuštění příkladů  
 Pokud chcete spustit v příkladech v tomto tématu, můžete vytvořit **aplikaci WPF** nebo **formulářové aplikace Windows** a poté přidejte **tlačítko**. U tlačítka `Click` událostí, přidejte volání do první metodu v obou příkladech.  
  
 V následujících příkladech, patří `using` příkazy.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>Použití třídy FileStream  
 V příkladech v tomto tématu <xref:System.IO.FileStream> třídy, která má možnost, která způsobí, že asynchronní vstupně-výstupních operací na úrovni operačního systému. Pomocí této možnosti se můžete vyhnout blokování podproces fondu podprocesů v mnoha případech. Chcete-li tuto možnost, zadejte `useAsync=true` nebo `options=FileOptions.Asynchronous` argument ve volání konstruktoru.  
  
 Nemůžete použít tuto možnost s <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter> Pokud otevřít přímo tak, že zadáte cestu k souboru. Ale můžete použít tuto možnost, pokud jste zadali, je <xref:System.IO.Stream> , <xref:System.IO.FileStream> třída otevřít. Upozorňujeme, že asynchronní volání jsou rychlejší v uživatelském rozhraní aplikace i v případě, že fondu vláken je blokovaný, protože vlákna uživatelského rozhraní není blokován během čekání.  
  
## <a name="writing-text"></a>Zápis textu  
 Následující příklad zapíše text do souboru. Na každé await prohlášení, metoda okamžitě ukončí. Po dokončení soubor vstupně-výstupních operací na příkaz, který následuje příkaz await obnoví metodu. Všimněte si, že se modifikátor asynchronní v definici metody, které používají příkaz await.  
  
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
  
 V původní příkladu má příkaz `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, což je zmenšení následující dva příkazy:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 První příkaz vrátí úlohu a způsobí, že při zpracování souboru spustit. Druhý příkaz se await způsobí, že metoda okamžitě ukončit a vrátit různých úloh. Po dokončení zpracování později souborů provádění vrátí příkaz, který následuje await. Další informace najdete v tématu [řízení toku v asynchronních programech (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Čtení textu  
 Následující příklad načte text ze souboru. Text je uložená do vyrovnávací paměti a v takovém případě bude umístěn do <xref:System.Text.StringBuilder>. Na rozdíl od v předchozím příkladu vytvoří vyhodnocení await hodnotu. <xref:System.IO.Stream.ReadAsync%2A> Metoda vrátí <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, takže vytváří vyhodnocení await `Int32` hodnotu (`numRead`) po dokončení operace. Další informace najdete v tématu [vrátit typy Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Paralelní asynchronní vstup-výstup  
 Následující příklad ukazuje paralelní zpracování napsáním 10 textových souborů. Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> metoda vrátí úlohu, která se pak přidá do seznamu úloh. `await Task.WhenAll(tasks);` Příkaz ukončí metodu a obnoví v rámci metody při zpracování souboru dokončete pro všechny úlohy.  
  
 Příklad zavření všech <xref:System.IO.FileStream> instancí v `finally` blokovat po dokončení úlohy. Pokud každý `FileStream` místo toho byl vytvořen v `using` příkaz, `FileStream` může probíhat za před dokončení úlohy.  
  
 Všimněte si, že žádné zvýšení výkonu je téměř úplně z paralelní zpracování a není asynchronní zpracování. Výhody asynchrony jsou ho nebude vytížit více vláken a že není vytížit vlákna uživatelského rozhraní.  
  
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
  
 Při použití <xref:System.IO.Stream.WriteAsync%2A> a <xref:System.IO.Stream.ReadAsync%2A> metod, můžete zadat <xref:System.Threading.CancellationToken>, který můžete použít se zrušit operaci střední datového proudu. Další informace najdete v tématu [Fine-Tuning vaše aplikace Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Asynchronní návratové typy (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [Řízení toku v asynchronních programech (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
