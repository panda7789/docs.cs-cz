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
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="bc8ab-102">streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="bc8ab-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="bc8ab-103">`streamWriterBufferedDataLost` Spravovaný ladicí asistent (MDA) <xref:System.IO.StreamWriter> je aktivován při <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter.Close%2A> zápisu do, ale metoda nebo <xref:System.IO.StreamWriter> není následně volána před zničením instance.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="bc8ab-104">Pokud je tato mda povolena, runtime určuje, zda všechna <xref:System.IO.StreamWriter>data ve vyrovnávací paměti stále existuje v rámci .</span><span class="sxs-lookup"><span data-stu-id="bc8ab-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="bc8ab-105">Pokud data ve vyrovnávací paměti existují, je aktivovánm MDA.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="bc8ab-106">Volání <xref:System.GC.Collect%2A> metody <xref:System.GC.WaitForPendingFinalizers%2A> a může vynutit spuštění finalizačních metod.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="bc8ab-107">Finalizační metody budou jinak spuštěny ve zdánlivě libovolných časech a možná vůbec ne při ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="bc8ab-108">Explicitně spuštěné finalizační metody s tímto povoleným mda pomůže spolehlivěji reprodukovat tento typ problému.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bc8ab-109">Příznaky</span><span class="sxs-lookup"><span data-stu-id="bc8ab-109">Symptoms</span></span>  
 <span data-ttu-id="bc8ab-110">A <xref:System.IO.StreamWriter> nezapisuje poslední 1–4 KB dat do souboru.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bc8ab-111">Příčina</span><span class="sxs-lookup"><span data-stu-id="bc8ab-111">Cause</span></span>  
 <span data-ttu-id="bc8ab-112">Vyrovnávací <xref:System.IO.StreamWriter> paměti data interně, což <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> vyžaduje, aby nebo metoda být volána k zápisu dat ve vyrovnávací paměti do úložiště dat podkladových.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="bc8ab-113">Pokud <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> nebo není správně volána, data <xref:System.IO.StreamWriter> do vyrovnávací paměti v instanci nemusí být zapsána podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="bc8ab-114">Následuje příklad špatně napsaný kód, který by měl tento MDA zachytit.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="bc8ab-115">Předchozí kód aktivuje tento MDA spolehlivěji, pokud je aktivována uvolňování paměti a potom pozastavena, dokud finalizační metody byly dokončeny.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="bc8ab-116">Chcete-li sledovat tento typ problému, můžete přidat následující kód na konec předchozí metody v sestavení ladění.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="bc8ab-117">To pomůže spolehlivě aktivovat MDA, ale samozřejmě to neřeší příčinu problému.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="bc8ab-118">Řešení</span><span class="sxs-lookup"><span data-stu-id="bc8ab-118">Resolution</span></span>  
 <span data-ttu-id="bc8ab-119">Ujistěte se, <xref:System.IO.StreamWriter.Flush%2A> že <xref:System.IO.StreamWriter> volání <xref:System.IO.StreamWriter.Close%2A> nebo na před zavřením aplikace <xref:System.IO.StreamWriter>nebo libovolný blok kódu, který má instanci .</span><span class="sxs-lookup"><span data-stu-id="bc8ab-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="bc8ab-120">Jedním z nejlepších mechanismů pro dosažení tohoto je vytvoření `using` instance`Using` s c# blok <xref:System.IO.StreamWriter.Dispose%2A> ( v jazyce Visual Basic), který zajistí, že metoda pro zapisovatele je vyvolána, výsledkem instance je správně uzavřen.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="bc8ab-121">Následující kód ukazuje stejné řešení, `try/finally` `using`pomocí namísto .</span><span class="sxs-lookup"><span data-stu-id="bc8ab-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="bc8ab-122">Pokud nelze použít žádné z těchto řešení <xref:System.IO.StreamWriter> (například pokud a je uložen ve statické proměnné a nelze <xref:System.IO.StreamWriter.Flush%2A> snadno <xref:System.IO.StreamWriter> spustit kód na konci jeho životnosti), pak volání po jeho poslední použití nebo nastavení <xref:System.IO.StreamWriter.AutoFlush%2A> vlastnosti `true` před jeho prvním použitím by se měl vyhnout tomuto problému.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bc8ab-123">Vliv na běhový čas</span><span class="sxs-lookup"><span data-stu-id="bc8ab-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="bc8ab-124">Tento MDA nemá žádný vliv na za běhu.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bc8ab-125">Výstup</span><span class="sxs-lookup"><span data-stu-id="bc8ab-125">Output</span></span>  
 <span data-ttu-id="bc8ab-126">Zpráva oznamující, že k tomuto porušení došlo.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bc8ab-127">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="bc8ab-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc8ab-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc8ab-128">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="bc8ab-129">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="bc8ab-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
