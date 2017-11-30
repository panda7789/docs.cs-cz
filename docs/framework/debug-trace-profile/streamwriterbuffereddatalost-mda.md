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
ms.openlocfilehash: fa6b64d37052c40dbef83a25b622e415f6946c1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="ebe26-102">streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="ebe26-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="ebe26-103">`streamWriterBufferedDataLost` Pomocník spravovaného ladění (MDA) se aktivuje při <xref:System.IO.StreamWriter> je zapsán do, ale <xref:System.IO.StreamWriter.Flush%2A> nebo <xref:System.IO.StreamWriter.Close%2A> metoda není volána následně před provedením instanci <xref:System.IO.StreamWriter> zničena.</span><span class="sxs-lookup"><span data-stu-id="ebe26-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="ebe26-104">Pokud je povolena tato MDA, modul runtime určuje, zda veškerá data ve vyrovnávací paměti stále existuje v rámci <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="ebe26-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="ebe26-105">Pokud data ve vyrovnávací paměti neexistuje, MDA je aktivována.</span><span class="sxs-lookup"><span data-stu-id="ebe26-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="ebe26-106">Volání <xref:System.GC.Collect%2A> a <xref:System.GC.WaitForPendingFinalizers%2A> metody můžete vynutit finalizační metody ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="ebe26-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="ebe26-107">Finalizační metody jinak poběží v zdánlivě libovolný dobu a může být vůbec na ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="ebe26-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="ebe26-108">Explicitně systémem finalizační metody s Tento MDA povoleno pomůže spolehlivěji reprodukujte tento typ problému.</span><span class="sxs-lookup"><span data-stu-id="ebe26-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ebe26-109">Příznaky</span><span class="sxs-lookup"><span data-stu-id="ebe26-109">Symptoms</span></span>  
 <span data-ttu-id="ebe26-110">A <xref:System.IO.StreamWriter> poslední 1 – 4 KB dat nelze zapsat do souboru.</span><span class="sxs-lookup"><span data-stu-id="ebe26-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ebe26-111">příčina</span><span class="sxs-lookup"><span data-stu-id="ebe26-111">Cause</span></span>  
 <span data-ttu-id="ebe26-112"><xref:System.IO.StreamWriter> Uloží data interně, která vyžaduje, aby <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> metodu volat při zápisu dat z vyrovnávací paměti do příslušné úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="ebe26-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="ebe26-113">Pokud <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> není volána správně, data uložená do vyrovnávací paměti v <xref:System.IO.StreamWriter> instance nemusí být zapsána podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="ebe26-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="ebe26-114">Následuje příklad chybně napsané kód, který by měl tento MDA catch.</span><span class="sxs-lookup"><span data-stu-id="ebe26-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="ebe26-115">Předchozí kód se budou aktivovat tuto MDA více spolehlivě uvolnění paměti je aktivaci a potom pozastaveno, dokud finalizační metody dokončení.</span><span class="sxs-lookup"><span data-stu-id="ebe26-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="ebe26-116">Chcete-li sledovat tento druh problému, můžete přidejte následující kód na konec předchozí postup v sestavení ladicí verze.</span><span class="sxs-lookup"><span data-stu-id="ebe26-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="ebe26-117">To vám pomůže spolehlivě aktivovat MDA, ale samozřejmě neopraví příčinu problému.</span><span class="sxs-lookup"><span data-stu-id="ebe26-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="ebe26-118">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="ebe26-118">Resolution</span></span>  
 <span data-ttu-id="ebe26-119">Zajistěte, aby zavoláte <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> před jeho zavřením aplikace nebo jakékoli blok kódu, která má instance <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="ebe26-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="ebe26-120">Jedním z nejlepší mechanismy pro dosažení tohoto cíle se vytvořit instanci pomocí C# `using` blok (`Using` v jazyce Visual Basic), který zajistí <xref:System.IO.StreamWriter.Dispose%2A> je volána metoda pro službu zápisu, což vede k instanci správně ukončování.</span><span class="sxs-lookup"><span data-stu-id="ebe26-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="ebe26-121">Následující kód ukazuje stejné řešení pomocí `try/finally` místo `using`.</span><span class="sxs-lookup"><span data-stu-id="ebe26-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="ebe26-122">Pokud ani jedno z těchto řešení je možné (například pokud <xref:System.IO.StreamWriter> je uložen v statického proměnné a nemůže spustit snadno kód na konci celé jeho životnosti), pak volání <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> po jeho posledního použití nebo nastavení <xref:System.IO.StreamWriter.AutoFlush%2A> Vlastnost `true` před jeho první použití byste neměli tento problém.</span><span class="sxs-lookup"><span data-stu-id="ebe26-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ebe26-123">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="ebe26-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="ebe26-124">Tato MDA nemá žádný vliv na modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ebe26-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ebe26-125">Výstup</span><span class="sxs-lookup"><span data-stu-id="ebe26-125">Output</span></span>  
 <span data-ttu-id="ebe26-126">Zprávu s upozorněním, že došlo k této porušení.</span><span class="sxs-lookup"><span data-stu-id="ebe26-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ebe26-127">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ebe26-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebe26-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebe26-128">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="ebe26-129">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="ebe26-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
