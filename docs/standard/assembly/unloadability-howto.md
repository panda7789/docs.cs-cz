---
title: Jak používat a unloadability sestavení ladění v rozhraní .NET Core
description: Další informace o použití kolekční AssemblyLoadContext pro načítání a uvolňování spravovaných sestavení a jak ladit problémy brání uvolňování úspěch.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 2929110952feb0913f21a9c69975cc605f49c646
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627789"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="2a76e-103">Jak používat a unloadability sestavení ladění v rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="2a76e-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="2a76e-104">Od verze .NET Core 3.0, umožňuje načtení a uvolnění později sadu sestavení je podporován.</span><span class="sxs-lookup"><span data-stu-id="2a76e-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="2a76e-105">V rozhraní .NET Framework vlastní aplikaci domén byly použity pro tento účel, ale .NET Core podporuje pouze jeden výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="2a76e-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="2a76e-106">.NET core 3.0 a novější verze podporují unloadability prostřednictvím <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="2a76e-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="2a76e-107">Sadu sestavení lze načíst do kolekční `AssemblyLoadContext`, spouštění metody v nich nebo je právě zkontrolovat pomocí reflexe a nakonec uvolnit `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="2a76e-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="2a76e-108">Který uvolní sestavení načtená do nich `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="2a76e-108">That unloads the assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="2a76e-109">Existuje jeden zajímavosti rozdíl mezi použitím uvolňování `AssemblyLoadContext` a pomocí objektů třídy AppDomains.</span><span class="sxs-lookup"><span data-stu-id="2a76e-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="2a76e-110">Pomocí objektů třídy AppDomains je vynucena uvolnění.</span><span class="sxs-lookup"><span data-stu-id="2a76e-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="2a76e-111">Všechna vlákna spuštěná v cílové doméně aplikace při jeho uvolnění budou zrušeny, spravované objekty modelu COM, které jsou vytvořeny v cílové doméně aplikace, jsou zničeny, atd. S `AssemblyLoadContext`, je "spolupráci" uvolnění z paměti.</span><span class="sxs-lookup"><span data-stu-id="2a76e-111">At the unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, etc. With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="2a76e-112">Volání <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> metoda právě zahájí uvolnění.</span><span class="sxs-lookup"><span data-stu-id="2a76e-112">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="2a76e-113">Uvolnění dokončí po:</span><span class="sxs-lookup"><span data-stu-id="2a76e-113">The unloading finishes after:</span></span>

- <span data-ttu-id="2a76e-114">Žádná vlákna mají metody ze sestavení načtena do `AssemblyLoadContext` na svých zásobníků volání.</span><span class="sxs-lookup"><span data-stu-id="2a76e-114">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="2a76e-115">Žádný z typů ze sestavení načtena do `AssemblyLoadContext`, instancí těchto typů a sestavení samotné mimo `AssemblyLoadContext` odkazuje:</span><span class="sxs-lookup"><span data-stu-id="2a76e-115">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types and the assemblies themselves outside of the `AssemblyLoadContext` are referenced by:</span></span>
  - <span data-ttu-id="2a76e-116">Mimo se odkazuje `AssemblyLoadContext`, kromě slabé odkazy (<xref:System.WeakReference> nebo <xref:System.WeakReference%601>).</span><span class="sxs-lookup"><span data-stu-id="2a76e-116">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="2a76e-117">Silná popisovačů (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span><span class="sxs-lookup"><span data-stu-id="2a76e-117">Strong GC handles (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span></span> <span data-ttu-id="2a76e-118">nebo <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) z uvnitř i mimo `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="2a76e-118">or <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="using-collectible-assemblyloadcontext"></a><span data-ttu-id="2a76e-119">Pomocí kolekční AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="2a76e-119">Using collectible AssemblyLoadContext</span></span>

