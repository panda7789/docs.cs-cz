---
title: Migrace aplikace pro Windows Store do .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac21e8aa67eabcb3e837cb5eca02d1145b765946
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941735"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="f19e7-102">Migrace aplikace pro Windows Store do .NET Native</span><span class="sxs-lookup"><span data-stu-id="f19e7-102">Migrating Your Windows Store App to .NET Native</span></span>

<span data-ttu-id="f19e7-103">.NET Native poskytuje statickou kompilaci aplikací ve Windows Storu nebo v počítači vývojáře.</span><span class="sxs-lookup"><span data-stu-id="f19e7-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="f19e7-104">To se liší od dynamické kompilace provedené pro aplikace pro Windows Store pomocí kompilátoru JIT (just-in-time) nebo generátoru [nativních imagí (Ngen. exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) na zařízení.</span><span class="sxs-lookup"><span data-stu-id="f19e7-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="f19e7-105">Navzdory rozdílům se .NET Native snaží udržet kompatibilitu s [rozhraním .NET pro aplikace pro Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span><span class="sxs-lookup"><span data-stu-id="f19e7-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span></span> <span data-ttu-id="f19e7-106">Ve většině případů fungují i v případě, že funkce pro .NET pro aplikace pro Windows Store funguje i .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="f19e7-107">V některých případech ale může dojít ke změnám chování.</span><span class="sxs-lookup"><span data-stu-id="f19e7-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="f19e7-108">Tento dokument popisuje tyto rozdíly mezi standardním rozhraním .NET pro aplikace pro Windows Store a .NET Native v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="f19e7-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>

- [<span data-ttu-id="f19e7-109">Obecné rozdíly v modulech runtime</span><span class="sxs-lookup"><span data-stu-id="f19e7-109">General runtime differences</span></span>](#Runtime)

- [<span data-ttu-id="f19e7-110">Rozdíly v dynamickém programování</span><span class="sxs-lookup"><span data-stu-id="f19e7-110">Dynamic programming differences</span></span>](#Dynamic)

- [<span data-ttu-id="f19e7-111">Další rozdíly týkající se reflexe</span><span class="sxs-lookup"><span data-stu-id="f19e7-111">Other reflection-related differences</span></span>](#Reflection)

- [<span data-ttu-id="f19e7-112">Nepodporované scénáře a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f19e7-112">Unsupported scenarios and APIs</span></span>](#Unsupported)

- [<span data-ttu-id="f19e7-113">Rozdíly v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f19e7-113">Visual Studio differences</span></span>](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a><span data-ttu-id="f19e7-114">Obecné rozdíly v modulech runtime</span><span class="sxs-lookup"><span data-stu-id="f19e7-114">General runtime differences</span></span>

- <span data-ttu-id="f19e7-115">Výjimky, například <xref:System.TypeLoadException>, které jsou vyvolány kompilátorem JIT v případě, že aplikace běží v modulu CLR (Common Language Runtime) obecně vede k chybám při kompilaci při zpracování pomocí .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>

- <span data-ttu-id="f19e7-116">Nevolejte <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metodu z vlákna uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="f19e7-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="f19e7-117">To může vést k zablokování .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-117">This can result in a deadlock on .NET Native.</span></span>

- <span data-ttu-id="f19e7-118">Nespoléhá se na řazení volání konstruktoru statické třídy.</span><span class="sxs-lookup"><span data-stu-id="f19e7-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="f19e7-119">V .NET Native se pořadí vyvolání liší od pořadí na standardním modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f19e7-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="f19e7-120">(I se standardním modulem runtime byste neměli spoléhat na pořadí spouštění statických konstruktorů tříd.)</span><span class="sxs-lookup"><span data-stu-id="f19e7-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>

- <span data-ttu-id="f19e7-121">Nekonečná smyčka bez provedení volání (například `while(true);`) v jakémkoli vlákně může aplikaci přenést do zastavení.</span><span class="sxs-lookup"><span data-stu-id="f19e7-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="f19e7-122">Podobně, velké nebo nekonečné čekací prodlevy můžou aplikaci zastavit.</span><span class="sxs-lookup"><span data-stu-id="f19e7-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>

- <span data-ttu-id="f19e7-123">Některé obecné inicializační cykly nevyvolají výjimky v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="f19e7-124">Například následující kód vyvolá <xref:System.TypeLoadException> výjimku pro standardní CLR.</span><span class="sxs-lookup"><span data-stu-id="f19e7-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="f19e7-125">V .NET Native ne.</span><span class="sxs-lookup"><span data-stu-id="f19e7-125">In .NET Native, it doesn't.</span></span>

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- <span data-ttu-id="f19e7-126">V některých případech .NET Native poskytuje různé implementace knihoven .NET Framework třídy.</span><span class="sxs-lookup"><span data-stu-id="f19e7-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="f19e7-127">Objekt vrácený z metody vždy implementuje členy vráceného typu.</span><span class="sxs-lookup"><span data-stu-id="f19e7-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="f19e7-128">Vzhledem k tomu, že je jeho implementace jiného typu odlišná, možná ho nebude možné přetypovat na stejnou sadu typů, jakou jste mohli na jiných .NET Framework platformách.</span><span class="sxs-lookup"><span data-stu-id="f19e7-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="f19e7-129">Například v některých případech nemusí <xref:System.Collections.Generic.IEnumerable%601> být možné přetypování objektu rozhraní vráceného metodami, jako je <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> na `T[]`.</span><span class="sxs-lookup"><span data-stu-id="f19e7-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>

- <span data-ttu-id="f19e7-130">Mezipaměť WinInet není ve výchozím nastavení povolená v rozhraní .NET pro aplikace pro Windows Store, ale je na .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="f19e7-131">To zlepšuje výkon, ale má vliv na pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="f19e7-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="f19e7-132">Není nutná žádná akce vývojáře.</span><span class="sxs-lookup"><span data-stu-id="f19e7-132">No developer action is necessary.</span></span>

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a><span data-ttu-id="f19e7-133">Rozdíly v dynamickém programování</span><span class="sxs-lookup"><span data-stu-id="f19e7-133">Dynamic programming differences</span></span>

<span data-ttu-id="f19e7-134">.NET Native staticky propojuje v kódu z .NET Framework pro zajištění maximálního výkonu pro místní aplikaci kódu.</span><span class="sxs-lookup"><span data-stu-id="f19e7-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="f19e7-135">Binární velikosti ale musí zůstat malé, takže celé .NET Framework nejde do.</span><span class="sxs-lookup"><span data-stu-id="f19e7-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="f19e7-136">Kompilátor .NET Native vyřeší toto omezení pomocí zmenšení závislosti, který odebírá odkazy na nepoužitý kód.</span><span class="sxs-lookup"><span data-stu-id="f19e7-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="f19e7-137">.NET Native však nemusí zachovat nebo vygenerovat některé informace o typu a kód, pokud tyto informace nelze odvodit staticky v době kompilace, ale místo toho se načte dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="f19e7-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>

<span data-ttu-id="f19e7-138">.NET Native povolí reflexi a dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="f19e7-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="f19e7-139">Ne všechny typy však mohou být označeny pro reflexi, protože by byla velikost generovaného kódu příliš velká (obzvláště proto, že je podporována podpora veřejných rozhraní API v .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="f19e7-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="f19e7-140">Kompilátor .NET Native zpřístupňuje inteligentní volby, které typy by měly podporovat reflexi, a udržuje metadata a generuje kód pouze pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="f19e7-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>

<span data-ttu-id="f19e7-141">Datová vazba například vyžaduje, aby aplikace mohla mapovat názvy vlastností na funkce.</span><span class="sxs-lookup"><span data-stu-id="f19e7-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="f19e7-142">V rozhraní .NET pro aplikace pro Windows Store modul CLR (Common Language Runtime) automaticky používá reflexi k poskytnutí této možnosti pro spravované typy a veřejně dostupné nativní typy.</span><span class="sxs-lookup"><span data-stu-id="f19e7-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="f19e7-143">V .NET Native kompilátor automaticky obsahuje metadata pro typy, na které svážete data.</span><span class="sxs-lookup"><span data-stu-id="f19e7-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>

<span data-ttu-id="f19e7-144">Kompilátor .NET Native může také zpracovat běžně používané obecné typy, jako jsou <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602>, které fungují bez vyžadování jakýchkoli pomocných parametrů nebo direktiv.</span><span class="sxs-lookup"><span data-stu-id="f19e7-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="f19e7-145">[Dynamické](../../csharp/language-reference/keywords/dynamic.md) klíčové slovo je podporováno i v určitých omezeních.</span><span class="sxs-lookup"><span data-stu-id="f19e7-145">The [dynamic](../../csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>

> [!NOTE]
> <span data-ttu-id="f19e7-146">Všechny cesty dynamického kódu by měly být důkladně testovány při přenosu vaší aplikace do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>

<span data-ttu-id="f19e7-147">Výchozí konfigurace pro .NET Native je dostačující pro většinu vývojářů, ale vývojáři můžou chtít doladit své konfigurace pomocí souboru běhových direktiv (. Rd. XML).</span><span class="sxs-lookup"><span data-stu-id="f19e7-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="f19e7-148">Navíc v některých případech kompilátor .NET Native nemůže určit, která metadata musí být k dispozici pro reflexi a spoléhá na pomocná doporučení, zejména v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="f19e7-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>

- <span data-ttu-id="f19e7-149">Některé konstrukce jako <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> a <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> nelze určit staticky.</span><span class="sxs-lookup"><span data-stu-id="f19e7-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>

- <span data-ttu-id="f19e7-150">Vzhledem k tomu, že kompilátor nemůže určit vytváření instancí, musí obecný typ, na kterém chcete reflektovat, být určen direktivami modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f19e7-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="f19e7-151">To není pouhá, protože musí být zahrnut všechen kód, ale vzhledem k tomu, že reflexe na obecných typech může tvořit nekonečný cyklus (například při vyvolání obecné metody na obecném typu).</span><span class="sxs-lookup"><span data-stu-id="f19e7-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>

> [!NOTE]
> <span data-ttu-id="f19e7-152">Direktivy modulu runtime jsou definovány v souboru direktiv modulu runtime (. Rd. XML).</span><span class="sxs-lookup"><span data-stu-id="f19e7-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="f19e7-153">Obecné informace o používání tohoto souboru najdete v tématu [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="f19e7-153">For general information about using this file, see [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span> <span data-ttu-id="f19e7-154">Informace o direktivách modulu runtime naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="f19e7-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>

<span data-ttu-id="f19e7-155">.NET Native také obsahuje nástroje pro profilaci, které vývojářům pomůžou určit, které typy mimo výchozí sadu mají podporovat reflexi.</span><span class="sxs-lookup"><span data-stu-id="f19e7-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a><span data-ttu-id="f19e7-156">Další rozdíly týkající se reflexe</span><span class="sxs-lookup"><span data-stu-id="f19e7-156">Other reflection-related differences</span></span>

<span data-ttu-id="f19e7-157">Mezi rozhraním .NET pro aplikace pro Windows Store a .NET Native existuje řada dalších rozdílů týkajících se reflexe.</span><span class="sxs-lookup"><span data-stu-id="f19e7-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>

<span data-ttu-id="f19e7-158">V .NET Native:</span><span class="sxs-lookup"><span data-stu-id="f19e7-158">In .NET Native:</span></span>

- <span data-ttu-id="f19e7-159">Privátní odraz nad typy a členy v knihovně tříd .NET Framework není podporován.</span><span class="sxs-lookup"><span data-stu-id="f19e7-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="f19e7-160">Můžete však reflektovat na vlastní privátní typy a členy a také typy a členy v knihovnách třetích stran.</span><span class="sxs-lookup"><span data-stu-id="f19e7-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>

- <span data-ttu-id="f19e7-161">Vlastnost správně `false` vrátí<xref:System.Reflection.ParameterInfo> objekt, který představuje vrácenou hodnotu. <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f19e7-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="f19e7-162">V rozhraní .NET pro aplikace pro Windows Store se vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="f19e7-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="f19e7-163">Intermediate Language (IL) nepodporuje tento přímý odkaz a interpretace je ponechána na jazyku.</span><span class="sxs-lookup"><span data-stu-id="f19e7-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>

- <span data-ttu-id="f19e7-164">Veřejné členy ve <xref:System.RuntimeFieldHandle> strukturách <xref:System.RuntimeMethodHandle> a nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="f19e7-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="f19e7-165">Tyto typy jsou podporovány pouze pro LINQ, stromy výrazů a inicializaci statického pole.</span><span class="sxs-lookup"><span data-stu-id="f19e7-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>

- <span data-ttu-id="f19e7-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType>a <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> zahrnují skryté členy v základních třídách, a proto mohou být přepsány bez explicitního přepsání.</span><span class="sxs-lookup"><span data-stu-id="f19e7-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="f19e7-167">To platí také pro jiné metody [RuntimeReflectionExtensions. GetRuntime \*](xref:System.Reflection.RuntimeReflectionExtensions) .</span><span class="sxs-lookup"><span data-stu-id="f19e7-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>

- <span data-ttu-id="f19e7-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>a <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> při pokusu o vytvoření určitých kombinací neproběhne chyba (například pole s parametry ByRef).</span><span class="sxs-lookup"><span data-stu-id="f19e7-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>

- <span data-ttu-id="f19e7-169">Nemůžete použít reflexi k vyvolání členů, kteří mají parametry ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f19e7-169">You can't use reflection to invoke members that have pointer parameters.</span></span>

- <span data-ttu-id="f19e7-170">Nemůžete použít reflexi k získání nebo nastavení pole ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f19e7-170">You can't use reflection to get or set a pointer field.</span></span>

- <span data-ttu-id="f19e7-171">Pokud je počet argumentů špatný a typ jednoho z argumentů je nesprávný, .NET Native vyvolá <xref:System.ArgumentException> namísto. <xref:System.Reflection.TargetParameterCountException></span><span class="sxs-lookup"><span data-stu-id="f19e7-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>

- <span data-ttu-id="f19e7-172">Binární serializace výjimek je obecně Nepodporovaná.</span><span class="sxs-lookup"><span data-stu-id="f19e7-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="f19e7-173">V důsledku toho lze do <xref:System.Exception.Data%2A?displayProperty=nameWithType> slovníku přidat objekty, které nejsou serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="f19e7-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="f19e7-174">Nepodporované scénáře a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f19e7-174">Unsupported scenarios and APIs</span></span>

<span data-ttu-id="f19e7-175">V následujících částech najdete seznam nepodporovaných scénářů a rozhraní API pro obecné vývoj, interoperabilitu a technologie, jako je HTTPClient a Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="f19e7-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>

- [<span data-ttu-id="f19e7-176">Obecný vývoj</span><span class="sxs-lookup"><span data-stu-id="f19e7-176">General development</span></span>](#General)

- [<span data-ttu-id="f19e7-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="f19e7-177">HttpClient</span></span>](#HttpClient)

- [<span data-ttu-id="f19e7-178">Interop</span><span class="sxs-lookup"><span data-stu-id="f19e7-178">Interop</span></span>](#Interop)

- [<span data-ttu-id="f19e7-179">Nepodporovaná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f19e7-179">Unsupported APIs</span></span>](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a><span data-ttu-id="f19e7-180">Obecné rozdíly v vývoji</span><span class="sxs-lookup"><span data-stu-id="f19e7-180">General development differences</span></span>

<span data-ttu-id="f19e7-181">**Typy hodnot**</span><span class="sxs-lookup"><span data-stu-id="f19e7-181">**Value types**</span></span>

- <span data-ttu-id="f19e7-182">Pokud přepíšete <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metody <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> a pro typ hodnoty, Nevolejte implementace základní třídy.</span><span class="sxs-lookup"><span data-stu-id="f19e7-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="f19e7-183">V rozhraní .NET pro aplikace pro Windows Store se tyto metody spoléhají na reflexi.</span><span class="sxs-lookup"><span data-stu-id="f19e7-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="f19e7-184">V době kompilace .NET Native generuje implementaci, která nespoléhá na reflexi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f19e7-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="f19e7-185">To znamená, že pokud tyto dvě metody nepřepíšete, budou fungovat podle očekávání, protože .NET Native generuje implementaci v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="f19e7-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="f19e7-186">Nicméně přepsání těchto metod, ale volání implementace základní třídy, způsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="f19e7-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>

- <span data-ttu-id="f19e7-187">Typy hodnot větší než 1 MB nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="f19e7-187">Value types larger than one megabyte aren't supported.</span></span>

- <span data-ttu-id="f19e7-188">Typy hodnot nemohou mít konstruktor bez parametrů v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-188">Value types can't have a parameterless constructor in .NET Native.</span></span> <span data-ttu-id="f19e7-189">(C# a Visual Basic zakázat konstruktory bez parametrů u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="f19e7-189">(C# and Visual Basic prohibit parameterless constructors on value types.</span></span> <span data-ttu-id="f19e7-190">Ty však lze vytvořit v IL.)</span><span class="sxs-lookup"><span data-stu-id="f19e7-190">However, these can be created in IL.)</span></span>

<span data-ttu-id="f19e7-191">**Pole**</span><span class="sxs-lookup"><span data-stu-id="f19e7-191">**Arrays**</span></span>

- <span data-ttu-id="f19e7-192">Pole s dolní mezí jinou než nula se nepodporují.</span><span class="sxs-lookup"><span data-stu-id="f19e7-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="f19e7-193">Obvykle jsou tato pole vytvořena voláním <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> přetížení.</span><span class="sxs-lookup"><span data-stu-id="f19e7-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

- <span data-ttu-id="f19e7-194">Dynamické vytváření multidimenzionálních polí se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="f19e7-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="f19e7-195">Taková pole jsou obvykle vytvořena voláním přetížení <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody, která `lengths` obsahuje parametr <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> , nebo voláním metody.</span><span class="sxs-lookup"><span data-stu-id="f19e7-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="f19e7-196">Multidimenzionální pole se čtyřmi nebo více dimenzemi nejsou podporována. To znamená, že <xref:System.Array.Rank%2A?displayProperty=nameWithType> jejich hodnota vlastnosti je čtyři nebo větší.</span><span class="sxs-lookup"><span data-stu-id="f19e7-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="f19e7-197">Místo toho použijte [vícenásobná pole](../../csharp/programming-guide/arrays/jagged-arrays.md) (pole polí).</span><span class="sxs-lookup"><span data-stu-id="f19e7-197">Use [jagged arrays](../../csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="f19e7-198">Například `array[x,y,z]` je neplatný, ale `array[x][y][z]` není.</span><span class="sxs-lookup"><span data-stu-id="f19e7-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>

- <span data-ttu-id="f19e7-199">Variance pro multidimenzionální pole není podporována a v době <xref:System.InvalidCastException> běhu způsobuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="f19e7-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>

<span data-ttu-id="f19e7-200">**Obecné typy**</span><span class="sxs-lookup"><span data-stu-id="f19e7-200">**Generics**</span></span>

- <span data-ttu-id="f19e7-201">Nekonečné rozšíření obecného typu má za následek chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f19e7-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="f19e7-202">Například tento kód nemůže kompilovat:</span><span class="sxs-lookup"><span data-stu-id="f19e7-202">For example, this code fails to compile:</span></span>

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

<span data-ttu-id="f19e7-203">**Ukazatele**</span><span class="sxs-lookup"><span data-stu-id="f19e7-203">**Pointers**</span></span>

- <span data-ttu-id="f19e7-204">Pole ukazatelů nejsou podporovaná.</span><span class="sxs-lookup"><span data-stu-id="f19e7-204">Arrays of pointers aren't supported.</span></span>

- <span data-ttu-id="f19e7-205">Nemůžete použít reflexi k získání nebo nastavení pole ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f19e7-205">You can't use reflection to get or set a pointer field.</span></span>

<span data-ttu-id="f19e7-206">**Serializace**</span><span class="sxs-lookup"><span data-stu-id="f19e7-206">**Serialization**</span></span>

<span data-ttu-id="f19e7-207"><xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Atribut není podporován.</span><span class="sxs-lookup"><span data-stu-id="f19e7-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="f19e7-208">Místo toho použijte atribut. <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29></span><span class="sxs-lookup"><span data-stu-id="f19e7-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>

<span data-ttu-id="f19e7-209">**Prostředky**</span><span class="sxs-lookup"><span data-stu-id="f19e7-209">**Resources**</span></span>

<span data-ttu-id="f19e7-210">Použití lokalizovaných prostředků s <xref:System.Diagnostics.Tracing.EventSource> třídou není podporováno.</span><span class="sxs-lookup"><span data-stu-id="f19e7-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="f19e7-211"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Vlastnost nedefinuje lokalizované prostředky.</span><span class="sxs-lookup"><span data-stu-id="f19e7-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>

<span data-ttu-id="f19e7-212">**Delegáti**</span><span class="sxs-lookup"><span data-stu-id="f19e7-212">**Delegates**</span></span>

<span data-ttu-id="f19e7-213">`Delegate.BeginInvoke`a `Delegate.EndInvoke` nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="f19e7-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>

<span data-ttu-id="f19e7-214">**Ostatní rozhraní API**</span><span class="sxs-lookup"><span data-stu-id="f19e7-214">**Miscellaneous APIs**</span></span>

- <span data-ttu-id="f19e7-215">Vlastnost [TypeInfo. GUID](xref:System.Type.GUID) vyvolá <xref:System.PlatformNotSupportedException> výjimku, pokud <xref:System.Runtime.InteropServices.GuidAttribute> atribut není použit pro typ.</span><span class="sxs-lookup"><span data-stu-id="f19e7-215">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="f19e7-216">Identifikátor GUID se používá hlavně pro podporu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="f19e7-216">The GUID is used primarily for COM support.</span></span>

- <span data-ttu-id="f19e7-217"><xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Metoda správně analyzuje řetězce, které obsahují krátká data v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="f19e7-218">Neudržuje však kompatibilitu se změnami v části datum a čas analýzy popsané v článcích [KB2803771](https://support.microsoft.com/kb/2803771) a [KB2803755](https://support.microsoft.com/kb/2803755)znalostní báze Microsoft Knowledge Base.</span><span class="sxs-lookup"><span data-stu-id="f19e7-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>

- <span data-ttu-id="f19e7-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")` je správně zaokrouhlena v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="f19e7-220">V některých verzích modulu CLR je výsledný řetězec zkrácen namísto zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="f19e7-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a><span data-ttu-id="f19e7-221">HttpClient rozdíly</span><span class="sxs-lookup"><span data-stu-id="f19e7-221">HttpClient differences</span></span>

<span data-ttu-id="f19e7-222">V .NET Native <xref:System.Net.Http.HttpClientHandler> třída interně používá rozhraní WinInet ( <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> přes <xref:System.Net.WebRequest> třídu) namísto tříd a <xref:System.Net.WebResponse> používaných ve standardním rozhraní .NET pro aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="f19e7-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="f19e7-223">Rozhraní WinINet nepodporuje všechny možnosti konfigurace, které <xref:System.Net.Http.HttpClientHandler> třída podporuje.</span><span class="sxs-lookup"><span data-stu-id="f19e7-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="f19e7-224">Výsledek:</span><span class="sxs-lookup"><span data-stu-id="f19e7-224">As a result:</span></span>

- <span data-ttu-id="f19e7-225">Některé vlastnosti schopností při <xref:System.Net.Http.HttpClientHandler> návratu `false` na .NET Native, zatímco se vrátí `true` do standardního rozhraní .NET pro aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="f19e7-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>

- <span data-ttu-id="f19e7-226">Některé z přidaných `get` objektů konfiguračních vlastností vždycky vrací pevnou hodnotu pro .NET Native, která se liší od výchozí konfigurovatelné hodnoty v rozhraní .NET pro aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="f19e7-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>

<span data-ttu-id="f19e7-227">V následujících pododdílech jsou uvedeny některé další rozdíly v chování.</span><span class="sxs-lookup"><span data-stu-id="f19e7-227">Some additional behavior differences are covered in the following subsections.</span></span>

<span data-ttu-id="f19e7-228">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="f19e7-228">**Proxy**</span></span>

<span data-ttu-id="f19e7-229"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Třída nepodporuje konfiguraci ani přepsání proxy serveru na základě jednotlivých požadavků.</span><span class="sxs-lookup"><span data-stu-id="f19e7-229">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="f19e7-230">To znamená, že všechny požadavky na .NET Native v závislosti na hodnotě <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> vlastnosti používají systém proxy server nebo žádné proxy server.</span><span class="sxs-lookup"><span data-stu-id="f19e7-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="f19e7-231">V rozhraní .NET pro aplikace pro Windows Store je proxy server definováno <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> vlastností.</span><span class="sxs-lookup"><span data-stu-id="f19e7-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="f19e7-232">V .NET Native nastavení <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> na jinou hodnotu než `null` vyvolá <xref:System.PlatformNotSupportedException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="f19e7-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="f19e7-233">Vlastnost vrací `false` .NET Native, zatímco se vrátí `true` ve standardním .NET Framework aplikací pro Windows Store. <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f19e7-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>

<span data-ttu-id="f19e7-234">**Automatické přesměrování**</span><span class="sxs-lookup"><span data-stu-id="f19e7-234">**Automatic redirection**</span></span>

<span data-ttu-id="f19e7-235"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Třída neumožňuje nakonfigurovat maximální počet automatických přesměrování.</span><span class="sxs-lookup"><span data-stu-id="f19e7-235">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="f19e7-236">Hodnota <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> vlastnosti je ve výchozím nastavení standardu .NET pro aplikace pro Windows Store 50 a je možné ji upravit.</span><span class="sxs-lookup"><span data-stu-id="f19e7-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="f19e7-237">V .NET Native je hodnota této vlastnosti 10 a pokus o její úpravu vyvolá <xref:System.PlatformNotSupportedException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="f19e7-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="f19e7-238">Vlastnost vrátí `false` na .NET Native, zatímco vrátí `true` v rozhraní .NET pro aplikace pro Windows Store. <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f19e7-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>

<span data-ttu-id="f19e7-239">**Automatická dekomprese**</span><span class="sxs-lookup"><span data-stu-id="f19e7-239">**Automatic decompression**</span></span>

<span data-ttu-id="f19e7-240">Rozhraní .NET pro aplikace pro <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> Windows Store umožňuje nastavit vlastnost na <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, <xref:System.Net.DecompressionMethods.Deflate> a <xref:System.Net.DecompressionMethods.GZip>, nebo <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="f19e7-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="f19e7-241">.NET Native podporuje <xref:System.Net.DecompressionMethods.Deflate> pouze společně s <xref:System.Net.DecompressionMethods.GZip>, nebo <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="f19e7-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="f19e7-242">Pokus o nastavení vlastnosti <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> buď <xref:System.Net.DecompressionMethods.Deflate> nebo <xref:System.Net.DecompressionMethods.GZip> samostatně, v tichém režimu nastaví na <xref:System.Net.DecompressionMethods.Deflate> hodnotu a <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="f19e7-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>

<span data-ttu-id="f19e7-243">**Soubory cookie**</span><span class="sxs-lookup"><span data-stu-id="f19e7-243">**Cookies**</span></span>

<span data-ttu-id="f19e7-244">Zpracování souborů cookie se provádí současně <xref:System.Net.Http.HttpClient> pomocí a WinInet.</span><span class="sxs-lookup"><span data-stu-id="f19e7-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="f19e7-245">Soubory cookie z <xref:System.Net.CookieContainer> jsou kombinovány s soubory cookie v mezipaměti WinInet cookie.</span><span class="sxs-lookup"><span data-stu-id="f19e7-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="f19e7-246">Odebrání souboru cookie z <xref:System.Net.CookieContainer> nebrání <xref:System.Net.Http.HttpClient> odeslání souboru cookie, ale pokud soubor cookie již viděla služba WinInet a soubory cookie nebyly odstraněny uživatelem, rozhraní WinInet ho pošle.</span><span class="sxs-lookup"><span data-stu-id="f19e7-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="f19e7-247">Nelze programově odebrat soubor cookie z rozhraní WinInet pomocí <xref:System.Net.Http.HttpClient>rozhraní API, <xref:System.Net.Http.HttpClientHandler>nebo <xref:System.Net.CookieContainer> .</span><span class="sxs-lookup"><span data-stu-id="f19e7-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="f19e7-248">Nastavení vlastnosti na `false` příčiny pouze <xref:System.Net.Http.HttpClient> pro zastavení odesílání souborů cookie; <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> Rozhraní WinINet může stále zahrnovat své soubory cookie v žádosti.</span><span class="sxs-lookup"><span data-stu-id="f19e7-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>

<span data-ttu-id="f19e7-249">**Přihlašovací údaje**</span><span class="sxs-lookup"><span data-stu-id="f19e7-249">**Credentials**</span></span>

<span data-ttu-id="f19e7-250">V rozhraní .NET pro aplikace <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> pro Windows Store fungují vlastnosti a <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> samostatně.</span><span class="sxs-lookup"><span data-stu-id="f19e7-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="f19e7-251">Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost přijímá libovolný objekt, který <xref:System.Net.ICredentials> implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f19e7-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="f19e7-252">V .NET Native nastavením <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> vlastnosti na `true` hodnotu způsobí, že <xref:System.Net.Http.HttpClientHandler.Credentials%2A> se vlastnost stane `null`.</span><span class="sxs-lookup"><span data-stu-id="f19e7-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="f19e7-253">Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> může být vlastnost nastavena pouze na `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>nebo objekt typu <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="f19e7-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="f19e7-254">Přiřazení libovolného <xref:System.Net.ICredentials> objektu, který je nejoblíbenější z, to znamená <xref:System.Net.CredentialCache>, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost vyvolá <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="f19e7-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="f19e7-255">**Jiné nepodporované nebo Nekonfigurovatelné funkce**</span><span class="sxs-lookup"><span data-stu-id="f19e7-255">**Other unsupported or unconfigurable features**</span></span>

<span data-ttu-id="f19e7-256">V .NET Native:</span><span class="sxs-lookup"><span data-stu-id="f19e7-256">In .NET Native:</span></span>

- <span data-ttu-id="f19e7-257">Hodnota <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> vlastnosti je vždy <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="f19e7-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="f19e7-258">V rozhraní .NET pro aplikace pro Windows Store je <xref:System.Net.Http.ClientCertificateOption.Manual>výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="f19e7-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>

- <span data-ttu-id="f19e7-259"><xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Vlastnost není konfigurovatelná.</span><span class="sxs-lookup"><span data-stu-id="f19e7-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>

- <span data-ttu-id="f19e7-260">Vlastnost je vždy `true`. <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f19e7-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="f19e7-261">V rozhraní .NET pro aplikace pro Windows Store je `false`výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="f19e7-261">In .NET for Windows Store apps, the default is `false`.</span></span>

- <span data-ttu-id="f19e7-262">`SetCookie2` Hlavička v odpovědích je ignorována jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f19e7-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>

<a name="Interop"></a>
### <a name="interop-differences"></a><span data-ttu-id="f19e7-263">Rozdíly v interoperabilitách</span><span class="sxs-lookup"><span data-stu-id="f19e7-263">Interop differences</span></span>
 <span data-ttu-id="f19e7-264">**Zastaralá rozhraní API**</span><span class="sxs-lookup"><span data-stu-id="f19e7-264">**Deprecated APIs**</span></span>

 <span data-ttu-id="f19e7-265">Počet zřídka používaných rozhraní API pro interoperabilitu se spravovaným kódem je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="f19e7-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="f19e7-266">Při použití s .NET Native může tato rozhraní API vyvolat <xref:System.NotImplementedException> výjimku nebo <xref:System.PlatformNotSupportedException> nebo způsobit chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f19e7-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="f19e7-267">V rozhraní .NET pro aplikace pro Windows Store jsou tato rozhraní API označena jako zastaralá, ale volání generují upozornění kompilátoru, nikoli chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f19e7-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>

 <span data-ttu-id="f19e7-268">Zastaralá rozhraní `VARIANT` API pro zařazování zahrnují:</span><span class="sxs-lookup"><span data-stu-id="f19e7-268">Deprecated APIs for `VARIANT` marshaling include:</span></span>

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <span data-ttu-id="f19e7-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>je podporováno, ale vyvolá výjimku v některých scénářích, například při použití s variantami [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) nebo ByRef.</span><span class="sxs-lookup"><span data-stu-id="f19e7-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or byref variants.</span></span>

 <span data-ttu-id="f19e7-270">Zastaralá rozhraní API pro podporu rozhraní [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) zahrnují:</span><span class="sxs-lookup"><span data-stu-id="f19e7-270">Deprecated APIs for [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

<span data-ttu-id="f19e7-271">Zastaralá rozhraní API pro události klasických objektů COM zahrnují:</span><span class="sxs-lookup"><span data-stu-id="f19e7-271">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<span data-ttu-id="f19e7-272">Zastaralá rozhraní API <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> v rozhraní, která nejsou ve .NET Native podporovaná, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="f19e7-272">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>

- <span data-ttu-id="f19e7-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="f19e7-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="f19e7-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="f19e7-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="f19e7-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="f19e7-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

<span data-ttu-id="f19e7-276">Mezi další nepodporované funkce spolupráce patří:</span><span class="sxs-lookup"><span data-stu-id="f19e7-276">Other unsupported interop features include:</span></span>

- <span data-ttu-id="f19e7-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="f19e7-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="f19e7-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="f19e7-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 <span data-ttu-id="f19e7-279">Zřídka používaná zařazování rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="f19e7-279">Rarely used marshaling APIs:</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 <span data-ttu-id="f19e7-280">**Volání platforem a kompatibilita zprostředkovatele komunikace s objekty COM**</span><span class="sxs-lookup"><span data-stu-id="f19e7-280">**Platform invoke and COM interop compatibility**</span></span>

 <span data-ttu-id="f19e7-281">Většina volání platforem a scénářů spolupráce s objekty COM jsou pořád podporované v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-281">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="f19e7-282">Konkrétně se podporuje veškerá interoperabilita s rozhraními API pro prostředí Windows Runtime (WinRT) a všechna zařazování požadovaná pro prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="f19e7-282">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="f19e7-283">Patří sem podpora zařazování pro:</span><span class="sxs-lookup"><span data-stu-id="f19e7-283">This includes marshaling support for:</span></span>

- <span data-ttu-id="f19e7-284">Pole (včetně <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="f19e7-284">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>

- `BStr`

- <span data-ttu-id="f19e7-285">Delegáty</span><span class="sxs-lookup"><span data-stu-id="f19e7-285">Delegates</span></span>

- <span data-ttu-id="f19e7-286">Řetězce (Unicode, ANSI a HSTRING)</span><span class="sxs-lookup"><span data-stu-id="f19e7-286">Strings (Unicode, Ansi, and HSTRING)</span></span>

- <span data-ttu-id="f19e7-287">Struktury (`byref` a `byval`)</span><span class="sxs-lookup"><span data-stu-id="f19e7-287">Structs (`byref` and `byval`)</span></span>

- <span data-ttu-id="f19e7-288">Sjednocení</span><span class="sxs-lookup"><span data-stu-id="f19e7-288">Unions</span></span>

- <span data-ttu-id="f19e7-289">Popisovače Win32</span><span class="sxs-lookup"><span data-stu-id="f19e7-289">Win32 handles</span></span>

- <span data-ttu-id="f19e7-290">Všechny konstruktory WinRT</span><span class="sxs-lookup"><span data-stu-id="f19e7-290">All WinRT constructs</span></span>

- <span data-ttu-id="f19e7-291">Částečná podpora pro zařazování typů variant</span><span class="sxs-lookup"><span data-stu-id="f19e7-291">Partial support for marshaling variant types.</span></span> <span data-ttu-id="f19e7-292">Podporovány jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f19e7-292">The following are supported:</span></span>

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [<span data-ttu-id="f19e7-293">IUnknown</span><span class="sxs-lookup"><span data-stu-id="f19e7-293">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

<span data-ttu-id="f19e7-294">.NET Native ale nepodporuje následující:</span><span class="sxs-lookup"><span data-stu-id="f19e7-294">However, .NET Native doesn't support the following:</span></span>

- <span data-ttu-id="f19e7-295">Používání klasických událostí COM</span><span class="sxs-lookup"><span data-stu-id="f19e7-295">Using classic COM events</span></span>

- <span data-ttu-id="f19e7-296"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> Implementace rozhraní na spravovaném typu</span><span class="sxs-lookup"><span data-stu-id="f19e7-296">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>

- <span data-ttu-id="f19e7-297">Implementace rozhraní [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) na spravovaném typu prostřednictvím <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> atributu.</span><span class="sxs-lookup"><span data-stu-id="f19e7-297">Implementing the [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="f19e7-298">Upozorňujeme však, že nelze volat objekty modelu COM pomocí `IDispatch`a váš spravovaný objekt nelze implementovat. `IDispatch`</span><span class="sxs-lookup"><span data-stu-id="f19e7-298">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>

<span data-ttu-id="f19e7-299">Použití reflexe k vyvolání metody Invoke platformy není podporováno.</span><span class="sxs-lookup"><span data-stu-id="f19e7-299">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="f19e7-300">Toto omezení můžete obejít tak, že zabalíte volání metody do jiné metody a pomocí reflexe namísto toho zavolejte obálku.</span><span class="sxs-lookup"><span data-stu-id="f19e7-300">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="f19e7-301">Další rozdíly od rozhraní API .NET pro aplikace pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="f19e7-301">Other differences from .NET APIs for Windows Store apps</span></span>

<span data-ttu-id="f19e7-302">Tato část obsahuje seznam zbývajících rozhraní API, která nejsou v .NET Native podporovaná.</span><span class="sxs-lookup"><span data-stu-id="f19e7-302">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="f19e7-303">Největší sadou nepodporovaných rozhraní API jsou Windows Communication Foundation (WCF) API.</span><span class="sxs-lookup"><span data-stu-id="f19e7-303">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>

<span data-ttu-id="f19e7-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="f19e7-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>

<span data-ttu-id="f19e7-305">Typy v <xref:System.ComponentModel.DataAnnotations> oborech názvů <xref:System.ComponentModel.DataAnnotations.Schema> a nejsou podporovány v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-305">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="f19e7-306">Mezi ně patří následující typy, které jsou k dispozici v rozhraní .NET pro aplikace pro Windows Store pro Windows 8:</span><span class="sxs-lookup"><span data-stu-id="f19e7-306">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 <span data-ttu-id="f19e7-307">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="f19e7-307">**Visual Basic**</span></span>

<span data-ttu-id="f19e7-308">Visual Basic se v .NET Native v tuto chvíli nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="f19e7-308">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="f19e7-309">Následující typy v <xref:Microsoft.VisualBasic> oborech názvů <xref:Microsoft.VisualBasic.CompilerServices> a nejsou k dispozici v .NET Native:</span><span class="sxs-lookup"><span data-stu-id="f19e7-309">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

<span data-ttu-id="f19e7-310">**Kontext reflexe (obor názvů System. Reflection. Context)**</span><span class="sxs-lookup"><span data-stu-id="f19e7-310">**Reflection Context (System.Reflection.Context namespace)**</span></span>

<span data-ttu-id="f19e7-311"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Třída není v .NET Native podporována.</span><span class="sxs-lookup"><span data-stu-id="f19e7-311">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>

<span data-ttu-id="f19e7-312">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="f19e7-312">**RTC (System.Net.Http.Rtc)**</span></span>

<span data-ttu-id="f19e7-313">`System.Net.Http.RtcRequestFactory` Třída není v .NET Native podporována.</span><span class="sxs-lookup"><span data-stu-id="f19e7-313">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>

<span data-ttu-id="f19e7-314">**Windows Communication Foundation (WCF) (System. ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="f19e7-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>

<span data-ttu-id="f19e7-315">Typy v oborech [názvů System. ServiceModel. \*](xref:System.ServiceModel) nejsou podporované v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f19e7-315">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="f19e7-316">Mezi ně patří následující typy:</span><span class="sxs-lookup"><span data-stu-id="f19e7-316">These includes the following types:</span></span>

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a><span data-ttu-id="f19e7-317">Rozdíly v serializátorech</span><span class="sxs-lookup"><span data-stu-id="f19e7-317">Differences in serializers</span></span>

<span data-ttu-id="f19e7-318">Následující rozdíly se týkají serializace a deserializace s <xref:System.Runtime.Serialization.DataContractSerializer>třídami, <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>a:</span><span class="sxs-lookup"><span data-stu-id="f19e7-318">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>

- <span data-ttu-id="f19e7-319">V .NET Native <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nepodařilo se serializovat nebo deserializovat odvozenou třídu, která má člena základní třídy, jehož typ není kořenovým typem serializace.</span><span class="sxs-lookup"><span data-stu-id="f19e7-319">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="f19e7-320">Například v následujícím kódu, pokus o serializaci nebo deserializaci `Y` má za následek chybu:</span><span class="sxs-lookup"><span data-stu-id="f19e7-320">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  <span data-ttu-id="f19e7-321">Typ `InnerType` není pro serializátor znám, protože členy základní třídy nejsou během serializace procházeny.</span><span class="sxs-lookup"><span data-stu-id="f19e7-321">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>

- <span data-ttu-id="f19e7-322"><xref:System.Runtime.Serialization.DataContractSerializer>a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serializaci třídy nebo struktury, která <xref:System.Collections.Generic.IEnumerable%601> implementuje rozhraní, se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="f19e7-322"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="f19e7-323">Například následující typy selhaly při serializaci nebo deserializaci:</span><span class="sxs-lookup"><span data-stu-id="f19e7-323">For example, the following types fail to serialize or deserialize:</span></span>

- <span data-ttu-id="f19e7-324"><xref:System.Xml.Serialization.XmlSerializer>serializace následující hodnoty objektu se nezdařila, protože neví přesný typ objektu, který má být serializován:</span><span class="sxs-lookup"><span data-stu-id="f19e7-324"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>

- <span data-ttu-id="f19e7-325"><xref:System.Xml.Serialization.XmlSerializer>serializaci nebo deserializaci, pokud je typ serializovaného objektu, <xref:System.Xml.XmlQualifiedName>se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="f19e7-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>

- <span data-ttu-id="f19e7-326">Všechny serializátory (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>a <xref:System.Xml.Serialization.XmlSerializer>) negenerují kód serializace pro typ <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> nebo pro typ, který obsahuje <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f19e7-326">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="f19e7-327">Místo toho zobrazují chyby při sestavování.</span><span class="sxs-lookup"><span data-stu-id="f19e7-327">They display build-time errors instead.</span></span>

- <span data-ttu-id="f19e7-328">Následující konstruktory typů serializace nemají zaručeny fungovat podle očekávání:</span><span class="sxs-lookup"><span data-stu-id="f19e7-328">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>

- <span data-ttu-id="f19e7-329"><xref:System.Xml.Serialization.XmlSerializer>Nepovedlo se vygenerovat kód pro typ, který má metody s atributem s některým z následujících atributů:</span><span class="sxs-lookup"><span data-stu-id="f19e7-329"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <span data-ttu-id="f19e7-330"><xref:System.Xml.Serialization.XmlSerializer>nedodržuje <xref:System.Xml.Serialization.IXmlSerializable> vlastní rozhraní serializace.</span><span class="sxs-lookup"><span data-stu-id="f19e7-330"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="f19e7-331">Pokud máte třídu, která implementuje toto rozhraní, <xref:System.Xml.Serialization.XmlSerializer> bere v úvahu typ jednoduchého starého objektu CLR (POCO) a provede serializaci pouze jeho veřejných vlastností.</span><span class="sxs-lookup"><span data-stu-id="f19e7-331">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>

- <span data-ttu-id="f19e7-332">Serializace prostého <xref:System.Exception> objektu nefunguje dobře s <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f19e7-332">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>

## <a name="visual-studio-differences"></a><span data-ttu-id="f19e7-333">Rozdíly v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f19e7-333">Visual Studio differences</span></span>

<span data-ttu-id="f19e7-334">**Výjimky a ladění**</span><span class="sxs-lookup"><span data-stu-id="f19e7-334">**Exceptions and debugging**</span></span>

<span data-ttu-id="f19e7-335">Pokud spouštíte aplikace zkompilované pomocí .NET Native v ladicím programu, jsou pro následující typy výjimek povoleny výjimky s první pravděpodobností:</span><span class="sxs-lookup"><span data-stu-id="f19e7-335">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

<span data-ttu-id="f19e7-336">**Sestavování aplikací**</span><span class="sxs-lookup"><span data-stu-id="f19e7-336">**Building apps**</span></span>

<span data-ttu-id="f19e7-337">Použijte nástroje pro sestavení x86, které jsou ve výchozím nastavení používány v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f19e7-337">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="f19e7-338">Nedoporučujeme používat nástroje AMD64 MSBuild, které se nacházejí v adresáři C:\Program Files (x86) \MSBuild\12.0\bin\amd64; Ty můžou vytvářet problémy s sestavením.</span><span class="sxs-lookup"><span data-stu-id="f19e7-338">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>

<span data-ttu-id="f19e7-339">**Profilery**</span><span class="sxs-lookup"><span data-stu-id="f19e7-339">**Profilers**</span></span>

- <span data-ttu-id="f19e7-340">Profiler procesoru sady Visual Studio a Profiler paměti XAML nezobrazuje správně pouze můj kód.</span><span class="sxs-lookup"><span data-stu-id="f19e7-340">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>

- <span data-ttu-id="f19e7-341">Profiler paměti XAML přesně nezobrazuje spravovaná data haldy.</span><span class="sxs-lookup"><span data-stu-id="f19e7-341">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>

- <span data-ttu-id="f19e7-342">Profiler procesoru správně neidentifikuje moduly a zobrazuje názvy předpevných funkcí.</span><span class="sxs-lookup"><span data-stu-id="f19e7-342">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>

<span data-ttu-id="f19e7-343">**Projekty knihovny testů jednotek**</span><span class="sxs-lookup"><span data-stu-id="f19e7-343">**Unit Test Library projects**</span></span>

<span data-ttu-id="f19e7-344">Povolení .NET Native v knihovně testů jednotek pro projekt aplikací pro Windows Store není podporované a způsobí, že se projekt nepodaří sestavit.</span><span class="sxs-lookup"><span data-stu-id="f19e7-344">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>

## <a name="see-also"></a><span data-ttu-id="f19e7-345">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f19e7-345">See also</span></span>

- [<span data-ttu-id="f19e7-346">Začínáme</span><span class="sxs-lookup"><span data-stu-id="f19e7-346">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="f19e7-347">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="f19e7-347">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="f19e7-348">Přehled aplikace .NET pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="f19e7-348">.NET For Windows Store apps overview</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [<span data-ttu-id="f19e7-349">Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f19e7-349">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
