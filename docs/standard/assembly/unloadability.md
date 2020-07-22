---
title: Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core
description: Naučte se používat kolekční AssemblyLoadContext pro načítání a uvolňování spravovaných sestavení a jak ladit problémy zabraňující úspěšnému uvolnění.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 9d1f604816dcbd7a84a3692b3cfd24481532789a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865343"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="0cde9-103">Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core</span><span class="sxs-lookup"><span data-stu-id="0cde9-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="0cde9-104">Počínaje rozhraním .NET Core 3,0 je podporována možnost načíst a později uvolnit sadu sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cde9-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="0cde9-105">V .NET Framework se pro tento účel používaly vlastní domény aplikací, ale .NET Core podporuje jenom jednu výchozí doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0cde9-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="0cde9-106">.NET Core 3,0 a novější verze podporují odinstalaci prostřednictvím <xref:System.Runtime.Loader.AssemblyLoadContext> .</span><span class="sxs-lookup"><span data-stu-id="0cde9-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="0cde9-107">Můžete načíst sadu sestavení do kolekční `AssemblyLoadContext` , provést v nich metody nebo je pouze zkontrolovat pomocí reflexe a nakonec uvolnit `AssemblyLoadContext` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="0cde9-108">Tím se uvolní sestavení načtená do `AssemblyLoadContext` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-108">That unloads the assemblies loaded into the `AssemblyLoadContext`.</span></span>

<span data-ttu-id="0cde9-109">Existuje jeden zajímavosti rozdíl mezi uvolňováním pomocí `AssemblyLoadContext` a používáním doménových aplikací.</span><span class="sxs-lookup"><span data-stu-id="0cde9-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="0cde9-110">S objekty třídy AppDomains je uvolnění vynuceno.</span><span class="sxs-lookup"><span data-stu-id="0cde9-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="0cde9-111">V době nenačtení jsou všechna vlákna spuštěná v cílové doméně AppDomain přerušena. spravované objekty COM vytvořené v cílové doméně AppDomain budou zničeny a tak dále.</span><span class="sxs-lookup"><span data-stu-id="0cde9-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, and so on.</span></span> <span data-ttu-id="0cde9-112">S `AssemblyLoadContext` , uvolnění je "kooperativní".</span><span class="sxs-lookup"><span data-stu-id="0cde9-112">With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="0cde9-113">Volání <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> metody pouze inicializuje uvolnění.</span><span class="sxs-lookup"><span data-stu-id="0cde9-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="0cde9-114">Uvolnění se dokončí po:</span><span class="sxs-lookup"><span data-stu-id="0cde9-114">The unloading finishes after:</span></span>

