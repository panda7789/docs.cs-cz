---
title: Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core
description: Zjistěte, jak používat sběratelské AssemblyLoadContext pro načítání a uvolňování spravovaných sestavení a jak ladit problémy bránící úspěchu uvolnění.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159738"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="867a3-103">Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core</span><span class="sxs-lookup"><span data-stu-id="867a3-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="867a3-104">Počínaje rozhraním .NET Core 3.0 je podporována možnost načíst a později uvolnit sadu sestavení.</span><span class="sxs-lookup"><span data-stu-id="867a3-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="867a3-105">V rozhraní .NET Framework byly k tomuto účelu použity vlastní domény aplikací, ale .NET Core podporuje jenom jednu výchozí doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="867a3-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="867a3-106">Rozhraní .NET Core 3.0 a novější <xref:System.Runtime.Loader.AssemblyLoadContext>verze podporují možnost uvolnění prostřednictvím .</span><span class="sxs-lookup"><span data-stu-id="867a3-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="867a3-107">Sadu sestavení můžete načíst do sběratelské , `AssemblyLoadContext`spustit metody v nich nebo je `AssemblyLoadContext`pouze zkontrolovat pomocí odrazu a nakonec uvolnit .</span><span class="sxs-lookup"><span data-stu-id="867a3-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="867a3-108">To uvolní sestavení naložené `AssemblyLoadContext`do .</span><span class="sxs-lookup"><span data-stu-id="867a3-108">That unloads the assemblies loaded into the `AssemblyLoadContext`.</span></span>

<span data-ttu-id="867a3-109">Existuje jeden pozoruhodný rozdíl mezi uvolněnípomocí `AssemblyLoadContext` a používáním AppDomains.</span><span class="sxs-lookup"><span data-stu-id="867a3-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="867a3-110">S AppDomains uvolnění je vynuceno.</span><span class="sxs-lookup"><span data-stu-id="867a3-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="867a3-111">V době uvolnění jsou všechna vlákna spuštěná v cílové appdomain přerušena, spravované objekty COM vytvořené v cílové službě AppDomain jsou zničeny a tak dále.</span><span class="sxs-lookup"><span data-stu-id="867a3-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, and so on.</span></span> <span data-ttu-id="867a3-112">S `AssemblyLoadContext`, vykládka je "spolupráce".</span><span class="sxs-lookup"><span data-stu-id="867a3-112">With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="867a3-113">Volání <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> metody pouze iniciuje uvolnění.</span><span class="sxs-lookup"><span data-stu-id="867a3-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="867a3-114">Vykládka končí po:</span><span class="sxs-lookup"><span data-stu-id="867a3-114">The unloading finishes after:</span></span>

