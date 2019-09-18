---
title: streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- StreamWriter class, data buffering problems
- managed debugging assistants (MDAs), StreamWriter data buffering
- buffers, StreamWriter problems
- MDAs (managed debugging assistants), StreamWriter data buffering
- StreamWriter buffered data lost
- data buffering problems
- streamWriterBufferedDataLost MDA
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3dcdd329318d48efa203d2b9dcbfe3501d94b3e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052272"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)
<xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> Pomocník spravovaného ladění (MDA) je aktivován při zápisu do, ale metoda nebo není následně volána před zničením instance. `streamWriterBufferedDataLost` Když je tento MDA povolený, modul runtime určí, jestli všechna data ve vyrovnávací paměti stále <xref:System.IO.StreamWriter>existují v rámci. Pokud data v bufferu existují, je aktivována aplikace MDA. Volání metod <xref:System.GC.WaitForPendingFinalizers%2A> a může vynutit spuštění finalizační metody. <xref:System.GC.Collect%2A> Finalizační metody se jinak spustí v zdánlivě libovolných časech a pravděpodobně ne vůbec při ukončení procesu. Explicitní spuštění finalizační metody s tímto povoleným MDA vám pomůže spolehlivě reprodukování tohoto typu problému.  
  
## <a name="symptoms"></a>Příznaky  
 A <xref:System.IO.StreamWriter> nezapisuje poslední 1 – 4 KB dat do souboru.  
  
## <a name="cause"></a>příčina  
 Ukládá data do vyrovnávací paměti interně, což vyžaduje <xref:System.IO.StreamWriter.Close%2A> , <xref:System.IO.StreamWriter.Flush%2A> aby metoda nebo byla volána pro zápis dat do vyrovnávací paměti do základního úložiště dat. <xref:System.IO.StreamWriter> Pokud <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter> nebo <xref:System.IO.StreamWriter.Flush%2A> není správně volána, data uložená do vyrovnávací paměti v instanci nemusí být zapsána podle očekávání.  
  
 Následuje příklad špatně napsaného kódu, který by měl tento MDA zachytit.  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Předchozí kód aktivuje tuto kolekci MDA spolehlivější, pokud je aktivováno uvolňování paměti a pak je pozastaveno, dokud nedokončí finalizační metody. Chcete-li sledovat tento typ problému, můžete přidat následující kód na konec předchozí metody v sestavení pro ladění. To vám pomůže s spolehlivou aktivací aplikace MDA, ale samozřejmě neopraví příčinu problému.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Řešení  
 Před zavřením aplikace <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> jakéhokoli bloku <xref:System.IO.StreamWriter>kódu, který má instanci, se ujistěte, že jste volali nebo na. <xref:System.IO.StreamWriter> Jedním z nejlepších mechanismů pro dosažení tohoto C# `using` je vytvoření instance s blokem (`Using` v <xref:System.IO.StreamWriter.Dispose%2A> Visual Basic), který zajistí vyvolání metody pro zápis, což vede k tomu, že je instance správně uzavřená.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 Následující kód ukazuje stejné řešení pomocí `try/finally` `using`místo.  
  
```csharp
StreamWriter sw;  
try   
{  
    sw = new StreamWriter("file.txt"));  
    sw.WriteLine("Data");  
}  
finally   
{  
    if (sw != null)  
        sw.Close();  
}  
```  
  
 Pokud ani jedno z těchto řešení nelze použít ( <xref:System.IO.StreamWriter> například v případě, že je uložen ve statické proměnné a nelze snadno spustit kód na konci své životnosti), pak zavolejte <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> po posledním použití nebo nastavením <xref:System.IO.StreamWriter.AutoFlush%2A> k `true` tomuto problému by se měla vyhnout vlastnost před prvním použitím.  
  
```csharp
private static StreamWriter log;  
// static class constructor.  
static WriteToFile()   
{  
    StreamWriter sw = new StreamWriter("log.txt");  
    sw.AutoFlush = true;  
  
    // Publish the StreamWriter for other threads.  
    log = sw;  
}  
```  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na modul runtime.  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující, že došlo k tomuto porušení.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamWriter>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