<span data-ttu-id="2a76e-120">Tato část obsahuje podrobné podrobný kurz, který ukazuje jednoduchý způsob, jak načíst aplikaci .NET Core do kolekční `AssemblyLoadContext`, provést jeho vstupního bodu a potom ho.</span><span class="sxs-lookup"><span data-stu-id="2a76e-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="2a76e-121">Můžete najít úplnou ukázku v <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.</span><span class="sxs-lookup"><span data-stu-id="2a76e-121">You can find a complete sample at <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="2a76e-122">Vytvoření kolekční AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="2a76e-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="2a76e-123">Je nutné odvozovat třídu z <xref:System.Runtime.Loader.AssemblyLoadContext> a přetížení jeho <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="2a76e-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2a76e-124">Že metoda překládá odkazy na všechna sestavení, která jsou závislosti sestavení načtena do které `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="2a76e-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>
<span data-ttu-id="2a76e-125">Následující kód je příkladem nejjednodušší vlastní `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="2a76e-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="2a76e-126">Jak je vidět, `Load` vrátí metoda `null`.</span><span class="sxs-lookup"><span data-stu-id="2a76e-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="2a76e-127">To znamená, že všechny závislosti sestavení jsou načtena do výchozí kontext a nový kontext obsahuje jenom sestavení explicitně do něho načtené.</span><span class="sxs-lookup"><span data-stu-id="2a76e-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="2a76e-128">Pokud chcete načíst některé nebo všechny závislosti do `AssemblyLoadContext` příliš, můžete použít `AssemblyDependencyResolver` v `Load` metody.</span><span class="sxs-lookup"><span data-stu-id="2a76e-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="2a76e-129">`AssemblyDependencyResolver` Překládá názvy sestavení na absolutní sestavení pomocí cesty k souborům `*.deps.json` soubor v tomto adresáři hlavní sestavení načteno do kontextu a použití souborů sestavení v tomto adresáři obsažené.</span><span class="sxs-lookup"><span data-stu-id="2a76e-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths using the `*.deps.json` file contained in the directory of the main assembly loaded into the context and using assembly files in that directory.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="2a76e-130">Použít vlastní kolekční AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="2a76e-130">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="2a76e-131">V této části se předpokládá jednodušší verzi `TestAssemblyLoadContext` je používán.</span><span class="sxs-lookup"><span data-stu-id="2a76e-131">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="2a76e-132">Můžete vytvořit instanci vlastního `AssemblyLoadContext` a načtení sestavení do něj následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2a76e-132">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="2a76e-133">Pro každého z těchto sestavení načtené sestavení odkazuje `TestAssemblyLoadContext.Load` volání metody tak, aby `TestAssemblyLoadContext` můžete rozhodnout, kde lze získat sestavení z.</span><span class="sxs-lookup"><span data-stu-id="2a76e-133">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="2a76e-134">V našem případě vrátí `null` k označení, že se mají načíst do výchozí kontext z umístění, které modul runtime používá k načtení sestavení ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="2a76e-134">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="2a76e-135">Teď, když sestavení bylo načteno, můžete spustit metodu z něj.</span><span class="sxs-lookup"><span data-stu-id="2a76e-135">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="2a76e-136">Spustit `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="2a76e-136">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="2a76e-137">Po `Main` metoda vrací výsledek, můžete zahájit uvolnění buď voláním `Unload` metodu na vlastní `AssemblyLoadContext` nebo jsme se zbavili odkazu je nutné `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="2a76e-137">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="2a76e-138">To stačí pro uvolnění testovacího sestavení.</span><span class="sxs-lookup"><span data-stu-id="2a76e-138">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="2a76e-139">Pojďme to všechno ve skutečnosti vložit do samostatné-inlineable metody zajistit, aby `TestAssemblyLoadContext`, `Assembly`, a `MethodInfo` ( `Assembly.EntryPoint`) nemůže být zachováno zásobníku slotu odkazy (zavedené reálném nebo JIT místní hodnoty).</span><span class="sxs-lookup"><span data-stu-id="2a76e-139">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="2a76e-140">Který by mohl vést `TestAssemblyLoadContext` aktivní a zabránit uvolnění z paměti.</span><span class="sxs-lookup"><span data-stu-id="2a76e-140">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="2a76e-141">Kromě toho vrátí Slabý odkaz na `AssemblyLoadContext` tak, aby ho můžete použít později ke zjištění dokončení uvolnění z paměti.</span><span class="sxs-lookup"><span data-stu-id="2a76e-141">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="2a76e-142">Teď můžete spouštět tuto funkci k načtení, spuštění a uvolnění sestavení.</span><span class="sxs-lookup"><span data-stu-id="2a76e-142">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="2a76e-143">Ale uvolnění nedokončí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="2a76e-143">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="2a76e-144">Jak už jsme zmínili spoléhá na uvolňování paměti – ke shromažďování všech objektů z testovacího sestavení.</span><span class="sxs-lookup"><span data-stu-id="2a76e-144">As previously mentioned, it relies on the GC to collect all the objects from the test assembly.</span></span> <span data-ttu-id="2a76e-145">V mnoha případech není potřeba počkat na dokončení uvolnění z paměti.</span><span class="sxs-lookup"><span data-stu-id="2a76e-145">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="2a76e-146">Existují však případy, kdy je užitečné vědět, že byla dokončena uvolnění z paměti.</span><span class="sxs-lookup"><span data-stu-id="2a76e-146">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="2a76e-147">Můžete například odstranit soubor sestavení, která byla načtena do vlastní `AssemblyLoadContext` z disku.</span><span class="sxs-lookup"><span data-stu-id="2a76e-147">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="2a76e-148">V takovém případě můžete použít následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="2a76e-148">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="2a76e-149">Aktivuje serverem globálního katalogu a čeká na čekající finalizační metody ve smyčce do Slabý odkaz na vlastní `AssemblyLoadContext` je nastavena na `null`, která cílový objekt byl shromážděn.</span><span class="sxs-lookup"><span data-stu-id="2a76e-149">It triggers a GC and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="2a76e-150">Všimněte si, že ve většině případů je vyžadována pouze jeden průchodu smyčky.</span><span class="sxs-lookup"><span data-stu-id="2a76e-150">Note that in most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="2a76e-151">U složitějších případech, kdy objekty vytvořené v kódu spuštěném však `AssemblyLoadContext` mají finalizační metody, může být potřeba další předá.</span><span class="sxs-lookup"><span data-stu-id="2a76e-151">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="2a76e-152">Události uvolňování</span><span class="sxs-lookup"><span data-stu-id="2a76e-152">The Unloading event</span></span>

