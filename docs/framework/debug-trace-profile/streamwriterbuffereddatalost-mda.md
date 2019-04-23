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
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="f92ec-102">streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="f92ec-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="f92ec-103">`streamWriterBufferedDataLost` Aktivovat pomocníka spravovaného ladění (MDA) při <xref:System.IO.StreamWriter> se zapisují do, ale <xref:System.IO.StreamWriter.Flush%2A> nebo <xref:System.IO.StreamWriter.Close%2A> metoda není volána následně před provedením instance <xref:System.IO.StreamWriter> zničen.</span><span class="sxs-lookup"><span data-stu-id="f92ec-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="f92ec-104">Když je povolené toto MDA, modul runtime určuje, zda všechna data ve vyrovnávací paměti stále existuje v rámci <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="f92ec-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="f92ec-105">Pokud data ve vyrovnávací paměti, MDA aktivováno.</span><span class="sxs-lookup"><span data-stu-id="f92ec-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="f92ec-106">Volání <xref:System.GC.Collect%2A> a <xref:System.GC.WaitForPendingFinalizers%2A> metod můžete vynutit finalizační metody ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="f92ec-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="f92ec-107">Finalizační metody jinak poběží v zdánlivě libovolného dobu a může být vůbec na ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="f92ec-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="f92ec-108">Explicitně s toto MDA povoleno spuštění finalizační metody pomůže spolehlivěji reprodukovat tento typ problému.</span><span class="sxs-lookup"><span data-stu-id="f92ec-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f92ec-109">Příznaky</span><span class="sxs-lookup"><span data-stu-id="f92ec-109">Symptoms</span></span>  
 <span data-ttu-id="f92ec-110">A <xref:System.IO.StreamWriter> nezapisuje poslední 1 – 4 KB dat do souboru.</span><span class="sxs-lookup"><span data-stu-id="f92ec-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f92ec-111">Příčina</span><span class="sxs-lookup"><span data-stu-id="f92ec-111">Cause</span></span>  
 <span data-ttu-id="f92ec-112"><xref:System.IO.StreamWriter> Ukládá do vyrovnávací paměti dat interně, což vyžaduje, aby <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> metodu volat zapisovat data ve vyrovnávací paměti k základnímu úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="f92ec-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="f92ec-113">Pokud <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> není volána správně, data uložená do vyrovnávací paměti v <xref:System.IO.StreamWriter> instance nemusejí být určeny podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="f92ec-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="f92ec-114">Následuje příklad špatně napsaný kód, který byste zachytit toto MDA.</span><span class="sxs-lookup"><span data-stu-id="f92ec-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="f92ec-115">Předchozí kód se budou aktivovat toto MDA více spolehlivě uvolňování paměti se aktivuje a potom pozastaveno, dokud dokončení finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="f92ec-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="f92ec-116">Sledovat tento druh problému, můžete přidat následující kód na konec předchozí metodu v sestavení pro ladění.</span><span class="sxs-lookup"><span data-stu-id="f92ec-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="f92ec-117">To vám pomůže spolehlivě aktivovat MDA, ale samozřejmě neopraví příčiny problému.</span><span class="sxs-lookup"><span data-stu-id="f92ec-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="f92ec-118">Řešení</span><span class="sxs-lookup"><span data-stu-id="f92ec-118">Resolution</span></span>  
 <span data-ttu-id="f92ec-119">Ujistěte se, že zavoláte <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> před ukončením aplikace nebo jakékoli blok kódu, který má instance <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="f92ec-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="f92ec-120">Jednu z nejlepších mechanismy pro dosažení tohoto cíle je vytvoření instance s C# `using` blok (`Using` v jazyce Visual Basic), která zajistí <xref:System.IO.StreamWriter.Dispose%2A> je vyvolána metoda pro modul pro zápis, výsledkem je instance správně zavírá.</span><span class="sxs-lookup"><span data-stu-id="f92ec-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="f92ec-121">Následující kód ukazuje stejného řešení, pomocí `try/finally` místo `using`.</span><span class="sxs-lookup"><span data-stu-id="f92ec-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="f92ec-122">Pokud ani jedno z těchto řešení je možné (například pokud <xref:System.IO.StreamWriter> je uložen v statickou proměnnou a nemůže spustit snadno kódu na konci svého životního cyklu), následným voláním <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> po nastavení nebo posledního použití <xref:System.IO.StreamWriter.AutoFlush%2A> Vlastnost `true` před jeho prvního použití byste se vyhnout tomuto problému.</span><span class="sxs-lookup"><span data-stu-id="f92ec-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f92ec-123">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="f92ec-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="f92ec-124">Toto MDA nemá žádný vliv na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="f92ec-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f92ec-125">Výstup</span><span class="sxs-lookup"><span data-stu-id="f92ec-125">Output</span></span>  
 <span data-ttu-id="f92ec-126">Zprávu s oznámením, že došlo k porušení.</span><span class="sxs-lookup"><span data-stu-id="f92ec-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f92ec-127">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f92ec-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f92ec-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f92ec-128">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="f92ec-129">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="f92ec-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
