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
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="cdbd5-103">streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="cdbd5-103">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="cdbd5-104">`streamWriterBufferedDataLost`Pomocník spravovaného ladění (MDA) je aktivován při <xref:System.IO.StreamWriter> zápisu do, ale <xref:System.IO.StreamWriter.Flush%2A> Metoda nebo není <xref:System.IO.StreamWriter.Close%2A> následně volána před <xref:System.IO.StreamWriter> zničením instance.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-104">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="cdbd5-105">Když je tento MDA povolený, modul runtime určí, jestli všechna data ve vyrovnávací paměti stále existují v rámci <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="cdbd5-105">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="cdbd5-106">Pokud data v bufferu existují, je aktivována aplikace MDA.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-106">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="cdbd5-107">Volání <xref:System.GC.Collect%2A> metod a <xref:System.GC.WaitForPendingFinalizers%2A> může vynutit spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-107">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="cdbd5-108">Finalizační metody se jinak spustí v zdánlivě libovolných časech a pravděpodobně ne vůbec při ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-108">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="cdbd5-109">Explicitní spuštění finalizační metody s tímto povoleným MDA vám pomůže spolehlivě reprodukování tohoto typu problému.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-109">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="cdbd5-110">Příznaky</span><span class="sxs-lookup"><span data-stu-id="cdbd5-110">Symptoms</span></span>  
 <span data-ttu-id="cdbd5-111">A <xref:System.IO.StreamWriter> nezapisuje poslední 1 – 4 KB dat do souboru.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-111">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="cdbd5-112">Příčina</span><span class="sxs-lookup"><span data-stu-id="cdbd5-112">Cause</span></span>  
 <span data-ttu-id="cdbd5-113"><xref:System.IO.StreamWriter>Ukládá data do vyrovnávací paměti interně, což vyžaduje, aby <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> Metoda nebo byla volána pro zápis dat do vyrovnávací paměti do základního úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-113">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="cdbd5-114">Pokud <xref:System.IO.StreamWriter.Close%2A> nebo není <xref:System.IO.StreamWriter.Flush%2A> správně volána, data uložená do vyrovnávací paměti v <xref:System.IO.StreamWriter> instanci nemusí být zapsána podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-114">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="cdbd5-115">Následuje příklad špatně napsaného kódu, který by měl tento MDA zachytit.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-115">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="cdbd5-116">Předchozí kód aktivuje tuto kolekci MDA spolehlivější, pokud je aktivováno uvolňování paměti a pak je pozastaveno, dokud nedokončí finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-116">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="cdbd5-117">Chcete-li sledovat tento typ problému, můžete přidat následující kód na konec předchozí metody v sestavení pro ladění.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-117">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="cdbd5-118">To vám pomůže s spolehlivou aktivací aplikace MDA, ale samozřejmě neopraví příčinu problému.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-118">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="cdbd5-119">Řešení</span><span class="sxs-lookup"><span data-stu-id="cdbd5-119">Resolution</span></span>  
 <span data-ttu-id="cdbd5-120"><xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> Před zavřením aplikace nebo jakéhokoli bloku kódu, který má instanci, se ujistěte, že jste volali nebo na <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="cdbd5-120">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="cdbd5-121">Jedním z nejlepších mechanismů pro dosažení tohoto je vytvoření instance pomocí bloku jazyka C# `using` ( `Using` v Visual Basic), který zajistí <xref:System.IO.StreamWriter.Dispose%2A> vyvolání metody zapisovače, což vede k tomu, že dojde k řádnému uzavření instance.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-121">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="cdbd5-122">Následující kód ukazuje stejné řešení pomocí `try/finally` místo `using` .</span><span class="sxs-lookup"><span data-stu-id="cdbd5-122">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="cdbd5-123">Pokud není možné použít žádná z těchto řešení (například pokud <xref:System.IO.StreamWriter> je uložena ve statické proměnné a nemůžete snadno spustit kód na konci své životnosti), pak volání <xref:System.IO.StreamWriter.Flush%2A> na základě <xref:System.IO.StreamWriter> posledního použití nebo nastavení <xref:System.IO.StreamWriter.AutoFlush%2A> vlastnosti na hodnotu `true` před prvním použitím by se mělo vyhnout tomuto problému.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-123">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="cdbd5-124">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="cdbd5-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="cdbd5-125">Tento MDA nemá žádný vliv na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-125">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="cdbd5-126">Výstup</span><span class="sxs-lookup"><span data-stu-id="cdbd5-126">Output</span></span>  
 <span data-ttu-id="cdbd5-127">Zpráva oznamující, že došlo k tomuto porušení.</span><span class="sxs-lookup"><span data-stu-id="cdbd5-127">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="cdbd5-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="cdbd5-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdbd5-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdbd5-129">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="cdbd5-130">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="cdbd5-130">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