<span data-ttu-id="2a76e-153">V některých případech může být nezbytné pro kód načtený do vlastní `AssemblyLoadContext` provést trochu pořádek v případě, uvolnění je inicioval.</span><span class="sxs-lookup"><span data-stu-id="2a76e-153">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="2a76e-154">Například může potřebovat zastavit vlákna, odstraňte některé silné popisovačů GC atd. `Unloading` Událost lze použít v takových případech.</span><span class="sxs-lookup"><span data-stu-id="2a76e-154">For example, it may need to stop threads, clean up some strong GC handles, etc. The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="2a76e-155">K této události lze využívat obslužnou rutinu, která provádí potřebné vyčištění.</span><span class="sxs-lookup"><span data-stu-id="2a76e-155">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="2a76e-156">Řešení potíží s unloadability</span><span class="sxs-lookup"><span data-stu-id="2a76e-156">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="2a76e-157">Vzhledem k kooperativní povaze uvolnění, je snadné zapomenout o odkazech na uchovávání věci v kolekční `AssemblyLoadContext` aktivní a brání uvolnění z paměti.</span><span class="sxs-lookup"><span data-stu-id="2a76e-157">Due to the cooperative nature of the unloading, it's easy to forget about references keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="2a76e-158">Tady je přehled věcí, (některé z nich není zřejmé), která mohou obsahovat odkazy:</span><span class="sxs-lookup"><span data-stu-id="2a76e-158">Here is a summary of things (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="2a76e-159">Pravidelné odkazy uchovávat z mimo kolekční `AssemblyLoadContext`, uložené v datová oblast zásobníku nebo registru procesoru (metoda lokálních proměnných, buď explicitně vytvořeny pomocí uživatelského kódu nebo implicitně vypršením JIT), statická proměnná nebo popisovače GC silné / Připnutí a tranzitivně odkazuje na:</span><span class="sxs-lookup"><span data-stu-id="2a76e-159">Regular references held from outside of the collectible `AssemblyLoadContext`, stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the JIT), a static variable or a strong / pinning GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="2a76e-160">Sestavení načtena do kolekční `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="2a76e-160">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="2a76e-161">Typ z těchto sestavení.</span><span class="sxs-lookup"><span data-stu-id="2a76e-161">A type from such an assembly.</span></span>
  - <span data-ttu-id="2a76e-162">Instance typu z těchto sestavení.</span><span class="sxs-lookup"><span data-stu-id="2a76e-162">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="2a76e-163">Vlákna spuštěná kód ze sestavení načtena do kolekční `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="2a76e-163">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="2a76e-164">Instance vlastní nekolekční `AssemblyLoadContext` vytvořené v rámci služby kolekční typy `AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="2a76e-164">Instances of custom non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`</span></span>
- <span data-ttu-id="2a76e-165">Čekající <xref:System.Threading.RegisteredWaitHandle> nastavit instancí pomocí zpětných volání metod ve vlastní `AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="2a76e-165">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`</span></span>

<span data-ttu-id="2a76e-166">Pokyny k vyhledání datová oblast zásobníku / register procesoru kořenová objektu:</span><span class="sxs-lookup"><span data-stu-id="2a76e-166">Hints to find stack slot / processor register rooting an object:</span></span>

- <span data-ttu-id="2a76e-167">Předání volání funkce výsledky přímo do jiné funkce mohou vytvořit kořenové, i když neexistuje žádný uživatel vytvořil místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="2a76e-167">Passing function call results directly to another function may create a root even though there is no user-created local variable.</span></span>
- <span data-ttu-id="2a76e-168">Pokud odkaz na objekt byla k dispozici v libovolném okamžiku v metodě, kompilátor JIT se možná rozhodli zachovávat odkaz v datová oblast zásobníku / procesoru zaregistrujte se na tak dlouho, dokud ji chce, aby se v aktuální funkci.</span><span class="sxs-lookup"><span data-stu-id="2a76e-168">If a reference to an object was available at any point in a method, the JIT might have decided to keep the reference in a stack slot / processor register for as long as it wants in the current function.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="2a76e-169">Ladění problémů uvolňování</span><span class="sxs-lookup"><span data-stu-id="2a76e-169">Debug unloading issues</span></span>

<span data-ttu-id="2a76e-170">Ladění problémů s uvolnění může být zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="2a76e-170">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="2a76e-171">Může nastat situace, kde zatím nevíte, co můžete uchovávající `AssemblyLoadContext` aktivní, ale selže uvolnění z paměti.</span><span class="sxs-lookup"><span data-stu-id="2a76e-171">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span>
<span data-ttu-id="2a76e-172">Nejlepší zbraň a Postavte se nápovědu, která je pomocí modulu plug-in SOS WinDbg (LLDB v Unixu).</span><span class="sxs-lookup"><span data-stu-id="2a76e-172">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="2a76e-173">Je potřeba najít, co je udržovat `LoaderAllocator` patřící do konkrétní `AssemblyLoadContext` zachování připojení.</span><span class="sxs-lookup"><span data-stu-id="2a76e-173">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span>
<span data-ttu-id="2a76e-174">Tento modul plug-in můžete se podívat na objektů haldy GC, jejich hierarchie a kořenové adresáře.</span><span class="sxs-lookup"><span data-stu-id="2a76e-174">This plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>
<span data-ttu-id="2a76e-175">Načtení modulu plug-in do ladicího programu, zadejte následující příkaz v příkazovém řádku ladicího programu:</span><span class="sxs-lookup"><span data-stu-id="2a76e-175">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="2a76e-176">V rámci WinDbg (zdá se, že WinDbg provede automaticky při rozdělení do aplikace .NET Core):</span><span class="sxs-lookup"><span data-stu-id="2a76e-176">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="2a76e-177">V LLDB:</span><span class="sxs-lookup"><span data-stu-id="2a76e-177">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="2a76e-178">Chcete-li ladit ukázkový program, který má problémy s uvolnění si vyzkoušíme.</span><span class="sxs-lookup"><span data-stu-id="2a76e-178">Let's try to debug an example program that has problems with unloading.</span></span> <span data-ttu-id="2a76e-179">Zdrojový kód je uveden níže.</span><span class="sxs-lookup"><span data-stu-id="2a76e-179">Source code is included below.</span></span> <span data-ttu-id="2a76e-180">Při spuštění v rámci WinDbg, program se rozdělí do pravé ladicí program po pokusu o odeslání pro úspěch uvolnění z paměti.</span><span class="sxs-lookup"><span data-stu-id="2a76e-180">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="2a76e-181">Potom můžete spustit hledání culprits.</span><span class="sxs-lookup"><span data-stu-id="2a76e-181">You can then start looking for the culprits.</span></span>

<span data-ttu-id="2a76e-182">Všimněte si, že pokud ladíte pomocí LLDB v systému Unix, v následujících příkladech příkazů SOS nemá `!` před nimi.</span><span class="sxs-lookup"><span data-stu-id="2a76e-182">Note that if you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="2a76e-183">Tento příkaz vypíše všechny objekty s názvem typu obsahujícím `LoaderAllocator` , které jsou v haldě GC.</span><span class="sxs-lookup"><span data-stu-id="2a76e-183">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="2a76e-184">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="2a76e-184">Here is an example:</span></span>

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

<span data-ttu-id="2a76e-185">V "statistiky:" část pod kontrolu `MT` (`MethodTable`) patřící do `System.Reflection.LoaderAllocator`, což je objekt starosti.</span><span class="sxs-lookup"><span data-stu-id="2a76e-185">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="2a76e-186">V seznamu na začátku, vyhledejte položku s `MT` porovnávání, že jedna a získejte adresu samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="2a76e-186">Then in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="2a76e-187">V našem případě je "000002b78000ce40"</span><span class="sxs-lookup"><span data-stu-id="2a76e-187">In our case, it is "000002b78000ce40"</span></span>

<span data-ttu-id="2a76e-188">Teď, když víme adresu `LoaderAllocator` objektu, můžeme použít jiný příkaz Najít jeho kořeny uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="2a76e-188">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots</span></span>

```console
!gcroot -all 0x000002b78000ce40 
```

<span data-ttu-id="2a76e-189">Tento příkaz vypíše řetěz odkazů na objekty, které vedly k `LoaderAllocator` instance.</span><span class="sxs-lookup"><span data-stu-id="2a76e-189">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="2a76e-190">V seznamu spustí s kořenem, což je entita, která zajišťuje naše `LoaderAllocator` aktivní a proto je základní problém, kterou ladíte.</span><span class="sxs-lookup"><span data-stu-id="2a76e-190">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem you're debugging.</span></span> <span data-ttu-id="2a76e-191">Kořen může být datová oblast zásobníku, registru procesoru, popisovače GC nebo statická proměnná.</span><span class="sxs-lookup"><span data-stu-id="2a76e-191">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="2a76e-192">Tady je příklad výstupu `gcroot` příkaz:</span><span class="sxs-lookup"><span data-stu-id="2a76e-192">Here is an example of the output of the `gcroot` command:</span></span>

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

<span data-ttu-id="2a76e-193">Teď je potřeba zjistit, kde se kořenovém adresáři nachází, můžete je vyřešit.</span><span class="sxs-lookup"><span data-stu-id="2a76e-193">Now you need to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="2a76e-194">Nejjednodušší případ je, když kořenový adresář je datová oblast zásobníku nebo registru procesoru.</span><span class="sxs-lookup"><span data-stu-id="2a76e-194">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="2a76e-195">V takovém případě `gcroot` zobrazuje název funkce, jejíž snímek neobsahuje kořenový adresář a vlákna, které spouští tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="2a76e-195">In that case, the `gcroot` shows you the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="2a76e-196">Obtížné případem je po kořen statická proměnná nebo popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="2a76e-196">The difficult case is when the root is a static variable or a GC handle.</span></span> 

<span data-ttu-id="2a76e-197">V předchozím příkladu první kořenový adresář je lokální proměnná typu `System.Reflection.RuntimeMethodInfo` uložené v rámci funkce `example.Program.Main(System.String[])` na adrese `rbp-20` (`rbp` je registru procesoru `rbp` a je hexadecimální posun z registru -20).</span><span class="sxs-lookup"><span data-stu-id="2a76e-197">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="2a76e-198">Druhý kořenový adresář je normální (silnou) `GCHandle` , který obsahuje odkaz na instanci `test.Test` třídy.</span><span class="sxs-lookup"><span data-stu-id="2a76e-198">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span> 

<span data-ttu-id="2a76e-199">Třetí kořenový adresář je připnutého `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="2a76e-199">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="2a76e-200">Tato funkce je ve skutečnosti statické proměnné.</span><span class="sxs-lookup"><span data-stu-id="2a76e-200">This one is actually a static variable.</span></span> <span data-ttu-id="2a76e-201">Bohužel neexistuje žádný způsob, jak říct.</span><span class="sxs-lookup"><span data-stu-id="2a76e-201">Unfortunately, there is no way to tell.</span></span> <span data-ttu-id="2a76e-202">Statické objekty pro typy odkazů jsou uloženy v poli spravovaných objektů ve strukturách vnitřního modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2a76e-202">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="2a76e-203">Dalším užitečným, která může zabránit uvolnění `AssemblyLoadContext` Pokud vlákno obsahuje blok metody z sestavení nahrán `AssemblyLoadContext` na svůj zásobník.</span><span class="sxs-lookup"><span data-stu-id="2a76e-203">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="2a76e-204">Můžete zkontrolovat, že podle vypsání spravované zásobníky volání všech vláken:</span><span class="sxs-lookup"><span data-stu-id="2a76e-204">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="2a76e-205">Příkaz znamená "platí pro všechna vlákna `!clrstack` příkaz".</span><span class="sxs-lookup"><span data-stu-id="2a76e-205">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="2a76e-206">Následuje výstupu tohoto příkazu pro příklad.</span><span class="sxs-lookup"><span data-stu-id="2a76e-206">The following is the output of that command for the example.</span></span> <span data-ttu-id="2a76e-207">Bohužel LLDB v systému Unix nemá žádný způsob, jak použít příkaz na všechna vlákna, takže budete muset ručně přepínání vlákna a opakující se uchýlíte `clrstack` příkazu.</span><span class="sxs-lookup"><span data-stu-id="2a76e-207">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you'll need to resort to manually switching threads and repeating the `clrstack` command.</span></span>
<span data-ttu-id="2a76e-208">Ignorovat všechna vlákna, kde ladicí program říká "Nelze procházet spravované zásobníku."</span><span class="sxs-lookup"><span data-stu-id="2a76e-208">Ignore all threads where the debugger says "Unable to walk the managed stack."</span></span>

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

<span data-ttu-id="2a76e-209">Jak je vidět, poslední vlákno má `test.Program.ThreadProc()`.</span><span class="sxs-lookup"><span data-stu-id="2a76e-209">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="2a76e-210">Toto je funkce ze sestavení načtena do `AssemblyLoadContext`, a proto se uchová `AssemblyLoadContext` zachování připojení.</span><span class="sxs-lookup"><span data-stu-id="2a76e-210">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="2a76e-211">Příklad zdroje s unloadability problémy</span><span class="sxs-lookup"><span data-stu-id="2a76e-211">Example source with unloadability issues</span></span>

<span data-ttu-id="2a76e-212">Následující kód se používá v předchozím příkladu ladění.</span><span class="sxs-lookup"><span data-stu-id="2a76e-212">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="2a76e-213">Hlavní testování aplikace</span><span class="sxs-lookup"><span data-stu-id="2a76e-213">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="2a76e-214">Program nahrán TestAssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="2a76e-214">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="2a76e-215">Následující kód představuje `test.dll` předán `ExecuteAndUnload` metoda v hlavní aplikaci testování.</span><span class="sxs-lookup"><span data-stu-id="2a76e-215">The following code represents the `test.dll` passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
