---
title: "streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StreamWriter class, data buffering problems
- managed debugging assistants (MDAs), StreamWriter data buffering
- buffers, StreamWriter problems
- MDAs (managed debugging assistants), StreamWriter data buffering
- StreamWriter buffered data lost
- data buffering problems
- streamWriterBufferedDataLost MDA
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5a59b8735cf87e8b88036ffb317f7bbeb9f0885
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)
`streamWriterBufferedDataLost` Pomocník spravovaného ladění (MDA) se aktivuje při <xref:System.IO.StreamWriter> je zapsán do, ale <xref:System.IO.StreamWriter.Flush%2A> nebo <xref:System.IO.StreamWriter.Close%2A> metoda není volána následně před provedením instanci <xref:System.IO.StreamWriter> zničena. Pokud je povolena tato MDA, modul runtime určuje, zda veškerá data ve vyrovnávací paměti stále existuje v rámci <xref:System.IO.StreamWriter>. Pokud data ve vyrovnávací paměti neexistuje, MDA je aktivována. Volání <xref:System.GC.Collect%2A> a <xref:System.GC.WaitForPendingFinalizers%2A> metody můžete vynutit finalizační metody ke spuštění. Finalizační metody jinak poběží v zdánlivě libovolný dobu a může být vůbec na ukončení procesu. Explicitně systémem finalizační metody s Tento MDA povoleno pomůže spolehlivěji reprodukujte tento typ problému.  
  
## <a name="symptoms"></a>Příznaky  
 A <xref:System.IO.StreamWriter> poslední 1 – 4 KB dat nelze zapsat do souboru.  
  
## <a name="cause"></a>příčina  
 <xref:System.IO.StreamWriter> Uloží data interně, která vyžaduje, aby <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> metodu volat při zápisu dat z vyrovnávací paměti do příslušné úložiště dat. Pokud <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> není volána správně, data uložená do vyrovnávací paměti v <xref:System.IO.StreamWriter> instance nemusí být zapsána podle očekávání.  
  
 Následuje příklad chybně napsané kód, který by měl tento MDA catch.  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Předchozí kód se budou aktivovat tuto MDA více spolehlivě uvolnění paměti je aktivaci a potom pozastaveno, dokud finalizační metody dokončení. Chcete-li sledovat tento druh problému, můžete přidejte následující kód na konec předchozí postup v sestavení ladicí verze. To vám pomůže spolehlivě aktivovat MDA, ale samozřejmě neopraví příčinu problému.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Rozlišení  
 Zajistěte, aby zavoláte <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> před jeho zavřením aplikace nebo jakékoli blok kódu, která má instance <xref:System.IO.StreamWriter>. Jedním z nejlepší mechanismy pro dosažení tohoto cíle se vytvořit instanci pomocí C# `using` blok (`Using` v jazyce Visual Basic), který zajistí <xref:System.IO.StreamWriter.Dispose%2A> je volána metoda pro službu zápisu, což vede k instanci správně ukončování.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 Následující kód ukazuje stejné řešení pomocí `try/finally` místo `using`.  
  
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
  
 Pokud ani jedno z těchto řešení je možné (například pokud <xref:System.IO.StreamWriter> je uložen v statického proměnné a nemůže spustit snadno kód na konci celé jeho životnosti), pak volání <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> po jeho posledního použití nebo nastavení <xref:System.IO.StreamWriter.AutoFlush%2A> Vlastnost `true` před jeho první použití byste neměli tento problém.  
  
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
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu runtime.  
  
## <a name="output"></a>Výstup  
 Zprávu s upozorněním, že došlo k této porušení.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.StreamWriter>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
