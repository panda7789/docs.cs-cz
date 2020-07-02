---
title: streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)
description: Projděte si pomocníka spravovaného ladění streamWriterBufferedDataLost (MDA), který se může aktivovat, pokud StreamWriter nepíše poslední 1 – 4 KB dat do souboru.
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
ms.openlocfilehash: 0c10ea6bb9dc0aaafa2ac1798696579af7592895
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803479"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)
`streamWriterBufferedDataLost`Pomocník spravovaného ladění (MDA) je aktivován při <xref:System.IO.StreamWriter> zápisu do, ale <xref:System.IO.StreamWriter.Flush%2A> Metoda nebo není <xref:System.IO.StreamWriter.Close%2A> následně volána před <xref:System.IO.StreamWriter> zničením instance. Když je tento MDA povolený, modul runtime určí, jestli všechna data ve vyrovnávací paměti stále existují v rámci <xref:System.IO.StreamWriter> . Pokud data v bufferu existují, je aktivována aplikace MDA. Volání <xref:System.GC.Collect%2A> metod a <xref:System.GC.WaitForPendingFinalizers%2A> může vynutit spuštění finalizační metody. Finalizační metody se jinak spustí v zdánlivě libovolných časech a pravděpodobně ne vůbec při ukončení procesu. Explicitní spuštění finalizační metody s tímto povoleným MDA vám pomůže spolehlivě reprodukování tohoto typu problému.  
  
## <a name="symptoms"></a>Příznaky  
 A <xref:System.IO.StreamWriter> nezapisuje poslední 1 – 4 KB dat do souboru.  
  
## <a name="cause"></a>Příčina  
 <xref:System.IO.StreamWriter>Ukládá data do vyrovnávací paměti interně, což vyžaduje, aby <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> Metoda nebo byla volána pro zápis dat do vyrovnávací paměti do základního úložiště dat. Pokud <xref:System.IO.StreamWriter.Close%2A> nebo není <xref:System.IO.StreamWriter.Flush%2A> správně volána, data uložená do vyrovnávací paměti v <xref:System.IO.StreamWriter> instanci nemusí být zapsána podle očekávání.  
  
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
 <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> Před zavřením aplikace nebo jakéhokoli bloku kódu, který má instanci, se ujistěte, že jste volali nebo na <xref:System.IO.StreamWriter> . Jedním z nejlepších mechanismů pro dosažení tohoto je vytvoření instance pomocí bloku jazyka C# `using` ( `Using` v Visual Basic), který zajistí <xref:System.IO.StreamWriter.Dispose%2A> vyvolání metody zapisovače, což vede k tomu, že dojde k řádnému uzavření instance.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 Následující kód ukazuje stejné řešení pomocí `try/finally` místo `using` .  
  
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
  
 Pokud není možné použít žádná z těchto řešení (například pokud <xref:System.IO.StreamWriter> je uložena ve statické proměnné a nemůžete snadno spustit kód na konci své životnosti), pak volání <xref:System.IO.StreamWriter.Flush%2A> na základě <xref:System.IO.StreamWriter> posledního použití nebo nastavení <xref:System.IO.StreamWriter.AutoFlush%2A> vlastnosti na hodnotu `true` před prvním použitím by se mělo vyhnout tomuto problému.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamWriter>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
