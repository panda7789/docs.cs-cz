---
title: Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core
description: Naučte se používat kolekční AssemblyLoadContext pro načítání a uvolňování spravovaných sestavení a jak ladit problémy zabraňující úspěšnému uvolnění.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159738"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="7a1d5-103">Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core</span><span class="sxs-lookup"><span data-stu-id="7a1d5-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="7a1d5-104">Počínaje rozhraním .NET Core 3,0 je podporována možnost načíst a později uvolnit sadu sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="7a1d5-105">V .NET Framework se pro tento účel používaly vlastní domény aplikací, ale .NET Core podporuje jenom jednu výchozí doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="7a1d5-106">.NET Core 3,0 a novější verze podporují odinstalaci prostřednictvím <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="7a1d5-107">Můžete načíst sadu sestavení do kolekční `AssemblyLoadContext`, provést v nich metody nebo je pouze zkontrolovat pomocí reflexe a nakonec uvolnit `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="7a1d5-108">Tím se uvolní sestavení načtená do `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-108">That unloads the assemblies loaded into the `AssemblyLoadContext`.</span></span>

<span data-ttu-id="7a1d5-109">Existuje jeden zajímavosti rozdíl mezi uvolněním pomocí `AssemblyLoadContext` a pomocí objektů třídy AppDomains.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="7a1d5-110">S objekty třídy AppDomains je uvolnění vynuceno.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="7a1d5-111">V době nenačtení jsou všechna vlákna spuštěná v cílové doméně AppDomain přerušena. spravované objekty COM vytvořené v cílové doméně AppDomain budou zničeny a tak dále.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, and so on.</span></span> <span data-ttu-id="7a1d5-112">Při `AssemblyLoadContext`je uvolnění "kooperativní".</span><span class="sxs-lookup"><span data-stu-id="7a1d5-112">With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="7a1d5-113">Volání metody <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> pouze inicializuje uvolnění.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="7a1d5-114">Uvolnění se dokončí po:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-114">The unloading finishes after:</span></span>

