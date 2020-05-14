---
title: Použití Async pro přístup k souborům (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 8e0a62c2263ed3fd11eb4accb54978ef439ac010
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396964"
---
# <a name="using-async-for-file-access-c"></a>Použití Async pro přístup k souborům (C#)
K přístupu k souborům můžete použít funkci Async. Pomocí asynchronní funkce můžete zavolat do asynchronních metod bez použití zpětných volání nebo rozdělení kódu napříč více metodami nebo lambda výrazy. Chcete-li synchronní asynchronní kód, stačí zavolat asynchronní metodu namísto synchronní metody a přidat k kódu několik klíčových slov.  
  
 Při přidávání asynchronii do volání přístupu k souborům můžete zvážit následující důvody:  
  
- Asynchronii umožňuje aplikacím uživatelského rozhraní lépe reagovat, protože vlákno uživatelského rozhraní, které spouští operaci, může provádět i jinou práci. Pokud vlákno uživatelského rozhraní musí spustit kód, který trvá dlouhou dobu (například více než 50 milisekund), může uživatelské rozhraní zablokovat až do dokončení vstupně-výstupních operací a vlákno uživatelského rozhraní může znovu zpracovat vstupy klávesnice a myši a další události.  
  
- Asynchronii zlepšuje škálovatelnost ASP.NET a dalších serverových aplikací tím, že snižuje nutnost vláken. Pokud aplikace používá vyhrazené vlákno na reakci a tisíce požadavků jsou zpracovávány současně, je zapotřebí tisíce vláken. Asynchronní operace často nepotřebují použít vlákno během čekání. Na konci se krátce používají existující vlákna dokončení v/v.  
  
- Latence operace přístupu k souboru může být v rámci současných podmínek velmi nízká, ale latence může výrazně zvýšit i v budoucnu. Soubor může být například přesunut na server, který je na celém světě.  
  
- Přidaná režie použití asynchronní funkce je malá.  
  
- Asynchronní úlohy lze snadno spustit paralelně.  
  
## <a name="running-the-examples"></a>Spuštění příkladů  
 Chcete-li spustit příklady v tomto tématu, můžete vytvořit **aplikaci WPF** nebo **aplikaci model Windows Forms** a pak přidat **tlačítko**. V `Click` události tlačítka přidejte do prvního příkladu volání první metody.  
  
 V následujících příkladech zahrňte následující `using` direktivy.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>Použití třídy FileStream  
 Příklady v tomto tématu používají <xref:System.IO.FileStream> třídu, která má možnost, která způsobuje asynchronní vstupně-výstupní operace na úrovni operačního systému. Pomocí této možnosti se můžete vyhnout blokování vlákna fondu vláken v mnoha případech. Chcete-li povolit tuto možnost, zadejte `useAsync=true` `options=FileOptions.Asynchronous` argument nebo ve volání konstruktoru.  
  
 Tuto možnost nemůžete použít s <xref:System.IO.StreamReader> a, <xref:System.IO.StreamWriter> Pokud je otevřete přímo zadáním cesty k souboru. Tuto možnost však můžete použít, pokud jim poskytnete <xref:System.IO.Stream> třídu, kterou <xref:System.IO.FileStream> otevřela. Všimněte si, že asynchronní volání jsou rychlejší v aplikacích uživatelského rozhraní i v případě, že je vlákno nevláken blokované, protože během čekání není zablokované vlákno uživatelského rozhraní.  
  
## <a name="writing-text"></a>Zápis textu  
 Následující příklad zapisuje text do souboru. V každém příkazu await se metoda okamžitě ukončí. Po dokončení vstupně-výstupních operací se metoda obnoví v příkazu, který následuje po příkazu await. Všimněte si, že modifikátor Async je v definici metod, které používají příkaz await.  
  
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
  
 Původní příklad obsahuje příkaz `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);` , který je kontraktem následujících dvou příkazů:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 První příkaz vrátí úlohu a způsobí, že se zpracování souboru spustí. Druhý příkaz s operátorem await způsobí, že metoda okamžitě ukončí a vrátí jiný úkol. Po dokončení zpracování souboru se spuštění vrátí do příkazu, který následuje za operátorem await. Další informace naleznete v tématu [řízení toku v asynchronních programech (C#)](./control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Čtení textu  
 Následující příklad přečte text ze souboru. Text je uložen do vyrovnávací paměti a v tomto případě je umístěn do <xref:System.Text.StringBuilder> . Na rozdíl od předchozího příkladu vyhodnocení await vytvoří hodnotu. <xref:System.IO.Stream.ReadAsync%2A>Metoda vrací <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, takže vyhodnocení metody await vytvoří `Int32` hodnotu ( `numRead` ) po dokončení operace. Další informace naleznete v tématu [Asynchronní návratové typy (C#)](./async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Paralelní asynchronní vstupně-výstupní operace  
 Následující příklad znázorňuje paralelní zpracování zápisem 10 textových souborů. Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> Metoda vrátí úkol, který je poté přidán do seznamu úkolů. `await Task.WhenAll(tasks);`Příkaz ukončí metodu a pokračuje v rámci metody, když je zpracování souborů dokončeno pro všechny úlohy.  
  
 Příklad zavře všechny <xref:System.IO.FileStream> instance v `finally` bloku po dokončení úkolů. Pokud byl každý z `FileStream` nich vytvořen v `using` příkazu, `FileStream` může být odstraněn před dokončením úkolu.  
  
 Všimněte si, že veškeré zvýšení výkonu je prakticky zcela úplné od paralelního zpracování, nikoli z asynchronního zpracování. Výhody asynchronii jsou, že neodkazují na více vláken a že nevyužívají vlákno uživatelského rozhraní.  
  
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
  
 Při použití <xref:System.IO.Stream.WriteAsync%2A> metod a <xref:System.IO.Stream.ReadAsync%2A> můžete zadat <xref:System.Threading.CancellationToken> , které můžete použít k zrušení operace střední-Stream. Další informace najdete v tématu [jemné ladění asynchronní aplikace (C#)](./fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Viz také

- [Asynchronní programování s modifikátorem Async a operátoru Await (C#)](./index.md)
- [Asynchronní návratové typy (C#)](./async-return-types.md)
- [Řízení toku v asynchronních programech (C#)](./control-flow-in-async-programs.md)