- <span data-ttu-id="867a3-115">Žádná vlákna mají metody z sestavení `AssemblyLoadContext` načtených do jejich zásobníků volání.</span><span class="sxs-lookup"><span data-stu-id="867a3-115">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="867a3-116">Žádný z typů ze sestavení načtených do `AssemblyLoadContext`instancí těchto typů a samotných sestavení není odkazován:</span><span class="sxs-lookup"><span data-stu-id="867a3-116">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types, and the assemblies themselves are referenced by:</span></span>
  - <span data-ttu-id="867a3-117">Odkazy mimo písmeno `AssemblyLoadContext`a) s<xref:System.WeakReference> výjimkou <xref:System.WeakReference%601>slabých odkazů ( nebo ).</span><span class="sxs-lookup"><span data-stu-id="867a3-117">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="867a3-118">Silné popisovače systému uvolňování paměti[(GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) nebo [GCHandleType.Pinned)](xref:System.Runtime.InteropServices.GCHandleType.Pinned) `AssemblyLoadContext`z vnitřníi i vnější strany .</span><span class="sxs-lookup"><span data-stu-id="867a3-118">Strong garbage collector (GC) handles ([GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) or [GCHandleType.Pinned](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="867a3-119">Použití sběratelského kontextu AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="867a3-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="867a3-120">Tato část obsahuje podrobný podrobný kurz, který ukazuje jednoduchý způsob, jak načíst `AssemblyLoadContext`aplikaci .NET Core do sběratelské položky , spustit vstupní bod a potom ji uvolnit.</span><span class="sxs-lookup"><span data-stu-id="867a3-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="867a3-121">Kompletní ukázku najdete [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)na adrese .</span><span class="sxs-lookup"><span data-stu-id="867a3-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="867a3-122">Vytvoření sběratelského kontextu AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="867a3-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="867a3-123">Je třeba odvodit <xref:System.Runtime.Loader.AssemblyLoadContext> třídu <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> z a přetížení jeho metody.</span><span class="sxs-lookup"><span data-stu-id="867a3-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="867a3-124">Tato metoda řeší odkazy na všechna sestavení, která jsou závislosti `AssemblyLoadContext`sestavení načtendo tohoto .</span><span class="sxs-lookup"><span data-stu-id="867a3-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="867a3-125">Následující kód je příkladem nejjednodušší vlastní `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="867a3-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="867a3-126">Jak můžete vidět, `Load` metoda `null`vrátí .</span><span class="sxs-lookup"><span data-stu-id="867a3-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="867a3-127">To znamená, že všechna sestavení závislostí jsou načtena do výchozího kontextu a nový kontext obsahuje pouze sestavení, která jsou do něj explicitně načtena.</span><span class="sxs-lookup"><span data-stu-id="867a3-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="867a3-128">Pokud chcete načíst některé nebo všechny závislosti `AssemblyLoadContext` do příliš, `AssemblyDependencyResolver` můžete `Load` použít v metodě.</span><span class="sxs-lookup"><span data-stu-id="867a3-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="867a3-129">Překládá `AssemblyDependencyResolver` názvy sestavení na absolutní cesty souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="867a3-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths.</span></span> <span data-ttu-id="867a3-130">Překladač používá soubor *.deps.json* a soubory sestavení v adresáři hlavního sestavení načteného do kontextu.</span><span class="sxs-lookup"><span data-stu-id="867a3-130">The resolver uses the *.deps.json* file and assembly files in the directory of the main assembly loaded into the context.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="867a3-131">Použití vlastního sběratelského objektu AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="867a3-131">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="867a3-132">Tato část předpokládá, že `TestAssemblyLoadContext` se používá jednodušší verze programu.</span><span class="sxs-lookup"><span data-stu-id="867a3-132">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="867a3-133">Můžete vytvořit instanci `AssemblyLoadContext` vlastní a načíst sestavení do něj takto:</span><span class="sxs-lookup"><span data-stu-id="867a3-133">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="867a3-134">Pro každou sestavu, na kterou odkazuje `TestAssemblyLoadContext.Load` načtené sestavení, `TestAssemblyLoadContext` je metoda volána tak, aby se mohla rozhodnout, odkud sestavení získá.</span><span class="sxs-lookup"><span data-stu-id="867a3-134">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="867a3-135">V našem případě `null` se vrátí k označení, že by měla být načtena do výchozího kontextu z umístění, která runtime používá k načtení sestavení ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="867a3-135">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="867a3-136">Nyní, když bylo načteno sestavení, můžete z něj spustit metodu.</span><span class="sxs-lookup"><span data-stu-id="867a3-136">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="867a3-137">Spusťte metodu: `Main`</span><span class="sxs-lookup"><span data-stu-id="867a3-137">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="867a3-138">Po `Main` vrátí metoda, můžete zahájit uvolnění `Unload` buď voláním `AssemblyLoadContext` metody na vlastní nebo zbavit `AssemblyLoadContext`odkazu, který máte na :</span><span class="sxs-lookup"><span data-stu-id="867a3-138">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="867a3-139">To je dostačující k uvolnění testovacího sestavení.</span><span class="sxs-lookup"><span data-stu-id="867a3-139">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="867a3-140">Pojďme vlastně dát to všechno do samostatné non-inlineable `TestAssemblyLoadContext`metoda `Assembly`zajistit, aby , , a `MethodInfo` `Assembly.EntryPoint`() nelze udržet naživu pomocí zásobníku slot odkazy (real- nebo JIT-představil místní).</span><span class="sxs-lookup"><span data-stu-id="867a3-140">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="867a3-141">To by `TestAssemblyLoadContext` mohlo udržet naživu a zabránit vyložit.</span><span class="sxs-lookup"><span data-stu-id="867a3-141">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="867a3-142">Také vrátit slabý odkaz `AssemblyLoadContext` na tak, aby můžete použít později ke zjištění dokončení uvolnění.</span><span class="sxs-lookup"><span data-stu-id="867a3-142">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="867a3-143">Nyní můžete spustit tuto funkci k načtení, spuštění a uvolnění sestavení.</span><span class="sxs-lookup"><span data-stu-id="867a3-143">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="867a3-144">Uvolnění však není dokončena okamžitě.</span><span class="sxs-lookup"><span data-stu-id="867a3-144">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="867a3-145">Jak již bylo zmíněno, spoléhá na uvolňování shromažďovat všechny objekty z testovacího sestavení.</span><span class="sxs-lookup"><span data-stu-id="867a3-145">As previously mentioned, it relies on the garbage collector to collect all the objects from the test assembly.</span></span> <span data-ttu-id="867a3-146">V mnoha případech není nutné čekat na dokončení uvolnění.</span><span class="sxs-lookup"><span data-stu-id="867a3-146">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="867a3-147">Existují však případy, kdy je užitečné vědět, že uvolnění bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="867a3-147">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="867a3-148">Můžete například odstranit soubor sestavení, který byl načten `AssemblyLoadContext` do vlastní z disku.</span><span class="sxs-lookup"><span data-stu-id="867a3-148">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="867a3-149">V takovém případě lze použít následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="867a3-149">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="867a3-150">Aktivuje uvolňování paměti a čeká na čekající finalizační metody ve `AssemblyLoadContext` `null`smyčce, dokud není nastaven slabý odkaz na vlastní , což znamená, že byl shromážděn cílový objekt.</span><span class="sxs-lookup"><span data-stu-id="867a3-150">It triggers garbage collection and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="867a3-151">Ve většině případů je vyžadován pouze jeden průchod smyčkou.</span><span class="sxs-lookup"><span data-stu-id="867a3-151">In most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="867a3-152">Však pro složitější případy, kde objekty `AssemblyLoadContext` vytvořené kód spuštěnv mají finalizační metody, může být zapotřebí další průchody.</span><span class="sxs-lookup"><span data-stu-id="867a3-152">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="867a3-153">Událost Uvolnění</span><span class="sxs-lookup"><span data-stu-id="867a3-153">The Unloading event</span></span>

<span data-ttu-id="867a3-154">V některých případech může být nezbytné pro `AssemblyLoadContext` kód načtendo vlastní provést některé vyčištění při zahájení uvolnění.</span><span class="sxs-lookup"><span data-stu-id="867a3-154">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="867a3-155">Může například potřebovat zastavit vlákna nebo vyčistit silné úchyty GC.</span><span class="sxs-lookup"><span data-stu-id="867a3-155">For example, it may need to stop threads or clean up strong GC handles.</span></span> <span data-ttu-id="867a3-156">Událost `Unloading` lze použít v takových případech.</span><span class="sxs-lookup"><span data-stu-id="867a3-156">The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="867a3-157">Obslužná rutina, která provádí nezbytné vyčištění může být připojen k této události.</span><span class="sxs-lookup"><span data-stu-id="867a3-157">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="867a3-158">Poradce při potížích s vyprodučností</span><span class="sxs-lookup"><span data-stu-id="867a3-158">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="867a3-159">Vzhledem k kooperativní povaze vykládky, je snadné zapomenout na odkazy, které `AssemblyLoadContext` mohou být udržet věci ve sběratelství naživu a brání vykládce.</span><span class="sxs-lookup"><span data-stu-id="867a3-159">Due to the cooperative nature of the unloading, it's easy to forget about references that may be keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="867a3-160">Zde je přehled entit (některé z nich non-zřejmé), které mohou obsahovat odkazy:</span><span class="sxs-lookup"><span data-stu-id="867a3-160">Here is a summary of entities (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="867a3-161">Pravidelné odkazy držené mimo sběratelskou `AssemblyLoadContext` položku, které jsou uloženy v zásobníku slotu nebo registru procesoru (místní metoda, buď explicitně vytvořené uživatelským kódem nebo implicitně kompilátorem just-in-time (JIT), statickou proměnnou nebo silným popisovačem GC (připnutí) a přechodně odkazujícím na:</span><span class="sxs-lookup"><span data-stu-id="867a3-161">Regular references held from outside of the collectible `AssemblyLoadContext` that are stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the just-in-time (JIT) compiler), a static variable, or a strong (pinning) GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="867a3-162">Sestava naložená do `AssemblyLoadContext`sběratelského .</span><span class="sxs-lookup"><span data-stu-id="867a3-162">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="867a3-163">Typ z takového sestavení.</span><span class="sxs-lookup"><span data-stu-id="867a3-163">A type from such an assembly.</span></span>
  - <span data-ttu-id="867a3-164">Instance typu z takového sestavení.</span><span class="sxs-lookup"><span data-stu-id="867a3-164">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="867a3-165">Vlákna spuštěnkód ze sestavení načtendo `AssemblyLoadContext`sběratelské .</span><span class="sxs-lookup"><span data-stu-id="867a3-165">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="867a3-166">Instance vlastních nesběratelských `AssemblyLoadContext` typů vytvořených uvnitř `AssemblyLoadContext`sběratelského souboru .</span><span class="sxs-lookup"><span data-stu-id="867a3-166">Instances of custom, non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="867a3-167">Čekající <xref:System.Threading.RegisteredWaitHandle> instance s zpětná volání nastavená `AssemblyLoadContext`na metody ve vlastní .</span><span class="sxs-lookup"><span data-stu-id="867a3-167">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`.</span></span>

> [!TIP]
> <span data-ttu-id="867a3-168">Odkazy na objekty, které jsou uloženy v zásobníku sloty `AssemblyLoadContext` nebo registrů procesorů a které by mohly zabránit uvolnění může dojít v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="867a3-168">Object references that are stored in stack slots or processor registers and that could prevent unloading of an `AssemblyLoadContext` can occur in the following situations:</span></span>
>
> - <span data-ttu-id="867a3-169">Při volání funkce výsledky jsou předány přímo do jiné funkce, i když neexistuje žádná uživatelská vytvořená místní proměnná.</span><span class="sxs-lookup"><span data-stu-id="867a3-169">When function call results are passed directly to another function, even though there is no user-created local variable.</span></span>
> - <span data-ttu-id="867a3-170">Při kompilátoru JIT udržuje odkaz na objekt, který byl k dispozici v určitém okamžiku v metodě.</span><span class="sxs-lookup"><span data-stu-id="867a3-170">When the JIT compiler keeps a reference to an object that was available at some point in a method.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="867a3-171">Ladění problémů s uvolněním</span><span class="sxs-lookup"><span data-stu-id="867a3-171">Debug unloading issues</span></span>

<span data-ttu-id="867a3-172">Ladění problémy s uvolněním může být únavné.</span><span class="sxs-lookup"><span data-stu-id="867a3-172">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="867a3-173">Můžete se dostat do situací, kdy nevíte, `AssemblyLoadContext` co může být držení naživu, ale vyložit selže.</span><span class="sxs-lookup"><span data-stu-id="867a3-173">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span> <span data-ttu-id="867a3-174">Nejlepší zbraň na pomoc s tím je WinDbg (LLDB na Unix) s PLUGIN SOS.</span><span class="sxs-lookup"><span data-stu-id="867a3-174">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="867a3-175">Musíte najít to, co `LoaderAllocator` drží majetek `AssemblyLoadContext` k určitému živu.</span><span class="sxs-lookup"><span data-stu-id="867a3-175">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span> <span data-ttu-id="867a3-176">Modul plug-in SOS umožňuje podívat se na objekty haldy GC, jejich hierarchie a kořeny.</span><span class="sxs-lookup"><span data-stu-id="867a3-176">The SOS plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>

<span data-ttu-id="867a3-177">Chcete-li načíst plugin do ladicího programu, zadejte do příkazového řádku ladicího programu následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="867a3-177">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="867a3-178">V WinDbg (zdá se, windbg dělá, že automaticky při vloupání do .NET Core aplikace):</span><span class="sxs-lookup"><span data-stu-id="867a3-178">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="867a3-179">V LLDB:</span><span class="sxs-lookup"><span data-stu-id="867a3-179">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="867a3-180">Pojďme ladit ukázkový program, který má problémy s uvolněním.</span><span class="sxs-lookup"><span data-stu-id="867a3-180">Let's debug an example program that has problems with unloading.</span></span> <span data-ttu-id="867a3-181">Zdrojový kód je uveden níže.</span><span class="sxs-lookup"><span data-stu-id="867a3-181">Source code is included below.</span></span> <span data-ttu-id="867a3-182">Při spuštění pod WinDbg, program přejde do ladicího programu hned po pokusu o kontrolu úspěchu uvolnění.</span><span class="sxs-lookup"><span data-stu-id="867a3-182">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="867a3-183">Pak můžete začít hledat viníky.</span><span class="sxs-lookup"><span data-stu-id="867a3-183">You can then start looking for the culprits.</span></span>

> [!TIP]
> <span data-ttu-id="867a3-184">Pokud ladíte pomocí LLDB na Unixu, příkazy SOS v `!` následujících příkladech nemají před sebou.</span><span class="sxs-lookup"><span data-stu-id="867a3-184">If you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="867a3-185">Tento příkaz vypíše všechny objekty `LoaderAllocator` s názvem typu, které jsou v haldě GC.</span><span class="sxs-lookup"><span data-stu-id="867a3-185">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="867a3-186">Zde naleznete příklad:</span><span class="sxs-lookup"><span data-stu-id="867a3-186">Here is an example:</span></span>

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

<span data-ttu-id="867a3-187">V části "Statistika:" níže `MT` `MethodTable`zkontrolujte ( `System.Reflection.LoaderAllocator`), který patří do , což je objekt, na kterém nám záleží.</span><span class="sxs-lookup"><span data-stu-id="867a3-187">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="867a3-188">Potom v seznamu na začátku najděte `MT` položku s odpovídající, že jeden a získat adresu samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="867a3-188">Then, in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="867a3-189">V našem případě je to "000002b78000ce40".</span><span class="sxs-lookup"><span data-stu-id="867a3-189">In our case, it is "000002b78000ce40".</span></span>

<span data-ttu-id="867a3-190">Nyní, když známe adresu `LoaderAllocator` objektu, můžeme použít jiný příkaz k nalezení jeho kořenů GC:</span><span class="sxs-lookup"><span data-stu-id="867a3-190">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots:</span></span>

```console
!gcroot -all 0x000002b78000ce40
```

<span data-ttu-id="867a3-191">Tento příkaz vypíše řetězec odkazů na `LoaderAllocator` objekty, které vedou k instanci.</span><span class="sxs-lookup"><span data-stu-id="867a3-191">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="867a3-192">Seznam začíná kořenem, což je entita, která udržuje naše `LoaderAllocator` naživu, a proto je jádrem problému.</span><span class="sxs-lookup"><span data-stu-id="867a3-192">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem.</span></span> <span data-ttu-id="867a3-193">Kořen může být zásobníku slot, registr procesoru, popisovač GC nebo statické proměnné.</span><span class="sxs-lookup"><span data-stu-id="867a3-193">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="867a3-194">Zde je příklad výstupu příkazu: `gcroot`</span><span class="sxs-lookup"><span data-stu-id="867a3-194">Here is an example of the output of the `gcroot` command:</span></span>

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

<span data-ttu-id="867a3-195">Dalším krokem je zjistit, kde je kořen umístěn, abyste ho mohli opravit.</span><span class="sxs-lookup"><span data-stu-id="867a3-195">The next step is to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="867a3-196">Nejjednodušší případ je, když kořen je zásobníku slot nebo registr procesoru.</span><span class="sxs-lookup"><span data-stu-id="867a3-196">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="867a3-197">V takovém případě `gcroot` zobrazí název funkce, jejíž rámec obsahuje kořen a vlákno provádění této funkce.</span><span class="sxs-lookup"><span data-stu-id="867a3-197">In that case, the `gcroot` shows the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="867a3-198">Obtížný případ je, když kořen je statická proměnná nebo popisovač GC.</span><span class="sxs-lookup"><span data-stu-id="867a3-198">The difficult case is when the root is a static variable or a GC handle.</span></span>

<span data-ttu-id="867a3-199">V předchozím příkladu je první kořen `System.Reflection.RuntimeMethodInfo` místní hosti typu `example.Program.Main(System.String[])` uloženého v rámci funkce na adrese `rbp-20` (`rbp` je registr procesoru `rbp` a -20 je šestnáctkový posun od tohoto registru).</span><span class="sxs-lookup"><span data-stu-id="867a3-199">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="867a3-200">Druhý kořen je normální (silný), `GCHandle` který obsahuje odkaz `test.Test` na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="867a3-200">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span>

<span data-ttu-id="867a3-201">Třetí kořen je připnutý `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="867a3-201">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="867a3-202">Tenhle je vlastně statická proměnná, ale bohužel, neexistuje žádný způsob, jak říct.</span><span class="sxs-lookup"><span data-stu-id="867a3-202">This one is actually a static variable, but unfortunately, there is no way to tell.</span></span> <span data-ttu-id="867a3-203">Statika pro typy odkazů jsou uloženy v poli spravovaného objektu v interních runtime strukturách.</span><span class="sxs-lookup"><span data-stu-id="867a3-203">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="867a3-204">Jiný případ, který může `AssemblyLoadContext` zabránit uvolnění je, když vlákno má rámec metody `AssemblyLoadContext` ze sestavy načtendo jeho zásobníku.</span><span class="sxs-lookup"><span data-stu-id="867a3-204">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="867a3-205">Můžete zkontrolovat, že dumpingem spravované zásobníky volání všech vláken:</span><span class="sxs-lookup"><span data-stu-id="867a3-205">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="867a3-206">Příkaz znamená "použít pro všechna `!clrstack` vlákna příkaz".</span><span class="sxs-lookup"><span data-stu-id="867a3-206">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="867a3-207">Následuje výstup tohoto příkazu pro příklad.</span><span class="sxs-lookup"><span data-stu-id="867a3-207">The following is the output of that command for the example.</span></span> <span data-ttu-id="867a3-208">Bohužel, LLDB na Unixu nemá žádný způsob, jak použít příkaz pro všechna vlákna, `clrstack` takže musíte ručně přepnout vlákna a opakovat příkaz.</span><span class="sxs-lookup"><span data-stu-id="867a3-208">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you must manually switch threads and repeat the `clrstack` command.</span></span> <span data-ttu-id="867a3-209">Ignorujte všechna vlákna, kde ladicí program říká "Nelze procházet spravované zásobníku".</span><span class="sxs-lookup"><span data-stu-id="867a3-209">Ignore all threads where the debugger says "Unable to walk the managed stack".</span></span>

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

<span data-ttu-id="867a3-210">Jak můžete vidět, poslední `test.Program.ThreadProc()`vlákno má .</span><span class="sxs-lookup"><span data-stu-id="867a3-210">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="867a3-211">Toto je funkce ze sestavení `AssemblyLoadContext`načtendo , `AssemblyLoadContext` a tak udržuje naživu.</span><span class="sxs-lookup"><span data-stu-id="867a3-211">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="867a3-212">Příklad zdroje s problémy s vykládkou</span><span class="sxs-lookup"><span data-stu-id="867a3-212">Example source with unloadability issues</span></span>

<span data-ttu-id="867a3-213">Následující kód se používá v předchozím příkladu ladění.</span><span class="sxs-lookup"><span data-stu-id="867a3-213">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="867a3-214">Hlavní testovací program</span><span class="sxs-lookup"><span data-stu-id="867a3-214">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="867a3-215">Program načtený do kontextu TestAssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="867a3-215">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="867a3-216">Následující kód představuje *test.dll* předán `ExecuteAndUnload` metodě v hlavním testovacím programu.</span><span class="sxs-lookup"><span data-stu-id="867a3-216">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