- <span data-ttu-id="7a1d5-115">Žádná vlákna neobsahují metody ze sestavení načtených do `AssemblyLoadContext` na jejich zásobníkech volání.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-115">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="7a1d5-116">Žádný z typů ze sestavení načtených do `AssemblyLoadContext`, instance těchto typů a samotná sestavení jsou odkazována pomocí:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-116">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types, and the assemblies themselves are referenced by:</span></span>
  - <span data-ttu-id="7a1d5-117">Odkazy mimo `AssemblyLoadContext`, s výjimkou slabých odkazů (<xref:System.WeakReference> nebo <xref:System.WeakReference%601>).</span><span class="sxs-lookup"><span data-stu-id="7a1d5-117">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="7a1d5-118">Silné popisovače uvolňování paměti (GC) ([GCHandleType. Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) nebo [GCHandleType. připnutý](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) zevnitř i mimo `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-118">Strong garbage collector (GC) handles ([GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) or [GCHandleType.Pinned](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="7a1d5-119">Použití kolekční AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="7a1d5-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="7a1d5-120">Tato část obsahuje podrobný návod, který ukazuje jednoduchý způsob, jak načíst aplikaci .NET Core do kolekční `AssemblyLoadContext`, spustit její vstupní bod a pak ji uvolnit.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="7a1d5-121">Úplnou ukázku najdete na [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span><span class="sxs-lookup"><span data-stu-id="7a1d5-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="7a1d5-122">Vytvoření kolekční AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="7a1d5-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="7a1d5-123">Musíte třídu odvodit z <xref:System.Runtime.Loader.AssemblyLoadContext> a přetížit její <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7a1d5-124">Tato metoda překládá odkazy na všechna sestavení, která jsou závislá na sestaveních, která jsou načtena do tohoto `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="7a1d5-125">Následující kód je příkladem nejjednoduššího vlastního `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="7a1d5-126">Jak vidíte, metoda `Load` vrátí `null`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="7a1d5-127">To znamená, že všechna sestavení závislostí jsou načtena do výchozího kontextu a nový kontext obsahuje pouze sestavení, která jsou do něj explicitně načtena.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="7a1d5-128">Pokud chcete některé nebo všechny závislosti načíst do `AssemblyLoadContext`, můžete použít `AssemblyDependencyResolver` v metodě `Load`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="7a1d5-129">`AssemblyDependencyResolver` vyřeší názvy sestavení k absolutním cestám souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths.</span></span> <span data-ttu-id="7a1d5-130">Překladač používá soubor *. DEPS. JSON* a soubory sestavení v adresáři hlavního sestavení načteného do kontextu.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-130">The resolver uses the *.deps.json* file and assembly files in the directory of the main assembly loaded into the context.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="7a1d5-131">Použít vlastní AssemblyLoadContext kolekční</span><span class="sxs-lookup"><span data-stu-id="7a1d5-131">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="7a1d5-132">V této části se předpokládá, že se používá jednodušší verze `TestAssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-132">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="7a1d5-133">Můžete vytvořit instanci vlastního `AssemblyLoadContext` a načíst do něj sestavení následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-133">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="7a1d5-134">Pro každé sestavení, na které odkazuje načtené sestavení, je volána metoda `TestAssemblyLoadContext.Load`, aby `TestAssemblyLoadContext` mohl rozhodnout, kde získat sestavení z.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-134">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="7a1d5-135">V našem případě vrátí `null`, aby označoval, že by měl být načten do výchozího kontextu z umístění, která modul runtime používá k načítání sestavení ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-135">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="7a1d5-136">Nyní, když bylo sestavení načteno, lze z něj spustit metodu.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-136">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="7a1d5-137">Spusťte metodu `Main`:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-137">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="7a1d5-138">Po návratu metody `Main` můžete iniciovat uvolnění voláním metody `Unload` na vlastní `AssemblyLoadContext` nebo odložením odkazu, který máte `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-138">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="7a1d5-139">To je dostačující pro uvolnění testovacího sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-139">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="7a1d5-140">Pojďme to všechno využít k samostatné nestandardní metodě, aby se zajistilo, že `TestAssemblyLoadContext`, `Assembly`a `MethodInfo` (`Assembly.EntryPoint`) se nedají udržovat naživu pomocí odkazů na slot zásobníku (lokálních hodnot Real-nebo JIT).</span><span class="sxs-lookup"><span data-stu-id="7a1d5-140">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="7a1d5-141">To může zůstat `TestAssemblyLoadContext` Alive a zabránit uvolnění.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-141">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="7a1d5-142">Také vrátí slabý odkaz na `AssemblyLoadContext`, aby jej bylo možné použít později ke zjištění dokončení uvolnění.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-142">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="7a1d5-143">Nyní můžete tuto funkci spustit, chcete-li načíst, spustit a uvolnit sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-143">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="7a1d5-144">Uvolnění se ale okamžitě nedokončilo.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-144">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="7a1d5-145">Jak už jsme uvedli, spoléhá se na systém uvolňování paměti ke shromáždění všech objektů z testovacího sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-145">As previously mentioned, it relies on the garbage collector to collect all the objects from the test assembly.</span></span> <span data-ttu-id="7a1d5-146">V mnoha případech není nutné čekat na dokončení uvolnění.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-146">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="7a1d5-147">Existují však případy, kdy je užitečné zjistit, že uvolnění bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-147">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="7a1d5-148">Například může být vhodné odstranit soubor sestavení, který byl načten do vlastního `AssemblyLoadContext` z disku.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-148">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="7a1d5-149">V takovém případě lze použít následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-149">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="7a1d5-150">Aktivuje uvolňování paměti a čeká na čekající finalizační metody ve smyčce, dokud nebude slabý odkaz na vlastní `AssemblyLoadContext` nastaven na `null`, což značí, že byl cílový objekt shromážděn.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-150">It triggers garbage collection and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="7a1d5-151">Ve většině případů je zapotřebí pouze jeden průchod smyčkou.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-151">In most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="7a1d5-152">Nicméně pro složitější případy, kdy objekty vytvořené kódem běžícím v `AssemblyLoadContext` mají finalizační metody, mohou být potřeba další průchody.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-152">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="7a1d5-153">Událost uvolnění</span><span class="sxs-lookup"><span data-stu-id="7a1d5-153">The Unloading event</span></span>

<span data-ttu-id="7a1d5-154">V některých případech může být nutné, aby kód byl načten do vlastního `AssemblyLoadContext` k provedení nějakého vyčištění při zahájení uvolnění.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-154">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="7a1d5-155">Například může být nutné zastavit vlákna nebo vyčistit silné obslužné rutiny GC.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-155">For example, it may need to stop threads or clean up strong GC handles.</span></span> <span data-ttu-id="7a1d5-156">V takových případech lze použít událost `Unloading`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-156">The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="7a1d5-157">Obslužná rutina, která provede potřebné vyčištění, může být do této události zapojování.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-157">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="7a1d5-158">Řešení potíží s nezátěží</span><span class="sxs-lookup"><span data-stu-id="7a1d5-158">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="7a1d5-159">Z důvodu kooperativního charakteru uvolňování je snadné zapomenout odkazy, které mohou udržet kolekční `AssemblyLoadContext` Alive a zabránit uvolnění.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-159">Due to the cooperative nature of the unloading, it's easy to forget about references that may be keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="7a1d5-160">Tady je souhrn entit (některé z nich není zřejmé), které můžou obsahovat odkazy:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-160">Here is a summary of entities (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="7a1d5-161">Běžné odkazy držené mimo kolekční `AssemblyLoadContext`, které jsou uloženy v zásobníku zásobníku nebo v registru procesoru (místní metody, buď explicitně vytvořené kódem uživatele nebo implicitně kompilátorem JIT (just-in-time)), statickou proměnnou nebo silným (připnutím) popisovač GC a umožňujícím přechod na:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-161">Regular references held from outside of the collectible `AssemblyLoadContext` that are stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the just-in-time (JIT) compiler), a static variable, or a strong (pinning) GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="7a1d5-162">Sestavení načtené do kolekční `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-162">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="7a1d5-163">Typ z takového sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-163">A type from such an assembly.</span></span>
  - <span data-ttu-id="7a1d5-164">Instance typu z takového sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-164">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="7a1d5-165">Vlákna spouštějící kód ze sestavení načteného do kolekční `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-165">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="7a1d5-166">Instance vlastních typů, které nejsou kolekční `AssemblyLoadContext` vytvořené v `AssemblyLoadContext`kolekční.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-166">Instances of custom, non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="7a1d5-167">Čeká se na <xref:System.Threading.RegisteredWaitHandle> instance s zpětnými voláními nastavenými na metody v vlastní `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-167">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`.</span></span>

> [!TIP]
> <span data-ttu-id="7a1d5-168">Odkazy na objekty, které jsou uloženy v paticích zásobníku nebo v registrech procesorů a které by mohly zabránit vykládku `AssemblyLoadContext` mohou nastat v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-168">Object references that are stored in stack slots or processor registers and that could prevent unloading of an `AssemblyLoadContext` can occur in the following situations:</span></span>
>
> - <span data-ttu-id="7a1d5-169">Když jsou výsledky volání funkce předány přímo jiné funkci, i když není k dispozici místní proměnná vytvořená uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-169">When function call results are passed directly to another function, even though there is no user-created local variable.</span></span>
> - <span data-ttu-id="7a1d5-170">Když kompilátor JIT udržuje odkaz na objekt, který byl k dispozici v nějakém okamžiku v metodě.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-170">When the JIT compiler keeps a reference to an object that was available at some point in a method.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="7a1d5-171">Problémy při uvolňování ladění</span><span class="sxs-lookup"><span data-stu-id="7a1d5-171">Debug unloading issues</span></span>

<span data-ttu-id="7a1d5-172">Problémy ladění s uvolněním můžou být zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-172">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="7a1d5-173">Můžete se dostat do situací, kdy nevíte, co by mohlo držet `AssemblyLoadContext` Alive, ale uvolnění se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-173">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span> <span data-ttu-id="7a1d5-174">Nejlepší zbraně, která vám to umožňuje, je WinDbg (LLDB v UNIX) s modulem plug-in SOS.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-174">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="7a1d5-175">Potřebujete najít, co udržuje `LoaderAllocator` patří do konkrétní `AssemblyLoadContext` Alive.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-175">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span> <span data-ttu-id="7a1d5-176">Modul plug-in SOS vám umožní podívat se na objekty haldy GC, jejich hierarchie a kořeny.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-176">The SOS plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>

<span data-ttu-id="7a1d5-177">Chcete-li načíst modul plug-in do ladicího programu, zadejte následující příkaz v příkazovém řádku ladicího programu:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-177">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="7a1d5-178">V programu WinDbg (při přerušení do aplikace .NET Core se to jeví jako WinDbg):</span><span class="sxs-lookup"><span data-stu-id="7a1d5-178">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="7a1d5-179">V LLDB:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-179">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="7a1d5-180">Pojďme ladit ukázkový program, který obsahuje problémy s uvolněním.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-180">Let's debug an example program that has problems with unloading.</span></span> <span data-ttu-id="7a1d5-181">Zdrojový kód je uveden níže.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-181">Source code is included below.</span></span> <span data-ttu-id="7a1d5-182">Při spuštění v rámci programu WinDbg se program přeruší do ladicího programu hned po pokusu o kontrolu úspěšného načtení.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-182">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="7a1d5-183">Pak můžete začít hledat v culprits.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-183">You can then start looking for the culprits.</span></span>

> [!TIP]
> <span data-ttu-id="7a1d5-184">Pokud ladíte pomocí LLDB v systému UNIX, příkazy SOS v následujících příkladech nemají `!` před nimi.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-184">If you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="7a1d5-185">Tento příkaz vypíše všechny objekty s názvem typu, který obsahuje `LoaderAllocator` v haldě GC.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-185">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="7a1d5-186">Zde naleznete příklad:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-186">Here is an example:</span></span>

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

<span data-ttu-id="7a1d5-187">V níže uvedené části "Statistika:" si Projděte `MT` (`MethodTable`) patřící do `System.Reflection.LoaderAllocator`, což je objekt, o kterém se zajímá.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-187">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="7a1d5-188">Potom v seznamu na začátku Najděte položku s `MT` odpovídající této adrese a získejte adresu samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-188">Then, in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="7a1d5-189">V našem případě je to "000002b78000ce40".</span><span class="sxs-lookup"><span data-stu-id="7a1d5-189">In our case, it is "000002b78000ce40".</span></span>

<span data-ttu-id="7a1d5-190">Teď, když znáte adresu `LoaderAllocator`ho objektu, můžeme k vyhledání jeho kořenů GC použít jiný příkaz:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-190">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots:</span></span>

```console
!gcroot -all 0x000002b78000ce40
```

<span data-ttu-id="7a1d5-191">Tento příkaz vypíše řetěz odkazů na objekty, které vedou k instanci `LoaderAllocator`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-191">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="7a1d5-192">Seznam začíná kořenovým adresářem, který je entitou, která udržuje naši `LoaderAllocator` Alive, a proto je jádrem problému.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-192">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem.</span></span> <span data-ttu-id="7a1d5-193">Kořenem může být slot zásobníku, registr procesoru, popisovač GC nebo statická proměnná.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-193">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="7a1d5-194">Tady je příklad výstupu `gcroot` příkazu:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-194">Here is an example of the output of the `gcroot` command:</span></span>

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

<span data-ttu-id="7a1d5-195">Dalším krokem je zjistit, kde se nachází kořenový adresář, abyste ho mohli opravit.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-195">The next step is to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="7a1d5-196">Nejjednodušším případem je, že kořen je slot zásobníku nebo registr procesoru.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-196">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="7a1d5-197">V takovém případě `gcroot` zobrazuje název funkce, jejíž rámec obsahuje kořen a vlákno, které tuto funkci spouští.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-197">In that case, the `gcroot` shows the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="7a1d5-198">Těžké velká písmena jsou v případě, že kořen je statická proměnná nebo popisovač GC.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-198">The difficult case is when the root is a static variable or a GC handle.</span></span>

<span data-ttu-id="7a1d5-199">V předchozím příkladu je prvním kořenem typ `System.Reflection.RuntimeMethodInfo` uložený v rámci `example.Program.Main(System.String[])` funkce na adrese `rbp-20` (`rbp` je registr registru `rbp` a-20 je hexadecimální posun od tohoto registru).</span><span class="sxs-lookup"><span data-stu-id="7a1d5-199">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="7a1d5-200">Druhý kořen je normální (silný) `GCHandle`, která obsahuje odkaz na instanci `test.Test` třídy.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-200">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span>

<span data-ttu-id="7a1d5-201">Třetí kořen je připnutý `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-201">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="7a1d5-202">Toto je vlastně statická proměnná, ale bohužel neexistuje žádný způsob, jak říct.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-202">This one is actually a static variable, but unfortunately, there is no way to tell.</span></span> <span data-ttu-id="7a1d5-203">Statické objekty pro odkazové typy jsou uloženy v poli spravovaného objektu v interních strukturách modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-203">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="7a1d5-204">Další případ, který může zabránit uvolnění `AssemblyLoadContext`, je, když vlákno obsahuje snímek metody ze sestavení načteného do `AssemblyLoadContext` v jeho zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-204">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="7a1d5-205">Můžete kontrolovat, zda jsou vyvolány spravované zásobníky volání všech vláken:</span><span class="sxs-lookup"><span data-stu-id="7a1d5-205">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="7a1d5-206">Příkaz znamená "použít u všech vláken `!clrstack` příkazu".</span><span class="sxs-lookup"><span data-stu-id="7a1d5-206">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="7a1d5-207">Následuje výstup tohoto příkazu pro příklad.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-207">The following is the output of that command for the example.</span></span> <span data-ttu-id="7a1d5-208">LLDB v systému UNIX bohužel nemá žádný způsob, jak použít příkaz pro všechna vlákna, takže musíte ručně přepnout vlákna a zopakovat příkaz `clrstack`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-208">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you must manually switch threads and repeat the `clrstack` command.</span></span> <span data-ttu-id="7a1d5-209">Ignorujte všechna vlákna, kde ladicí program říká, že se nepovedlo projít spravovanou sadu.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-209">Ignore all threads where the debugger says "Unable to walk the managed stack".</span></span>

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

<span data-ttu-id="7a1d5-210">Jak vidíte, poslední vlákno má `test.Program.ThreadProc()`.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-210">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="7a1d5-211">Toto je funkce ze sestavení načtených do `AssemblyLoadContext`, takže udržuje `AssemblyLoadContext` Alive.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-211">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="7a1d5-212">Příklad zdroje s problémy s načtením</span><span class="sxs-lookup"><span data-stu-id="7a1d5-212">Example source with unloadability issues</span></span>

<span data-ttu-id="7a1d5-213">Následující kód se používá v předchozím příkladu ladění.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-213">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="7a1d5-214">Hlavní testovací program</span><span class="sxs-lookup"><span data-stu-id="7a1d5-214">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="7a1d5-215">Program byl načten do TestAssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="7a1d5-215">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="7a1d5-216">Následující kód představuje *test. dll* předaný metodě `ExecuteAndUnload` v hlavním testovacím programu.</span><span class="sxs-lookup"><span data-stu-id="7a1d5-216">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
