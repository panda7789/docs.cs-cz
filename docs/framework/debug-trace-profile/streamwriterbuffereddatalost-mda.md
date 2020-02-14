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
ms.openlocfilehash: 82940b40b302f4a928547f2e6a0c285727e13934
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216101"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)
V případě, že je zapsána <xref:System.IO.StreamWriter> do, je aktivována aplikace `streamWriterBufferedDataLost` Pomocník pro ladění spravovaného ladění (MDA), ale <xref:System.IO.StreamWriter.Flush%2A> nebo <xref:System.IO.StreamWriter.Close%2A> metoda není následně volána před zničením instance <xref:System.IO.StreamWriter>. Když je tento MDA povolený, modul runtime určí, jestli všechna data ve vyrovnávací paměti stále existují v rámci <xref:System.IO.StreamWriter>. Pokud data v bufferu existují, je aktivována aplikace MDA. Volání metod <xref:System.GC.Collect%2A> a <xref:System.GC.WaitForPendingFinalizers%2A> může vynutit spuštění finalizační metody. Finalizační metody se jinak spustí v zdánlivě libovolných časech a pravděpodobně ne vůbec při ukončení procesu. Explicitní spuštění finalizační metody s tímto povoleným MDA vám pomůže spolehlivě reprodukování tohoto typu problému.  
  
## <a name="symptoms"></a>Příznaky  
 <xref:System.IO.StreamWriter> nezapisuje poslední 1 – 4 KB dat do souboru.  
  
## <a name="cause"></a>Příčina  
 <xref:System.IO.StreamWriter> ukládá data interně, což vyžaduje, aby byla volána metoda <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> pro zápis dat do vyrovnávací paměti do podkladového úložiště dat. Pokud <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> není správně volána, data uložená v instanci <xref:System.IO.StreamWriter> se nemusí zapsat podle očekávání.  
  
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
 Před zavřením aplikace nebo jakéhokoli bloku kódu, který má instanci <xref:System.IO.StreamWriter>, se ujistěte, že jste volali <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter>. Jedním z nejlepších mechanismů pro dosažení tohoto je vytvoření instance s blokem C# `using` (`Using` v Visual Basic), který zajistí vyvolání metody <xref:System.IO.StreamWriter.Dispose%2A> pro zapisovač, což vede k tomu, že je instance správně uzavřená.  
  
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
  
 Pokud není možné použít žádná z těchto řešení (například pokud je <xref:System.IO.StreamWriter> uložen ve statické proměnné a nemůžete snadno spustit kód na konci své životnosti), pak volání <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> po posledním použití nebo nastavení vlastnosti <xref:System.IO.StreamWriter.AutoFlush%2A> na `true` před prvním použitím by se mělo vyhnout tomuto problému.  
  
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
