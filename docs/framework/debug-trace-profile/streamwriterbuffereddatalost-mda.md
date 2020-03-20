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
ms.openlocfilehash: 18b2a5a95756ed125d26b2846c0b1ddc320463ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181743"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)
`streamWriterBufferedDataLost` Spravovaný ladicí asistent (MDA) <xref:System.IO.StreamWriter> je aktivován při <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter.Close%2A> zápisu do, ale metoda nebo <xref:System.IO.StreamWriter> není následně volána před zničením instance. Pokud je tato mda povolena, runtime určuje, zda všechna <xref:System.IO.StreamWriter>data ve vyrovnávací paměti stále existuje v rámci . Pokud data ve vyrovnávací paměti existují, je aktivovánm MDA. Volání <xref:System.GC.Collect%2A> metody <xref:System.GC.WaitForPendingFinalizers%2A> a může vynutit spuštění finalizačních metod. Finalizační metody budou jinak spuštěny ve zdánlivě libovolných časech a možná vůbec ne při ukončení procesu. Explicitně spuštěné finalizační metody s tímto povoleným mda pomůže spolehlivěji reprodukovat tento typ problému.  
  
## <a name="symptoms"></a>Příznaky  
 A <xref:System.IO.StreamWriter> nezapisuje poslední 1–4 KB dat do souboru.  
  
## <a name="cause"></a>Příčina  
 Vyrovnávací <xref:System.IO.StreamWriter> paměti data interně, což <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> vyžaduje, aby nebo metoda být volána k zápisu dat ve vyrovnávací paměti do úložiště dat podkladových. Pokud <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> nebo není správně volána, data <xref:System.IO.StreamWriter> do vyrovnávací paměti v instanci nemusí být zapsána podle očekávání.  
  
 Následuje příklad špatně napsaný kód, který by měl tento MDA zachytit.  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Předchozí kód aktivuje tento MDA spolehlivěji, pokud je aktivována uvolňování paměti a potom pozastavena, dokud finalizační metody byly dokončeny. Chcete-li sledovat tento typ problému, můžete přidat následující kód na konec předchozí metody v sestavení ladění. To pomůže spolehlivě aktivovat MDA, ale samozřejmě to neřeší příčinu problému.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Řešení  
 Ujistěte se, <xref:System.IO.StreamWriter.Flush%2A> že <xref:System.IO.StreamWriter> volání <xref:System.IO.StreamWriter.Close%2A> nebo na před zavřením aplikace <xref:System.IO.StreamWriter>nebo libovolný blok kódu, který má instanci . Jedním z nejlepších mechanismů pro dosažení tohoto je vytvoření `using` instance`Using` s c# blok <xref:System.IO.StreamWriter.Dispose%2A> ( v jazyce Visual Basic), který zajistí, že metoda pro zapisovatele je vyvolána, výsledkem instance je správně uzavřen.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 Následující kód ukazuje stejné řešení, `try/finally` `using`pomocí namísto .  
  
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
  
 Pokud nelze použít žádné z těchto řešení <xref:System.IO.StreamWriter> (například pokud a je uložen ve statické proměnné a nelze <xref:System.IO.StreamWriter.Flush%2A> snadno <xref:System.IO.StreamWriter> spustit kód na konci jeho životnosti), pak volání po jeho poslední použití nebo nastavení <xref:System.IO.StreamWriter.AutoFlush%2A> vlastnosti `true` před jeho prvním použitím by se měl vyhnout tomuto problému.  
  
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
  
## <a name="effect-on-the-runtime"></a>Vliv na běhový čas  
 Tento MDA nemá žádný vliv na za běhu.  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující, že k tomuto porušení došlo.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamWriter>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
