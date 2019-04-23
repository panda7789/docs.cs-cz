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
ms.openlocfilehash: 3b35e6ab4de699126b4b3b5f74d7a9a8dacfa4a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117388"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)
`streamWriterBufferedDataLost` Aktivovat pomocníka spravovaného ladění (MDA) při <xref:System.IO.StreamWriter> se zapisují do, ale <xref:System.IO.StreamWriter.Flush%2A> nebo <xref:System.IO.StreamWriter.Close%2A> metoda není volána následně před provedením instance <xref:System.IO.StreamWriter> zničen. Když je povolené toto MDA, modul runtime určuje, zda všechna data ve vyrovnávací paměti stále existuje v rámci <xref:System.IO.StreamWriter>. Pokud data ve vyrovnávací paměti, MDA aktivováno. Volání <xref:System.GC.Collect%2A> a <xref:System.GC.WaitForPendingFinalizers%2A> metod můžete vynutit finalizační metody ke spuštění. Finalizační metody jinak poběží v zdánlivě libovolného dobu a může být vůbec na ukončení procesu. Explicitně s toto MDA povoleno spuštění finalizační metody pomůže spolehlivěji reprodukovat tento typ problému.  
  
## <a name="symptoms"></a>Příznaky  
 A <xref:System.IO.StreamWriter> nezapisuje poslední 1 – 4 KB dat do souboru.  
  
## <a name="cause"></a>Příčina  
 <xref:System.IO.StreamWriter> Ukládá do vyrovnávací paměti dat interně, což vyžaduje, aby <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> metodu volat zapisovat data ve vyrovnávací paměti k základnímu úložišti dat. Pokud <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> není volána správně, data uložená do vyrovnávací paměti v <xref:System.IO.StreamWriter> instance nemusejí být určeny podle očekávání.  
  
 Následuje příklad špatně napsaný kód, který byste zachytit toto MDA.  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Předchozí kód se budou aktivovat toto MDA více spolehlivě uvolňování paměti se aktivuje a potom pozastaveno, dokud dokončení finalizační metody. Sledovat tento druh problému, můžete přidat následující kód na konec předchozí metodu v sestavení pro ladění. To vám pomůže spolehlivě aktivovat MDA, ale samozřejmě neopraví příčiny problému.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Řešení  
 Ujistěte se, že zavoláte <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> před ukončením aplikace nebo jakékoli blok kódu, který má instance <xref:System.IO.StreamWriter>. Jednu z nejlepších mechanismy pro dosažení tohoto cíle je vytvoření instance s C# `using` blok (`Using` v jazyce Visual Basic), která zajistí <xref:System.IO.StreamWriter.Dispose%2A> je vyvolána metoda pro modul pro zápis, výsledkem je instance správně zavírá.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 Následující kód ukazuje stejného řešení, pomocí `try/finally` místo `using`.  
  
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
  
 Pokud ani jedno z těchto řešení je možné (například pokud <xref:System.IO.StreamWriter> je uložen v statickou proměnnou a nemůže spustit snadno kódu na konci svého životního cyklu), následným voláním <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> po nastavení nebo posledního použití <xref:System.IO.StreamWriter.AutoFlush%2A> Vlastnost `true` před jeho prvního použití byste se vyhnout tomuto problému.  
  
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
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na modul runtime.  
  
## <a name="output"></a>Výstup  
 Zprávu s oznámením, že došlo k porušení.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamWriter>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
