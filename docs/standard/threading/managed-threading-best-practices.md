---
title: Doporučené postupy spravovaného dělení na vlákna
ms.date: 10/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8319424c82327fd9743c573846663bdd76ed1b9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644633"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="2b420-102">Dělení na spravovaná vlákna osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="2b420-102">Managed threading best practices</span></span>
<span data-ttu-id="2b420-103">Multithreading vyžaduje pečlivé programování.</span><span class="sxs-lookup"><span data-stu-id="2b420-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="2b420-104">V případě většiny úkolů lze omezit složitost umístěním požadavků do fronty pro spuštění pomocí vláken fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="2b420-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="2b420-105">Toto téma řeší obtížnější situace, například koordinaci práce více vláken nebo zpracování vláken, která se blokují.</span><span class="sxs-lookup"><span data-stu-id="2b420-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b420-106">Od verze rozhraní .NET Framework 4, Task Parallel Library a PLINQ poskytuje rozhraní API, která snižuje do hry složitost a rizika vícevláknového programování.</span><span class="sxs-lookup"><span data-stu-id="2b420-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="2b420-107">Další informace najdete v tématu [paralelní programování v .NET](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="2b420-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="2b420-108">Zablokování a konflikty časování</span><span class="sxs-lookup"><span data-stu-id="2b420-108">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="2b420-109">Multithreading řeší problémy s propustností a rychlostí odezvy, ale zároveň přináší nové problémy: zablokování a konflikty časování.</span><span class="sxs-lookup"><span data-stu-id="2b420-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="2b420-110">Zablokování</span><span class="sxs-lookup"><span data-stu-id="2b420-110">Deadlocks</span></span>  
 <span data-ttu-id="2b420-111">K zablokování dochází tehdy, pokud se každé ze dvou vláken pokusí uzamknout prostředek, který je již zamčený.</span><span class="sxs-lookup"><span data-stu-id="2b420-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="2b420-112">Ani jedno vlákno nemůže provádět žádný další krok.</span><span class="sxs-lookup"><span data-stu-id="2b420-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="2b420-113">Mnoho metod tříd modelu spravovaných vláken poskytuje časové limity, které usnadňují zjišťování případů zablokování.</span><span class="sxs-lookup"><span data-stu-id="2b420-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="2b420-114">Například následující kód pokouší získat zámek na objekt s názvem `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="2b420-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="2b420-115">Pokud nezíská zámek do 300 milisekund, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="2b420-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="2b420-116">Konflikty časování</span><span class="sxs-lookup"><span data-stu-id="2b420-116">Race conditions</span></span>  
 <span data-ttu-id="2b420-117">Konflikt časování je chyba, ke které dojde, pokud výstup programu závisí na tom, které ze dvou nebo více vláken dříve dosáhne určitého bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="2b420-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="2b420-118">Opakované spuštění programu vrací různé výsledky a nelze předpovědět výsledek jakéhokoli daného běhu.</span><span class="sxs-lookup"><span data-stu-id="2b420-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="2b420-119">Jednoduchým příkladem konfliktu časování je zvyšování pole.</span><span class="sxs-lookup"><span data-stu-id="2b420-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="2b420-120">Předpokládejme, že třída má privátní **statické** pole (**Shared** v jazyce Visual Basic), které se navyšuje pokaždé, když je vytvořena instance třídy pomocí kódu, jako `objCt++;` (C#) nebo `objCt += 1` () Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2b420-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="2b420-121">Tato operace vyžaduje načtení hodnoty z kódu `objCt` do registru, navýšení hodnoty a její uložení v kódu `objCt`.</span><span class="sxs-lookup"><span data-stu-id="2b420-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="2b420-122">Ve vícevláknových aplikacích platí, že vlákno, které načetlo a zvýšilo hodnotu, může být přerušeno jiným vláknem, jež provede všechny tři kroky. Pokud první vlákno pokračuje v provádění a uloží svou hodnotu, přepíše kód `objCt`, aniž by zohlednilo, že hodnota se mezitím změnila.</span><span class="sxs-lookup"><span data-stu-id="2b420-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="2b420-123">Těmto konkrétním konfliktům časování se dá snadno vyhnout použitím metod třídy <xref:System.Threading.Interlocked>, jako například <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2b420-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2b420-124">Další informace o jiných technikách pro synchronizaci dat mezi více vláken, naleznete v tématu [synchronizace dat pro Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="2b420-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="2b420-125">Ke konfliktům časování může docházet také tehdy, pokud synchronizujete aktivity více vláken.</span><span class="sxs-lookup"><span data-stu-id="2b420-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="2b420-126">Při každém zápisu řádku kódu je nutné zvážit, co může nastat, pokud by vlákno bylo před provedením daného řádku (nebo před provedením jakéhokoliv jednotlivého pokynu počítače, který řádek tvoří) přerušeno a jiné vlákno by jej nahradilo.</span><span class="sxs-lookup"><span data-stu-id="2b420-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="2b420-127">Statické členy a statické konstruktory</span><span class="sxs-lookup"><span data-stu-id="2b420-127">Static members and static constructors</span></span>  
 <span data-ttu-id="2b420-128">Třída není inicializována až do té doby, dokud příslušný konstruktor třídy (konstruktor `static` v jazyce C#, konstruktor `Shared Sub New` v jazyce Visual Basic) nedokončí provádění.</span><span class="sxs-lookup"><span data-stu-id="2b420-128">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="2b420-129">Aby nedošlo ke spuštění kódu pro typ, který není inicializován, blokuje modul CLR všechna volání členů `static` dané třídy (`Shared` v jazyce Visual Basic) z jiných vláken až do dokončení konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="2b420-129">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="2b420-130">Pokud například konstruktor třídy začíná nové vlákno a procedura vlákna volá člen `static` dané třídy, je nové vlákno blokováno do doby, než je konstruktor třídy dokončen.</span><span class="sxs-lookup"><span data-stu-id="2b420-130">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="2b420-131">To platí pro jakýkoli typ, který může mít konstruktor `static`.</span><span class="sxs-lookup"><span data-stu-id="2b420-131">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="2b420-132">Počet procesorů</span><span class="sxs-lookup"><span data-stu-id="2b420-132">Number of processors</span></span>

<span data-ttu-id="2b420-133">Ať už nejsou jenom jeden procesor nebo více procesorů k dispozici v systému mohou mít vliv na architekturu s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="2b420-133">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="2b420-134">Další informace najdete v tématu [počet procesorů](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span><span class="sxs-lookup"><span data-stu-id="2b420-134">For more information, see [Number of Processors](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span></span>

<span data-ttu-id="2b420-135">Použití <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> vlastnosti k určení počtu procesorů, které jsou k dispozici za běhu.</span><span class="sxs-lookup"><span data-stu-id="2b420-135">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at runtime.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="2b420-136">Obecná doporučení</span><span class="sxs-lookup"><span data-stu-id="2b420-136">General recommendations</span></span>  
 <span data-ttu-id="2b420-137">Při používání více vláken zvažte následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="2b420-137">Consider the following guidelines when using multiple threads:</span></span>  
  
- <span data-ttu-id="2b420-138">Pro ukončení ostatních vláken nepoužívejte vlákno <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2b420-138">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="2b420-139">Volání **přerušit** na jiné vlákno se podobá vyvolání výjimky na, že vlákno, bez znalosti, jakého bodu vlákno bylo dosaženo zpracovávání dosáhlo.</span><span class="sxs-lookup"><span data-stu-id="2b420-139">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
- <span data-ttu-id="2b420-140">Pro synchronizaci činností více vláken nepoužívejte vlákna <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2b420-140">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="2b420-141">Použijte vlákna <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="2b420-141">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
- <span data-ttu-id="2b420-142">Řízení zpracovávání pracovních vláken neprovádějte z hlavního programu (například pomocí událostí).</span><span class="sxs-lookup"><span data-stu-id="2b420-142">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="2b420-143">Namísto toho je vhodné navrhnout program tak, aby pracovní vlákna byla zodpovědná za čekání, dokud není k dispozici činnost, kterou pak vykonají a oznámí ostatním částem programu, že byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="2b420-143">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="2b420-144">Pokud nejsou pracovní vlákna blokovací, zvažte používání vláken fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="2b420-144">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="2b420-145">Volání metody <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> je užitečné v situacích, kdy pracovní vlákna provádí blokování.</span><span class="sxs-lookup"><span data-stu-id="2b420-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
- <span data-ttu-id="2b420-146">Nepoužívejte typy jako objekty zámku.</span><span class="sxs-lookup"><span data-stu-id="2b420-146">Don't use types as lock objects.</span></span> <span data-ttu-id="2b420-147">To znamená, že byste neměli používat kódy, jako je `lock(typeof(X))` v jazyce C# nebo `SyncLock(GetType(X))` v jazyce Visual Basic, nebo používat kód <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> s objekty <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="2b420-147">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="2b420-148">Pro daný typ existuje pouze jedna instance <xref:System.Type?displayProperty=nameWithType> v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b420-148">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="2b420-149">V případě, že typ, pro který použijete zámek, je veřejný, může jej jiný kód uzamknout, což povede k zablokování.</span><span class="sxs-lookup"><span data-stu-id="2b420-149">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="2b420-150">Další informace najdete v části [spolehlivost – doporučené postupy](../../../docs/framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="2b420-150">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
- <span data-ttu-id="2b420-151">Při zamykání instancí, například `lock(this)` v jazyce C# nebo `SyncLock(Me)` v jazyce Visual Basic, buďte obezřetní.</span><span class="sxs-lookup"><span data-stu-id="2b420-151">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="2b420-152">Pokud jiný kód v aplikaci, který je vůči typu externí, převezme zámek objektu, může dojít k zablokování.</span><span class="sxs-lookup"><span data-stu-id="2b420-152">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
- <span data-ttu-id="2b420-153">Zajistěte, aby vlákno, které se zobrazilo v monitorovacím nástroji, jej opustilo vždy, i pokud dojde k výjimce během zobrazení vlákna v monitorovacím nástroji.</span><span class="sxs-lookup"><span data-stu-id="2b420-153">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="2b420-154">C# [Zámek](~/docs/csharp/language-reference/keywords/lock-statement.md) příkazu a Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) příkaz zajišťují toto chování automaticky, když **nakonec** blok k Ujistěte se, že <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> je volá se.</span><span class="sxs-lookup"><span data-stu-id="2b420-154">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="2b420-155">Pokud nelze zajistit, aby **ukončovací** bude volána, zvažte změnu návrhu a použít **Mutex**.</span><span class="sxs-lookup"><span data-stu-id="2b420-155">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="2b420-156">Objekt mutex je automaticky uvolněn, pokud se ukončí vlákno, které jej vlastní.</span><span class="sxs-lookup"><span data-stu-id="2b420-156">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
- <span data-ttu-id="2b420-157">Pro úkoly, jež vyžadují různé prostředky, používejte více vláken a zamezte přiřazení většího počtu vláken jedinému prostředku.</span><span class="sxs-lookup"><span data-stu-id="2b420-157">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="2b420-158">Například všechny úkoly zahrnující vstup-výstup těží z toho, že mají vlastní vlákno, protože dané vlákno bude přerušováno během vstupně-výstupních operací, a tím umožní provedení jiných vláken.</span><span class="sxs-lookup"><span data-stu-id="2b420-158">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="2b420-159">Uživatelský vstup je dalším prostředkem, který těží z vyhrazeného vlákna.</span><span class="sxs-lookup"><span data-stu-id="2b420-159">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="2b420-160">Úkol, který vyžaduje intenzivní výpočty, existuje na počítači s jedním procesorem spolu s uživatelským vstupem a s úkoly, jež se týkají vstupu-výstupu, ale úkoly s vícenásobnými intenzivními výpočty si vzájemně konkurují.</span><span class="sxs-lookup"><span data-stu-id="2b420-160">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
- <span data-ttu-id="2b420-161">Pro jednoduché změny stavu je třeba zvážit použití metod třídy <xref:System.Threading.Interlocked> namísto používání příkazu `lock` (`SyncLock` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2b420-161">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="2b420-162">Příkaz `lock` je dobrý univerzální nástroj, avšak třída <xref:System.Threading.Interlocked> poskytuje lepší výkon aktualizací, které musí být atomické.</span><span class="sxs-lookup"><span data-stu-id="2b420-162">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="2b420-163">Pokud neexistují žádné kolize, provede interně jedinou předponu zámku.</span><span class="sxs-lookup"><span data-stu-id="2b420-163">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="2b420-164">V revizích kódu hledejte stejný kód, jaký je uveden v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="2b420-164">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="2b420-165">V prvním příkladu je zvýšena stavová proměnná:</span><span class="sxs-lookup"><span data-stu-id="2b420-165">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="2b420-166">Pokud použijete metodu <xref:System.Threading.Interlocked.Increment%2A> namísto příkazu `lock`, můžete zlepšit výkon, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="2b420-166">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="2b420-167">V rozhraní .NET Framework 2.0 nebo novější, použijte <xref:System.Threading.Interlocked.Add%2A> metodu pro atomické přírůstcích větších než 1.</span><span class="sxs-lookup"><span data-stu-id="2b420-167">In the .NET Framework 2.0 and later, use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="2b420-168">Ve druhém příkladu je proměnná referenčního typu aktualizována pouze tehdy, pokud má odkaz hodnotu null (`Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2b420-168">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="2b420-169">Výkon lze zvýšit pomocí metody <xref:System.Threading.Interlocked.CompareExchange%2A>, jak je zobrazeno dále:</span><span class="sxs-lookup"><span data-stu-id="2b420-169">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="2b420-170">Od verze rozhraní .NET Framework 2.0, <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> přetížení metody poskytuje alternativu typově bezpečný pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="2b420-170">Beginning with .NET Framework 2.0, the <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="2b420-171">Doporučení pro knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="2b420-171">Recommendations for class libraries</span></span>  
 <span data-ttu-id="2b420-172">Při navrhování knihoven tříd pro multithreading zvažte následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="2b420-172">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
- <span data-ttu-id="2b420-173">Pokud je to možné, synchronizaci nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="2b420-173">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="2b420-174">To zejména platí pro velmi vytížený kód.</span><span class="sxs-lookup"><span data-stu-id="2b420-174">This is especially true for heavily used code.</span></span> <span data-ttu-id="2b420-175">Algoritmus může být například upraven pro tolerování konfliktů časování spíše než pro jejich odstranění.</span><span class="sxs-lookup"><span data-stu-id="2b420-175">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="2b420-176">Zbytečná synchronizace snižuje výkon a vytvoří možnosti pro zablokování a konflikty časování.</span><span class="sxs-lookup"><span data-stu-id="2b420-176">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
- <span data-ttu-id="2b420-177">Zajistěte, aby data deklarovaná jako static (`Shared` v jazyce Visual Basic) byla ve výchozím nastavení bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2b420-177">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
- <span data-ttu-id="2b420-178">Nenastavujte data instancí ve výchozím nastavení jako bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2b420-178">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="2b420-179">Přidávání zámků za účelem vytvoření kódu bezpečného pro přístup z více vláken snižuje výkon, zvyšuje kolize zámků a vytváří možnost zablokování.</span><span class="sxs-lookup"><span data-stu-id="2b420-179">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="2b420-180">V běžných modelech aplikací provádí uživatelský kód v každém okamžiku pouze jedno vlákno, což minimalizuje potřebu zabezpečení pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2b420-180">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="2b420-181">Z tohoto důvodu nejsou knihovny tříd rozhraní .NET Framework ve výchozím nastavení bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2b420-181">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
- <span data-ttu-id="2b420-182">Nepoužívejte poskytování statických metod, které mění stav.</span><span class="sxs-lookup"><span data-stu-id="2b420-182">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="2b420-183">V případě běžných použití serverů je statický stav sdílen napříč požadavky, což znamená, že více vláken může současně spustit tento kód.</span><span class="sxs-lookup"><span data-stu-id="2b420-183">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="2b420-184">Tato skutečnost otevírá možnosti pro chyby spojené s používáním více vláken.</span><span class="sxs-lookup"><span data-stu-id="2b420-184">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="2b420-185">Zvažte používání návrhového vzoru, který zapouzdřuje data do instancí, jež nejsou sdíleny napříč požadavky.</span><span class="sxs-lookup"><span data-stu-id="2b420-185">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="2b420-186">Dále platí, že pokud jsou synchronizována statická data, volání mezi statickými metodami, které mění stav, může způsobit zablokování nebo redundantní synchronizaci, což nepříznivě ovlivňuje výkon.</span><span class="sxs-lookup"><span data-stu-id="2b420-186">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b420-187">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b420-187">See also</span></span>

- [<span data-ttu-id="2b420-188">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="2b420-188">Threading</span></span>](../../../docs/standard/threading/index.md)
- [<span data-ttu-id="2b420-189">Vlákna a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="2b420-189">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
