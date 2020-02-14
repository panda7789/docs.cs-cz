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
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="ffc4a-102">streamWriterBufferedDataLost – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="ffc4a-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="ffc4a-103">V případě, že je zapsána <xref:System.IO.StreamWriter> do, je aktivována aplikace `streamWriterBufferedDataLost` Pomocník pro ladění spravovaného ladění (MDA), ale <xref:System.IO.StreamWriter.Flush%2A> nebo <xref:System.IO.StreamWriter.Close%2A> metoda není následně volána před zničením instance <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="ffc4a-104">Když je tento MDA povolený, modul runtime určí, jestli všechna data ve vyrovnávací paměti stále existují v rámci <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="ffc4a-105">Pokud data v bufferu existují, je aktivována aplikace MDA.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="ffc4a-106">Volání metod <xref:System.GC.Collect%2A> a <xref:System.GC.WaitForPendingFinalizers%2A> může vynutit spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="ffc4a-107">Finalizační metody se jinak spustí v zdánlivě libovolných časech a pravděpodobně ne vůbec při ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="ffc4a-108">Explicitní spuštění finalizační metody s tímto povoleným MDA vám pomůže spolehlivě reprodukování tohoto typu problému.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ffc4a-109">Příznaky</span><span class="sxs-lookup"><span data-stu-id="ffc4a-109">Symptoms</span></span>  
 <span data-ttu-id="ffc4a-110"><xref:System.IO.StreamWriter> nezapisuje poslední 1 – 4 KB dat do souboru.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ffc4a-111">Příčina</span><span class="sxs-lookup"><span data-stu-id="ffc4a-111">Cause</span></span>  
 <span data-ttu-id="ffc4a-112"><xref:System.IO.StreamWriter> ukládá data interně, což vyžaduje, aby byla volána metoda <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> pro zápis dat do vyrovnávací paměti do podkladového úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="ffc4a-113">Pokud <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> není správně volána, data uložená v instanci <xref:System.IO.StreamWriter> se nemusí zapsat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="ffc4a-114">Následuje příklad špatně napsaného kódu, který by měl tento MDA zachytit.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="ffc4a-115">Předchozí kód aktivuje tuto kolekci MDA spolehlivější, pokud je aktivováno uvolňování paměti a pak je pozastaveno, dokud nedokončí finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="ffc4a-116">Chcete-li sledovat tento typ problému, můžete přidat následující kód na konec předchozí metody v sestavení pro ladění.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="ffc4a-117">To vám pomůže s spolehlivou aktivací aplikace MDA, ale samozřejmě neopraví příčinu problému.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="ffc4a-118">Řešení</span><span class="sxs-lookup"><span data-stu-id="ffc4a-118">Resolution</span></span>  
 <span data-ttu-id="ffc4a-119">Před zavřením aplikace nebo jakéhokoli bloku kódu, který má instanci <xref:System.IO.StreamWriter>, se ujistěte, že jste volali <xref:System.IO.StreamWriter.Close%2A> nebo <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="ffc4a-120">Jedním z nejlepších mechanismů pro dosažení tohoto je vytvoření instance s blokem C# `using` (`Using` v Visual Basic), který zajistí vyvolání metody <xref:System.IO.StreamWriter.Dispose%2A> pro zapisovač, což vede k tomu, že je instance správně uzavřená.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="ffc4a-121">Následující kód ukazuje stejné řešení pomocí `try/finally` místo `using`.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="ffc4a-122">Pokud není možné použít žádná z těchto řešení (například pokud je <xref:System.IO.StreamWriter> uložen ve statické proměnné a nemůžete snadno spustit kód na konci své životnosti), pak volání <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> po posledním použití nebo nastavení vlastnosti <xref:System.IO.StreamWriter.AutoFlush%2A> na `true` před prvním použitím by se mělo vyhnout tomuto problému.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ffc4a-123">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="ffc4a-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="ffc4a-124">Tento MDA nemá žádný vliv na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ffc4a-125">Výstup</span><span class="sxs-lookup"><span data-stu-id="ffc4a-125">Output</span></span>  
 <span data-ttu-id="ffc4a-126">Zpráva oznamující, že došlo k tomuto porušení.</span><span class="sxs-lookup"><span data-stu-id="ffc4a-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ffc4a-127">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ffc4a-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffc4a-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffc4a-128">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="ffc4a-129">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="ffc4a-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