- <span data-ttu-id="0cde9-115">Žádná vlákna neobsahují metody ze sestavení načtených do v `AssemblyLoadContext` jejich zásobníkech volání.</span><span class="sxs-lookup"><span data-stu-id="0cde9-115">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="0cde9-116">Žádný z typů ze sestavení načtených do `AssemblyLoadContext` , instancí těchto typů a samotná sestavení jsou odkazována pomocí:</span><span class="sxs-lookup"><span data-stu-id="0cde9-116">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types, and the assemblies themselves are referenced by:</span></span>
  - <span data-ttu-id="0cde9-117">Odkazy mimo `AssemblyLoadContext` , s výjimkou slabých odkazů ( <xref:System.WeakReference> nebo <xref:System.WeakReference%601> ).</span><span class="sxs-lookup"><span data-stu-id="0cde9-117">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="0cde9-118">Silné popisovače uvolňování paměti (GC) ([GCHandleType. Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) nebo [GCHandleType. připnutý](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) z uvnitř i vně `AssemblyLoadContext` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-118">Strong garbage collector (GC) handles ([GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) or [GCHandleType.Pinned](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="0cde9-119">Použití kolekční AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="0cde9-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="0cde9-120">Tato část obsahuje podrobný návod, který ukazuje jednoduchý způsob, jak načíst aplikaci .NET Core do kolekční `AssemblyLoadContext` , spustit její vstupní bod a pak ji uvolnit.</span><span class="sxs-lookup"><span data-stu-id="0cde9-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="0cde9-121">Úplnou ukázku najdete na adrese [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading) .</span><span class="sxs-lookup"><span data-stu-id="0cde9-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="0cde9-122">Vytvoření kolekční AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="0cde9-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="0cde9-123">Musíte třídu odvodit z rozhraní <xref:System.Runtime.Loader.AssemblyLoadContext> a přepsat její <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="0cde9-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and override its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0cde9-124">Tato metoda překládá odkazy na všechna sestavení, která jsou závislá na sestaveních, která jsou v takovém načtena `AssemblyLoadContext` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="0cde9-125">Následující kód je příkladem nejjednoduššího vlastního `AssemblyLoadContext` :</span><span class="sxs-lookup"><span data-stu-id="0cde9-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="0cde9-126">Jak vidíte, `Load` Metoda vrátí `null` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="0cde9-127">To znamená, že všechna sestavení závislostí jsou načtena do výchozího kontextu a nový kontext obsahuje pouze sestavení, která jsou do něj explicitně načtena.</span><span class="sxs-lookup"><span data-stu-id="0cde9-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="0cde9-128">Pokud chcete některé nebo všechny závislosti načíst do `AssemblyLoadContext` , můžete použít `AssemblyDependencyResolver` v `Load` metodě.</span><span class="sxs-lookup"><span data-stu-id="0cde9-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="0cde9-129">`AssemblyDependencyResolver`Přeloží názvy sestavení na absolutní cesty k souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cde9-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths.</span></span> <span data-ttu-id="0cde9-130">Překladač používá *.deps.js* v souborech a sestaveních v adresáři hlavního sestavení načteného do kontextu.</span><span class="sxs-lookup"><span data-stu-id="0cde9-130">The resolver uses the *.deps.json* file and assembly files in the directory of the main assembly loaded into the context.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="0cde9-131">Použít vlastní AssemblyLoadContext kolekční</span><span class="sxs-lookup"><span data-stu-id="0cde9-131">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="0cde9-132">V této části se předpokládá, že se používá zjednodušená verze `TestAssemblyLoadContext` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-132">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="0cde9-133">Můžete vytvořit instanci vlastního `AssemblyLoadContext` a načíst sestavení do tohoto sestavení následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0cde9-133">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="0cde9-134">Pro každé sestavení odkazované načteným sestavením `TestAssemblyLoadContext.Load` je metoda volána, aby bylo `TestAssemblyLoadContext` možné rozhodnout, odkud se má sestavení získat.</span><span class="sxs-lookup"><span data-stu-id="0cde9-134">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="0cde9-135">V našem případě se vrátí `null` k indikaci, že by měl být načten do výchozího kontextu z umístění, která modul runtime používá k načtení sestavení ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="0cde9-135">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="0cde9-136">Nyní, když bylo sestavení načteno, lze z něj spustit metodu.</span><span class="sxs-lookup"><span data-stu-id="0cde9-136">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="0cde9-137">Spusťte `Main` metodu:</span><span class="sxs-lookup"><span data-stu-id="0cde9-137">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="0cde9-138">Až se `Main` Metoda vrátí, můžete iniciovat uvolnění voláním `Unload` metody ve vlastním nebo odložení `AssemblyLoadContext` reference, kterou máte `AssemblyLoadContext` :</span><span class="sxs-lookup"><span data-stu-id="0cde9-138">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="0cde9-139">To je dostačující pro uvolnění testovacího sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cde9-139">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="0cde9-140">Pojďme to všechno využít k samostatné nestandardní metodě, aby se zajistilo, že se `TestAssemblyLoadContext` , `Assembly` a `MethodInfo` (a `Assembly.EntryPoint` ) nedají udržovat naživu pomocí odkazů na slot zásobníku (lokálních hodnot Real-nebo JIT).</span><span class="sxs-lookup"><span data-stu-id="0cde9-140">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="0cde9-141">To může zůstat ponecháno `TestAssemblyLoadContext` a zabránit uvolnění.</span><span class="sxs-lookup"><span data-stu-id="0cde9-141">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="0cde9-142">Také vrátí slabý odkaz na, `AssemblyLoadContext` aby jej bylo možné použít později ke zjištění dokončení uvolnění.</span><span class="sxs-lookup"><span data-stu-id="0cde9-142">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="0cde9-143">Nyní můžete tuto funkci spustit, chcete-li načíst, spustit a uvolnit sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cde9-143">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="0cde9-144">Uvolnění se ale okamžitě nedokončilo.</span><span class="sxs-lookup"><span data-stu-id="0cde9-144">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="0cde9-145">Jak už jsme uvedli, spoléhá se na systém uvolňování paměti ke shromáždění všech objektů z testovacího sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cde9-145">As previously mentioned, it relies on the garbage collector to collect all the objects from the test assembly.</span></span> <span data-ttu-id="0cde9-146">V mnoha případech není nutné čekat na dokončení uvolnění.</span><span class="sxs-lookup"><span data-stu-id="0cde9-146">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="0cde9-147">Existují však případy, kdy je užitečné zjistit, že uvolnění bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="0cde9-147">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="0cde9-148">Například může být vhodné odstranit soubor sestavení, který byl načten do vlastního `AssemblyLoadContext` z disku.</span><span class="sxs-lookup"><span data-stu-id="0cde9-148">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="0cde9-149">V takovém případě lze použít následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="0cde9-149">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="0cde9-150">Aktivuje uvolňování paměti a čeká na čekající finalizační metody ve smyčce, dokud není slabý odkaz na vlastní `AssemblyLoadContext` nastavený na hodnotu `null` , což značí, že byl cílový objekt shromážděn.</span><span class="sxs-lookup"><span data-stu-id="0cde9-150">It triggers garbage collection and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="0cde9-151">Ve většině případů je zapotřebí pouze jeden průchod smyčkou.</span><span class="sxs-lookup"><span data-stu-id="0cde9-151">In most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="0cde9-152">Nicméně pro složitější případy, kdy objekty vytvořené kódem spuštěným v nástroji `AssemblyLoadContext` mají finalizační metody, mohou být potřeba další průchody.</span><span class="sxs-lookup"><span data-stu-id="0cde9-152">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="0cde9-153">Událost uvolnění</span><span class="sxs-lookup"><span data-stu-id="0cde9-153">The Unloading event</span></span>

<span data-ttu-id="0cde9-154">V některých případech může být nutné, aby kód byl načten do vlastního `AssemblyLoadContext` pro provedení nějakého vyčištění při zahájení uvolnění.</span><span class="sxs-lookup"><span data-stu-id="0cde9-154">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="0cde9-155">Například může být nutné zastavit vlákna nebo vyčistit silné obslužné rutiny GC.</span><span class="sxs-lookup"><span data-stu-id="0cde9-155">For example, it may need to stop threads or clean up strong GC handles.</span></span> <span data-ttu-id="0cde9-156">`Unloading`V takových případech je možné událost použít.</span><span class="sxs-lookup"><span data-stu-id="0cde9-156">The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="0cde9-157">Obslužná rutina, která provede potřebné vyčištění, může být do této události zapojování.</span><span class="sxs-lookup"><span data-stu-id="0cde9-157">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="0cde9-158">Řešení potíží s nezátěží</span><span class="sxs-lookup"><span data-stu-id="0cde9-158">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="0cde9-159">Z důvodu kooperativního charakteru uvolňování je snadné zapomenout odkazy, které by mohly udržet věci ve kolekční `AssemblyLoadContext` Alive a bránit uvolnění.</span><span class="sxs-lookup"><span data-stu-id="0cde9-159">Due to the cooperative nature of the unloading, it's easy to forget about references that may be keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="0cde9-160">Tady je souhrn entit (některé z nich není zřejmé), které můžou obsahovat odkazy:</span><span class="sxs-lookup"><span data-stu-id="0cde9-160">Here is a summary of entities (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="0cde9-161">Regulární odkazy držené mimo kolekční `AssemblyLoadContext` , které jsou uložené v zásobníku zásobníku nebo v registru procesoru (místní metody, buď explicitně vytvořené kódem uživatele nebo implicitně pomocí kompilátoru JIT (just-in-time)), statické proměnné nebo silného (připnutí) popisovače GC a umožňují průjezdně ukazovat na:</span><span class="sxs-lookup"><span data-stu-id="0cde9-161">Regular references held from outside of the collectible `AssemblyLoadContext` that are stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the just-in-time (JIT) compiler), a static variable, or a strong (pinning) GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="0cde9-162">Sestavení načtené do kolekční `AssemblyLoadContext` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-162">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="0cde9-163">Typ z takového sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cde9-163">A type from such an assembly.</span></span>
  - <span data-ttu-id="0cde9-164">Instance typu z takového sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cde9-164">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="0cde9-165">Vlákna spouštějící kód ze sestavení načteného do kolekční `AssemblyLoadContext` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-165">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="0cde9-166">Instance vlastních, nekolekčních `AssemblyLoadContext` typů vytvořených v kolekční `AssemblyLoadContext` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-166">Instances of custom, non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="0cde9-167">Nedokončené <xref:System.Threading.RegisteredWaitHandle> instance s zpětnými voláními nastavenými na metody v vlastní `AssemblyLoadContext` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-167">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`.</span></span>

> [!TIP]
> <span data-ttu-id="0cde9-168">Odkazy na objekty, které jsou uloženy v paticích zásobníku nebo v registrech procesorů a které by mohly zabránit uvolnění `AssemblyLoadContext` může nastat v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="0cde9-168">Object references that are stored in stack slots or processor registers and that could prevent unloading of an `AssemblyLoadContext` can occur in the following situations:</span></span>
>
> - <span data-ttu-id="0cde9-169">Když jsou výsledky volání funkce předány přímo jiné funkci, i když není k dispozici místní proměnná vytvořená uživatelem.</span><span class="sxs-lookup"><span data-stu-id="0cde9-169">When function call results are passed directly to another function, even though there is no user-created local variable.</span></span>
> - <span data-ttu-id="0cde9-170">Když kompilátor JIT udržuje odkaz na objekt, který byl k dispozici v nějakém okamžiku v metodě.</span><span class="sxs-lookup"><span data-stu-id="0cde9-170">When the JIT compiler keeps a reference to an object that was available at some point in a method.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="0cde9-171">Problémy při uvolňování ladění</span><span class="sxs-lookup"><span data-stu-id="0cde9-171">Debug unloading issues</span></span>

<span data-ttu-id="0cde9-172">Problémy ladění s uvolněním můžou být zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="0cde9-172">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="0cde9-173">Můžete se dostat do situací, kdy si nejste jisti, co může držet `AssemblyLoadContext` aktivní, ale uvolnění se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="0cde9-173">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span> <span data-ttu-id="0cde9-174">Nejlepší zbraně, která vám to umožňuje, je WinDbg (LLDB v UNIX) s modulem plug-in SOS.</span><span class="sxs-lookup"><span data-stu-id="0cde9-174">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="0cde9-175">Potřebujete zjistit, co `LoaderAllocator` patří do konkrétního typu `AssemblyLoadContext` Alive.</span><span class="sxs-lookup"><span data-stu-id="0cde9-175">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span> <span data-ttu-id="0cde9-176">Modul plug-in SOS vám umožní podívat se na objekty haldy GC, jejich hierarchie a kořeny.</span><span class="sxs-lookup"><span data-stu-id="0cde9-176">The SOS plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>

<span data-ttu-id="0cde9-177">Chcete-li načíst modul plug-in do ladicího programu, zadejte následující příkaz v příkazovém řádku ladicího programu:</span><span class="sxs-lookup"><span data-stu-id="0cde9-177">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="0cde9-178">V programu WinDbg (při přerušení do aplikace .NET Core se to jeví jako WinDbg):</span><span class="sxs-lookup"><span data-stu-id="0cde9-178">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="0cde9-179">V LLDB:</span><span class="sxs-lookup"><span data-stu-id="0cde9-179">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="0cde9-180">Pojďme ladit ukázkový program, který obsahuje problémy s uvolněním.</span><span class="sxs-lookup"><span data-stu-id="0cde9-180">Let's debug an example program that has problems with unloading.</span></span> <span data-ttu-id="0cde9-181">Zdrojový kód je uveden níže.</span><span class="sxs-lookup"><span data-stu-id="0cde9-181">Source code is included below.</span></span> <span data-ttu-id="0cde9-182">Při spuštění v rámci programu WinDbg se program přeruší do ladicího programu hned po pokusu o kontrolu úspěšného načtení.</span><span class="sxs-lookup"><span data-stu-id="0cde9-182">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="0cde9-183">Pak můžete začít hledat v culprits.</span><span class="sxs-lookup"><span data-stu-id="0cde9-183">You can then start looking for the culprits.</span></span>

> [!TIP]
> <span data-ttu-id="0cde9-184">Pokud ladíte pomocí LLDB v systému UNIX, příkazy SOS v následujících příkladech nemají `!` před nimi žádné z nich.</span><span class="sxs-lookup"><span data-stu-id="0cde9-184">If you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="0cde9-185">Tento příkaz vypíše všechny objekty s názvem typu obsahujícím `LoaderAllocator` v haldě GC.</span><span class="sxs-lookup"><span data-stu-id="0cde9-185">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="0cde9-186">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="0cde9-186">Here is an example:</span></span>

```console
         Address               MT     Size
000002b78000ce40 00007ffadc93a288       48
000002b78000ceb0 00007ffadc93a218       24

Statistics:
              MT    Count    TotalSize Class Name
00007ffadc93a218        1           24 System.Reflection.LoaderAllocatorScout
00007ffadc93a288        1           48 System.Reflection.LoaderAllocator
Total 2 objects
```

<span data-ttu-id="0cde9-187">V níže uvedené části "Statistika:" se podívejte na `MT` ( `MethodTable` ) patřící do `System.Reflection.LoaderAllocator` , což je objekt, o kterém se zajímá.</span><span class="sxs-lookup"><span data-stu-id="0cde9-187">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="0cde9-188">Potom v seznamu na začátku Najděte položku s `MT` odpovídajícím záznamem a získejte adresu samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="0cde9-188">Then, in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="0cde9-189">V našem případě je to "000002b78000ce40".</span><span class="sxs-lookup"><span data-stu-id="0cde9-189">In our case, it is "000002b78000ce40".</span></span>

<span data-ttu-id="0cde9-190">Teď, když znáte adresu `LoaderAllocator` objektu, můžeme k vyhledání jeho kořenů GC použít jiný příkaz:</span><span class="sxs-lookup"><span data-stu-id="0cde9-190">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots:</span></span>

```console
!gcroot -all 0x000002b78000ce40
```

<span data-ttu-id="0cde9-191">Tento příkaz vypíše řetěz odkazů na objekty, které vedou k `LoaderAllocator` instanci.</span><span class="sxs-lookup"><span data-stu-id="0cde9-191">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="0cde9-192">Seznam začíná kořenovým adresářem, který je entitou, která udržuje naši službu `LoaderAllocator` Alive, a proto je jádrem problému.</span><span class="sxs-lookup"><span data-stu-id="0cde9-192">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem.</span></span> <span data-ttu-id="0cde9-193">Kořenem může být slot zásobníku, registr procesoru, popisovač GC nebo statická proměnná.</span><span class="sxs-lookup"><span data-stu-id="0cde9-193">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="0cde9-194">Tady je příklad výstupu `gcroot` příkazu:</span><span class="sxs-lookup"><span data-stu-id="0cde9-194">Here is an example of the output of the `gcroot` command:</span></span>

```console
Thread 4ac:
    000000cf9499dd20 00007ffa7d0236bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
        rbp-20: 000000cf9499dd90
            ->  000002b78000d328 System.Reflection.RuntimeMethodInfo
            ->  000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
            ->  000002b78000d1d0 System.RuntimeType
            ->  000002b78000ce40 System.Reflection.LoaderAllocator

HandleTable:
    000002b7f8a81198 (strong handle)
    -> 000002b78000d948 test.Test
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

    000002b7f8a815f8 (pinned handle)
    -> 000002b790001038 System.Object[]
    -> 000002b78000d390 example.TestInfo
    -> 000002b78000d328 System.Reflection.RuntimeMethodInfo
    -> 000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
    -> 000002b78000d1d0 System.RuntimeType
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

Found 3 roots.
```

<span data-ttu-id="0cde9-195">Dalším krokem je zjistit, kde se nachází kořenový adresář, abyste ho mohli opravit.</span><span class="sxs-lookup"><span data-stu-id="0cde9-195">The next step is to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="0cde9-196">Nejjednodušším případem je, že kořen je slot zásobníku nebo registr procesoru.</span><span class="sxs-lookup"><span data-stu-id="0cde9-196">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="0cde9-197">V takovém případě `gcroot` zobrazuje název funkce, jejíž rámec obsahuje kořen a vlákno, které tuto funkci spouští.</span><span class="sxs-lookup"><span data-stu-id="0cde9-197">In that case, the `gcroot` shows the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="0cde9-198">Těžké velká písmena jsou v případě, že kořen je statická proměnná nebo popisovač GC.</span><span class="sxs-lookup"><span data-stu-id="0cde9-198">The difficult case is when the root is a static variable or a GC handle.</span></span>

<span data-ttu-id="0cde9-199">V předchozím příkladu je první kořen místní typ `System.Reflection.RuntimeMethodInfo` uložený v rámci funkce `example.Program.Main(System.String[])` na adrese `rbp-20` ( `rbp` je registr procesoru `rbp` a-20 je hexadecimální posun od tohoto registru).</span><span class="sxs-lookup"><span data-stu-id="0cde9-199">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="0cde9-200">Druhý kořen je normální (silný) `GCHandle` , který obsahuje odkaz na instanci `test.Test` třídy.</span><span class="sxs-lookup"><span data-stu-id="0cde9-200">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span>

<span data-ttu-id="0cde9-201">Třetí kořen je připnutý `GCHandle` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-201">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="0cde9-202">Toto je vlastně statická proměnná, ale bohužel neexistuje žádný způsob, jak říct.</span><span class="sxs-lookup"><span data-stu-id="0cde9-202">This one is actually a static variable, but unfortunately, there is no way to tell.</span></span> <span data-ttu-id="0cde9-203">Statické objekty pro odkazové typy jsou uloženy v poli spravovaného objektu v interních strukturách modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0cde9-203">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="0cde9-204">Další případ, který může zabránit uvolnění objektu, `AssemblyLoadContext` je, když vlákno má snímek metody ze sestavení načtené do `AssemblyLoadContext` zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0cde9-204">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="0cde9-205">Můžete kontrolovat, zda jsou vyvolány spravované zásobníky volání všech vláken:</span><span class="sxs-lookup"><span data-stu-id="0cde9-205">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="0cde9-206">Příkaz znamená "použít u všech vláken `!clrstack` příkazu".</span><span class="sxs-lookup"><span data-stu-id="0cde9-206">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="0cde9-207">Následuje výstup tohoto příkazu pro příklad.</span><span class="sxs-lookup"><span data-stu-id="0cde9-207">The following is the output of that command for the example.</span></span> <span data-ttu-id="0cde9-208">LLDB v systému UNIX bohužel nemá žádný způsob, jak použít příkaz pro všechna vlákna, takže musíte ručně přepnout vlákna a zopakovat `clrstack` příkaz.</span><span class="sxs-lookup"><span data-stu-id="0cde9-208">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you must manually switch threads and repeat the `clrstack` command.</span></span> <span data-ttu-id="0cde9-209">Ignorujte všechna vlákna, kde ladicí program říká, že se nepovedlo projít spravovanou sadu.</span><span class="sxs-lookup"><span data-stu-id="0cde9-209">Ignore all threads where the debugger says "Unable to walk the managed stack".</span></span>

```console
OS Thread Id: 0x6ba8 (0)
        Child SP               IP Call Site
0000001fc697d5c8 00007ffb50d9de12 [HelperMethodFrame: 0000001fc697d5c8] System.Diagnostics.Debugger.BreakInternal()
0000001fc697d6d0 00007ffa864765fa System.Diagnostics.Debugger.Break()
0000001fc697d700 00007ffa864736bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
0000001fc697d998 00007ffae5fdc1e3 [GCFrame: 0000001fc697d998]
0000001fc697df28 00007ffae5fdc1e3 [GCFrame: 0000001fc697df28]
OS Thread Id: 0x2ae4 (1)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x61a4 (2)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x7fdc (3)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5390 (4)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5ec8 (5)
        Child SP               IP Call Site
0000001fc70ff6e0 00007ffb5437f6e4 [DebuggerU2MCatchHandlerFrame: 0000001fc70ff6e0]
OS Thread Id: 0x4624 (6)
        Child SP               IP Call Site
GetFrameContext failed: 1
0000000000000000 0000000000000000
OS Thread Id: 0x60bc (7)
        Child SP               IP Call Site
0000001fc727f158 00007ffb5437fce4 [HelperMethodFrame: 0000001fc727f158] System.Threading.Thread.SleepInternal(Int32)
0000001fc727f260 00007ffb37ea7c2b System.Threading.Thread.Sleep(Int32)
0000001fc727f290 00007ffa865005b3 test.Program.ThreadProc() [E:\unloadability\test\Program.cs @ 17]
0000001fc727f2c0 00007ffb37ea6a5b System.Threading.Thread.ThreadMain_ThreadStart()
0000001fc727f2f0 00007ffadbc4cbe3 System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)
0000001fc727f568 00007ffae5fdc1e3 [GCFrame: 0000001fc727f568]
0000001fc727f7f0 00007ffae5fdc1e3 [DebuggerU2MCatchHandlerFrame: 0000001fc727f7f0]

```

<span data-ttu-id="0cde9-210">Jak vidíte, poslední vlákno má `test.Program.ThreadProc()` .</span><span class="sxs-lookup"><span data-stu-id="0cde9-210">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="0cde9-211">Toto je funkce ze sestavení načtených do `AssemblyLoadContext` , takže udržuje `AssemblyLoadContext` Alive.</span><span class="sxs-lookup"><span data-stu-id="0cde9-211">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="0cde9-212">Příklad zdroje s problémy s načtením</span><span class="sxs-lookup"><span data-stu-id="0cde9-212">Example source with unloadability issues</span></span>

<span data-ttu-id="0cde9-213">Následující kód se používá v předchozím příkladu ladění.</span><span class="sxs-lookup"><span data-stu-id="0cde9-213">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="0cde9-214">Hlavní testovací program</span><span class="sxs-lookup"><span data-stu-id="0cde9-214">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="0cde9-215">Program byl načten do TestAssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="0cde9-215">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="0cde9-216">Následující kód představuje *test.dll* předaný `ExecuteAndUnload` metodě v hlavním testovacím programu.</span><span class="sxs-lookup"><span data-stu-id="0cde9-216">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
