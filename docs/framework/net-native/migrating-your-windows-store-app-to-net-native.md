---
title: Migrace aplikace pro Windows Store do .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a44819e8a8c0b07b3ffbfb2d92533cbdc558ef6
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874741"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="99cae-102">Migrace aplikace pro Windows Store do .NET Native</span><span class="sxs-lookup"><span data-stu-id="99cae-102">Migrating Your Windows Store App to .NET Native</span></span>
<span data-ttu-id="99cae-103">.NET native poskytuje statické kompilace aplikací ve Windows Store nebo v počítači vývojáře.</span><span class="sxs-lookup"><span data-stu-id="99cae-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="99cae-104">Tím se liší od dynamická kompilace provádí kompilátor just-in-time (JIT) pro aplikace Windows Store nebo [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) na zařízení.</span><span class="sxs-lookup"><span data-stu-id="99cae-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="99cae-105">Bez ohledu na rozdíly, .NET Native snaží udržovat kompatibilitu s [.NET pro Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span><span class="sxs-lookup"><span data-stu-id="99cae-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span></span> <span data-ttu-id="99cae-106">Ve většině případů věcí, které fungují v aplikacích .NET pro Windows Store také pracovat s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="99cae-107">Nicméně v některých případech může dojít k nějaké změny.</span><span class="sxs-lookup"><span data-stu-id="99cae-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="99cae-108">Tento dokument popisuje tyto rozdíly mezi standardní aplikace .NET pro Windows Store a .NET Native v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="99cae-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>  
  
-   [<span data-ttu-id="99cae-109">Obecné runtime rozdíly</span><span class="sxs-lookup"><span data-stu-id="99cae-109">General runtime differences</span></span>](#Runtime)  
  
-   [<span data-ttu-id="99cae-110">Dynamické programování rozdílů</span><span class="sxs-lookup"><span data-stu-id="99cae-110">Dynamic programming differences</span></span>](#Dynamic)  
  
-   [<span data-ttu-id="99cae-111">Další související reflexe rozdíly</span><span class="sxs-lookup"><span data-stu-id="99cae-111">Other reflection-related differences</span></span>](#Reflection)  
  
-   [<span data-ttu-id="99cae-112">Nepodporované scénáře a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="99cae-112">Unsupported scenarios and APIs</span></span>](#Unsupported)  
  
-   [<span data-ttu-id="99cae-113">Visual Studio rozdíly</span><span class="sxs-lookup"><span data-stu-id="99cae-113">Visual Studio differences</span></span>](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a><span data-ttu-id="99cae-114">Obecné runtime rozdíly</span><span class="sxs-lookup"><span data-stu-id="99cae-114">General runtime differences</span></span>  
  
-   <span data-ttu-id="99cae-115">Výjimky, jako například <xref:System.TypeLoadException>, která jsou vyvolány pomocí kompilátoru JIT, když je aplikace spuštěna ve společné language runtime (CLR) obecně vést k chybám kompilace při zpracování v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>  
  
-   <span data-ttu-id="99cae-116">Nevolejte <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metoda z vlákna uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="99cae-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="99cae-117">To může způsobit zablokování v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-117">This can result in a deadlock on .NET Native.</span></span>  
  
-   <span data-ttu-id="99cae-118">Nemusíte spoléhat na pořadí vyvolání konstruktoru statické třídy.</span><span class="sxs-lookup"><span data-stu-id="99cae-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="99cae-119">V rozhraní .NET Native se liší od pořadí v modulu runtime standardní pořadí volání.</span><span class="sxs-lookup"><span data-stu-id="99cae-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="99cae-120">(I s standardní modulu runtime, neměli byste spoléhat pořadí spuštění statické třídy konstruktory.)</span><span class="sxs-lookup"><span data-stu-id="99cae-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>  
  
-   <span data-ttu-id="99cae-121">Nekonečné smyčky bez volání (například `while(true);`) v libovolném vlákně může přenést aplikaci do zastavení.</span><span class="sxs-lookup"><span data-stu-id="99cae-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="99cae-122">Obdobně čeká velký nebo nekonečné podat aplikace zastavení.</span><span class="sxs-lookup"><span data-stu-id="99cae-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>  
  
-   <span data-ttu-id="99cae-123">Některé obecné inicializace cykly není vyvolat výjimky v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="99cae-124">Například následující kód vyvolá výjimku <xref:System.TypeLoadException> výjimky na standardní modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="99cae-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="99cae-125">V .NET Native nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="99cae-125">In .NET Native, it doesn't.</span></span>  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   <span data-ttu-id="99cae-126">V některých případech poskytuje různé implementace knihovny tříd rozhraní .NET Framework .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="99cae-127">Objekt vrácený z metody vždy členy vrácený typ implementuje.</span><span class="sxs-lookup"><span data-stu-id="99cae-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="99cae-128">Ale protože jeho základní implementaci se liší, je nemusí být schopné provést přetypování na stejnou sadu typů, jako by na jiných platformách rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99cae-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="99cae-129">Například v některých případech se vám nemusí být schopné provést přetypování <xref:System.Collections.Generic.IEnumerable%601> vrácena metodami, jako objekt rozhraní <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> k `T[]`.</span><span class="sxs-lookup"><span data-stu-id="99cae-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>  
  
-   <span data-ttu-id="99cae-130">Ve výchozím nastavení pro aplikace .NET pro Windows Store není povolené mezipaměti rozhraní WinInet, ale je v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="99cae-131">To zvyšuje výkon, ale má pracujícího důsledky sady.</span><span class="sxs-lookup"><span data-stu-id="99cae-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="99cae-132">Není nutná žádná akce pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="99cae-132">No developer action is necessary.</span></span>  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a><span data-ttu-id="99cae-133">Dynamické programování rozdílů</span><span class="sxs-lookup"><span data-stu-id="99cae-133">Dynamic programming differences</span></span>  
 <span data-ttu-id="99cae-134">.NET native staticky odkazuje v kódu z rozhraní .NET Framework, aby kód aplikace místní pro maximální výkon.</span><span class="sxs-lookup"><span data-stu-id="99cae-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="99cae-135">Binární velikosti je však nutné zůstanou malé, takže celé rozhraní .NET Framework není možné připojit v.</span><span class="sxs-lookup"><span data-stu-id="99cae-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="99cae-136">Toto omezení kompilátoru .NET Native řeší pomocí závislost redukční funkci, která odebere odkazy na nepoužitý kód.</span><span class="sxs-lookup"><span data-stu-id="99cae-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="99cae-137">Však .NET Native nemusí udržovat nebo vytvořit některé informace o typu a kód při informace nelze odvodit staticky v době kompilace, ale místo toho se dynamicky načíst za běhu.</span><span class="sxs-lookup"><span data-stu-id="99cae-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>  
  
 <span data-ttu-id="99cae-138">.NET native povolení reflexe a dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="99cae-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="99cae-139">Ne všechny typy však může být označený pro reflexi, protože by velikost generovaného kódu moc velká (zejména protože odráží v rámci veřejných API v rozhraní .NET Framework je podporováno).</span><span class="sxs-lookup"><span data-stu-id="99cae-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="99cae-140">Kompilátor .NET Native díky inteligentní možnosti, které typy by měly podporovat reflexe a uchovává metadata a generuje kód jenom pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="99cae-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>  
  
 <span data-ttu-id="99cae-141">Například datová vazba vyžaduje aplikaci umožnit názvy vlastností namapovat na funkce.</span><span class="sxs-lookup"><span data-stu-id="99cae-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="99cae-142">V aplikacích .NET pro Windows Store modul common language runtime automaticky používá reflexi pro tuto možnost poskytnout pro spravované typy a veřejně dostupné nativní typy.</span><span class="sxs-lookup"><span data-stu-id="99cae-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="99cae-143">V rozhraní .NET Native kompilátor automaticky zahrnuje jejich metadata pro typy, na které svázat data.</span><span class="sxs-lookup"><span data-stu-id="99cae-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>  
  
 <span data-ttu-id="99cae-144">.NET Native kompilátoru zvládne také běžně používá obecné typy, jako <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602>, což práce bez vyžadování jakéhokoli pomocné parametry nebo direktivy.</span><span class="sxs-lookup"><span data-stu-id="99cae-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="99cae-145">[Dynamické](~/docs/csharp/language-reference/keywords/dynamic.md) – klíčové slovo je podporováno také v rámci určitá omezení.</span><span class="sxs-lookup"><span data-stu-id="99cae-145">The [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99cae-146">Při přenesení aplikace do .NET Native měli důkladně otestujte všech cestách kódu. dynamické.</span><span class="sxs-lookup"><span data-stu-id="99cae-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>  
  
 <span data-ttu-id="99cae-147">Výchozí konfigurace pro .NET Native stačí pro většinu vývojářů, ale někteří vývojáři mohou chtít jemné ladit jejich konfigurace s použitím direktivy modulu runtime (. rd.xml) soubor.</span><span class="sxs-lookup"><span data-stu-id="99cae-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="99cae-148">Kromě toho v některých případech se kompilátoru .NET Native nelze určit, která metadata musí být k dispozici pro účely reflexe a spoléhá na pomocné parametry, zejména v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="99cae-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>  
  
-   <span data-ttu-id="99cae-149">Některé konstrukce, jako jsou <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> a <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> nemůže být určeno staticky.</span><span class="sxs-lookup"><span data-stu-id="99cae-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>  
  
-   <span data-ttu-id="99cae-150">Obecný typ, který chcete zhodnocení, protože kompilátor nemůže určit, instancí, musí být zadaný pomocí direktivy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="99cae-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="99cae-151">Nejedná se o to, že veškerý kód musí být zahrnut, ale protože odraz na obecných typech mohl vytvořit nekonečné cyklus (například, když obecné metody se vyvolá u obecného typu).</span><span class="sxs-lookup"><span data-stu-id="99cae-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99cae-152">Direktivy modulu runtime jsou definovány v direktivy modulu runtime (. rd.xml) soubor.</span><span class="sxs-lookup"><span data-stu-id="99cae-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="99cae-153">Obecné informace o použití tohoto souboru najdete v tématu [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="99cae-153">For general information about using this file, see [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span> <span data-ttu-id="99cae-154">Informace o direktivy modulu runtime naleznete v tématu [direktivy modulu Runtime (rd.xml) odkaz na soubor konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="99cae-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
 <span data-ttu-id="99cae-155">.NET native také zahrnuje profilování nástroje, které pomůžou vývojářům určit, jaké typy mimo výchozí sadu by měla podporovat reflexe.</span><span class="sxs-lookup"><span data-stu-id="99cae-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a><span data-ttu-id="99cae-156">Další související reflexe rozdíly</span><span class="sxs-lookup"><span data-stu-id="99cae-156">Other reflection-related differences</span></span>  
 <span data-ttu-id="99cae-157">Existuje mnoho dalších jednotlivé související reflexe rozdíly v chování mezi aplikacemi .NET pro Windows Store a .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>  
  
 <span data-ttu-id="99cae-158">V .NET Native:</span><span class="sxs-lookup"><span data-stu-id="99cae-158">In .NET Native:</span></span>  
  
-   <span data-ttu-id="99cae-159">Privátní reflexe přes typy a členy v knihovně tříd rozhraní .NET Framework není podporováno.</span><span class="sxs-lookup"><span data-stu-id="99cae-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="99cae-160">Můžete však reflexi vlastní privátní typy a členy, jakož i typy a členy v knihovnách třetích stran.</span><span class="sxs-lookup"><span data-stu-id="99cae-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>  
  
-   <span data-ttu-id="99cae-161"><xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Správně vrátí vlastnost `false` pro <xref:System.Reflection.ParameterInfo> objekt, který reprezentuje návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="99cae-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="99cae-162">V aplikacích .NET pro Windows Store, vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="99cae-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="99cae-163">Převodní jazyk (IL) nepodporuje tento přímo a výkladu je ponecháno na jazyk.</span><span class="sxs-lookup"><span data-stu-id="99cae-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>  
  
-   <span data-ttu-id="99cae-164">Veřejné členy na <xref:System.RuntimeFieldHandle> a <xref:System.RuntimeMethodHandle> struktury nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="99cae-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="99cae-165">Tyto typy jsou podporovány pouze pro LINQ, stromy výrazů a inicializace statické pole.</span><span class="sxs-lookup"><span data-stu-id="99cae-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>  
  
-   <span data-ttu-id="99cae-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> a <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> zahrnout skryté členy základních tříd a může proto přepsat bez explicitního přepsání.</span><span class="sxs-lookup"><span data-stu-id="99cae-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="99cae-167">To platí také pro jiné [RuntimeReflectionExtensions.GetRuntime\*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="99cae-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) methods.</span></span>  
  
-   <span data-ttu-id="99cae-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> a <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> není selhání při pokusu o vytvoření určité kombinace (například pole Parametry ByRef).</span><span class="sxs-lookup"><span data-stu-id="99cae-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>  
  
-   <span data-ttu-id="99cae-169">Reflexe nelze použít k vyvolání členy, které mají parametry ukazatele.</span><span class="sxs-lookup"><span data-stu-id="99cae-169">You can't use reflection to invoke members that have pointer parameters.</span></span>  
  
-   <span data-ttu-id="99cae-170">Reflexe nelze použít k získání nebo nastavení pole ukazatel.</span><span class="sxs-lookup"><span data-stu-id="99cae-170">You can't use reflection to get or set a pointer field.</span></span>  
  
-   <span data-ttu-id="99cae-171">Když je nesprávný počet argumentů a typ jednoho z argumentů není správný, .NET Native vyvolá <xref:System.ArgumentException> místo <xref:System.Reflection.TargetParameterCountException>.</span><span class="sxs-lookup"><span data-stu-id="99cae-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>  
  
-   <span data-ttu-id="99cae-172">Binární serializace výjimek není obecně podporována.</span><span class="sxs-lookup"><span data-stu-id="99cae-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="99cae-173">V důsledku toho nejsou objekty mohou být přidány do <xref:System.Exception.Data%2A?displayProperty=nameWithType> slovníku.</span><span class="sxs-lookup"><span data-stu-id="99cae-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="99cae-174">Nepodporované scénáře a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="99cae-174">Unsupported scenarios and APIs</span></span>  
 <span data-ttu-id="99cae-175">V následujících částech nepodporované scénáře a rozhraní API pro obecný vývoj, spolupráce a technologie, jako je HTTPClient a Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="99cae-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>  
  
-   [<span data-ttu-id="99cae-176">Obecný vývoj</span><span class="sxs-lookup"><span data-stu-id="99cae-176">General development</span></span>](#General)  
  
-   [<span data-ttu-id="99cae-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="99cae-177">HttpClient</span></span>](#HttpClient)  
  
-   [<span data-ttu-id="99cae-178">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="99cae-178">Interop</span></span>](#Interop)  
  
-   [<span data-ttu-id="99cae-179">Nepodporované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="99cae-179">Unsupported APIs</span></span>](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a><span data-ttu-id="99cae-180">Obecný vývoj rozdíly</span><span class="sxs-lookup"><span data-stu-id="99cae-180">General development differences</span></span>  
 <span data-ttu-id="99cae-181">**Typy hodnot**</span><span class="sxs-lookup"><span data-stu-id="99cae-181">**Value types**</span></span>  
  
-   <span data-ttu-id="99cae-182">Pokud přepíšete <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> a <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody pro typ hodnoty, nevolejte implementace základní třídy.</span><span class="sxs-lookup"><span data-stu-id="99cae-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="99cae-183">V aplikacích .NET pro Windows Store tyto metody závisí na reflexi.</span><span class="sxs-lookup"><span data-stu-id="99cae-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="99cae-184">V době kompilace .NET Native generuje implementace, která se nemusí spoléhat na reflexe runtime.</span><span class="sxs-lookup"><span data-stu-id="99cae-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="99cae-185">To znamená, že pokud nepřepíšete tyto dvě metody, budou fungovat podle očekávání, protože implementace v době kompilace .NET Native generuje.</span><span class="sxs-lookup"><span data-stu-id="99cae-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="99cae-186">Ale přepsání těchto metod ale volání implementace základní třídy za následek výjimku.</span><span class="sxs-lookup"><span data-stu-id="99cae-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>  
  
-   <span data-ttu-id="99cae-187">Typy hodnot, které jsou větší než jeden megabajt, ale nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="99cae-187">Value types larger than one megabyte aren't supported.</span></span>  
  
-   <span data-ttu-id="99cae-188">Typy hodnot nemohou mít výchozí konstruktor v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-188">Value types can't have a default constructor in .NET Native.</span></span> <span data-ttu-id="99cae-189">(C# a Visual Basic zakázat výchozí konstruktory na hodnotách.</span><span class="sxs-lookup"><span data-stu-id="99cae-189">(C# and Visual Basic prohibit default constructors on value types.</span></span> <span data-ttu-id="99cae-190">Nicméně ty lze vytvořit v IL.)</span><span class="sxs-lookup"><span data-stu-id="99cae-190">However, these can be created in IL.)</span></span>  
  
 <span data-ttu-id="99cae-191">**Pole**</span><span class="sxs-lookup"><span data-stu-id="99cae-191">**Arrays**</span></span>  
  
-   <span data-ttu-id="99cae-192">Pole s dolní hranicí jinou než nula, nejsou podporována.</span><span class="sxs-lookup"><span data-stu-id="99cae-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="99cae-193">Obvykle se tato pole vytvářejí voláním <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> přetížení.</span><span class="sxs-lookup"><span data-stu-id="99cae-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
-   <span data-ttu-id="99cae-194">Dynamické vytváření vícerozměrných polí není podporováno.</span><span class="sxs-lookup"><span data-stu-id="99cae-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="99cae-195">Takové pole jsou obvykle vytvořeny voláním přetížení <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metoda, která zahrnuje `lengths` parametr, nebo voláním <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="99cae-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="99cae-196">Vícerozměrná pole, které mají čtyři nebo více dimenzí nejsou podporovány. To znamená, že jejich <xref:System.Array.Rank%2A?displayProperty=nameWithType> hodnotu vlastnosti, jsou čtyři nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="99cae-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="99cae-197">Použití [Vícenásobná pole](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (pole polí) místo toho.</span><span class="sxs-lookup"><span data-stu-id="99cae-197">Use [jagged arrays](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="99cae-198">Například `array[x,y,z]` není platný, ale `array[x][y][z]` není.</span><span class="sxs-lookup"><span data-stu-id="99cae-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>  
  
-   <span data-ttu-id="99cae-199">Variance pro vícerozměrná pole se nepodporuje a způsobí, že <xref:System.InvalidCastException> výjimka za běhu.</span><span class="sxs-lookup"><span data-stu-id="99cae-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>  
  
 <span data-ttu-id="99cae-200">**Obecné typy**</span><span class="sxs-lookup"><span data-stu-id="99cae-200">**Generics**</span></span>  
  
-   <span data-ttu-id="99cae-201">Nekonečné rozšíření generického typu způsobí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="99cae-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="99cae-202">Tento kód například selže při kompilaci:</span><span class="sxs-lookup"><span data-stu-id="99cae-202">For example, this code fails to compile:</span></span>  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 <span data-ttu-id="99cae-203">**Ukazatele**</span><span class="sxs-lookup"><span data-stu-id="99cae-203">**Pointers**</span></span>  
  
-   <span data-ttu-id="99cae-204">Pole ukazatelů nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="99cae-204">Arrays of pointers aren't supported.</span></span>  
  
-   <span data-ttu-id="99cae-205">Reflexe nelze použít k získání nebo nastavení pole ukazatel.</span><span class="sxs-lookup"><span data-stu-id="99cae-205">You can't use reflection to get or set a pointer field.</span></span>  
  
 <span data-ttu-id="99cae-206">**Serializace**</span><span class="sxs-lookup"><span data-stu-id="99cae-206">**Serialization**</span></span>  
  
 <span data-ttu-id="99cae-207"><xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Atribut není podporován.</span><span class="sxs-lookup"><span data-stu-id="99cae-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="99cae-208">Použití <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> místo atributu.</span><span class="sxs-lookup"><span data-stu-id="99cae-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>  
  
 <span data-ttu-id="99cae-209">**Prostředky**</span><span class="sxs-lookup"><span data-stu-id="99cae-209">**Resources**</span></span>  
  
 <span data-ttu-id="99cae-210">Používání lokalizované prostředky <xref:System.Diagnostics.Tracing.EventSource> třída není podporována.</span><span class="sxs-lookup"><span data-stu-id="99cae-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="99cae-211"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Vlastnost nedefinuje lokalizované prostředky.</span><span class="sxs-lookup"><span data-stu-id="99cae-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>  
  
 <span data-ttu-id="99cae-212">**Delegáti**</span><span class="sxs-lookup"><span data-stu-id="99cae-212">**Delegates**</span></span>  
  
 <span data-ttu-id="99cae-213">`Delegate.BeginInvoke` a `Delegate.EndInvoke` nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="99cae-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>  
  
 <span data-ttu-id="99cae-214">**Ostatní rozhraní API**</span><span class="sxs-lookup"><span data-stu-id="99cae-214">**Miscellaneous APIs**</span></span>  
  
-   <span data-ttu-id="99cae-215"><xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> Vlastnost vyvolá <xref:System.PlatformNotSupportedException> výjimka pokud <xref:System.Runtime.InteropServices.GuidAttribute> není použit atribut typu.</span><span class="sxs-lookup"><span data-stu-id="99cae-215">The <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="99cae-216">Identifikátor GUID slouží především pro podporu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="99cae-216">The GUID is used primarily for COM support.</span></span>  
  
-   <span data-ttu-id="99cae-217"><xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Metoda správně Parsuje řetězce, které obsahují krátký kalendářní data v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="99cae-218">Ale se nebude udržovat kompatibilitu s změny v datum a čas analýzy je popsáno v článcích znalostní báze Microsoft Knowledge Base [KB2803771](http://support.microsoft.com/kb/2803771) a [KB2803755](http://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="99cae-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](http://support.microsoft.com/kb/2803771) and [KB2803755](http://support.microsoft.com/kb/2803755).</span></span>  
  
-   <span data-ttu-id="99cae-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` poloměr zaoblení správně v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="99cae-220">V některých verzích CLR je výsledný řetězec zkrácen místo zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="99cae-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a><span data-ttu-id="99cae-221">Rozdíly HttpClient</span><span class="sxs-lookup"><span data-stu-id="99cae-221">HttpClient differences</span></span>  
 <span data-ttu-id="99cae-222">V rozhraní .NET Native <xref:System.Net.Http.HttpClientHandler> třída interně používá rozhraní WinINet (prostřednictvím [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třídy) namísto <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy používané ve standardní aplikace .NET pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="99cae-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="99cae-223">WinINet nepodporuje všechny možnosti konfigurace, pro které <xref:System.Net.Http.HttpClientHandler> třídy podporuje.</span><span class="sxs-lookup"><span data-stu-id="99cae-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="99cae-224">Výsledek:</span><span class="sxs-lookup"><span data-stu-id="99cae-224">As a result:</span></span>  
  
-   <span data-ttu-id="99cae-225">Některé vlastnosti funkce na <xref:System.Net.Http.HttpClientHandler> vrátit `false` v .NET Native, že vrátí `true` ve standardní aplikace .NET pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="99cae-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>  
  
-   <span data-ttu-id="99cae-226">Některé vlastnosti konfigurace `get` přistupující objekty vždy vrátí pevnou hodnotu v .NET Native, která je jiná než výchozí hodnotu konfigurovatelné v aplikacích .NET pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="99cae-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="99cae-227">Některé další rozdíly jsou popsané v následujících oddílech.</span><span class="sxs-lookup"><span data-stu-id="99cae-227">Some additional behavior differences are covered in the following subsections.</span></span>  
  
 <span data-ttu-id="99cae-228">**Proxy server**</span><span class="sxs-lookup"><span data-stu-id="99cae-228">**Proxy**</span></span>  
  
 <span data-ttu-id="99cae-229">[HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třída nepodporuje konfiguraci nebo přepsání proxy serveru na základě žádosti.</span><span class="sxs-lookup"><span data-stu-id="99cae-229">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="99cae-230">To znamená, že všechny žádosti na .NET Native používat systému nakonfigurovaný proxy server nebo žádný proxy server, v závislosti na hodnotu <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="99cae-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="99cae-231">V aplikacích .NET pro Windows Store, je definován proxy serveru <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="99cae-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="99cae-232">V .NET Native, nastavení <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> hodnotu jinou než `null` vyvolá <xref:System.PlatformNotSupportedException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="99cae-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="99cae-233"><xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Vrátí vlastnost `false` v .NET Native, že ji vrací `true` ve standardní aplikace rozhraní .NET Framework pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="99cae-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>  
  
 <span data-ttu-id="99cae-234">**Automatické přesměrování**</span><span class="sxs-lookup"><span data-stu-id="99cae-234">**Automatic redirection**</span></span>  
  
 <span data-ttu-id="99cae-235">[HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třídy neumožňuje maximálního počtu automatické přesměrování nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="99cae-235">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="99cae-236">Hodnota <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> vlastnost je 50 ve výchozím nastavení standardní aplikace .NET pro Windows Store a je možné upravit.</span><span class="sxs-lookup"><span data-stu-id="99cae-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="99cae-237">V .NET Native, tato vlastnost hodnotu 10 a upravit ji vyvolá výjimku při pokusu <xref:System.PlatformNotSupportedException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="99cae-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="99cae-238"><xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Vrátí vlastnost `false` v .NET Native, že ji vrací `true` v aplikacích .NET pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="99cae-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="99cae-239">**Automatická dekomprese**</span><span class="sxs-lookup"><span data-stu-id="99cae-239">**Automatic decompression**</span></span>  
  
 <span data-ttu-id="99cae-240">.NET pro Windows Store apps vám umožní nastavit <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> vlastnost <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, obě <xref:System.Net.DecompressionMethods.Deflate> a <xref:System.Net.DecompressionMethods.GZip>, nebo <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="99cae-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="99cae-241">.NET native podporuje pouze <xref:System.Net.DecompressionMethods.Deflate> spolu s <xref:System.Net.DecompressionMethods.GZip>, nebo <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="99cae-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="99cae-242">Pokoušíte se nastavit <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> vlastnost buď <xref:System.Net.DecompressionMethods.Deflate> nebo <xref:System.Net.DecompressionMethods.GZip> samostatně tiše nastaví na obě <xref:System.Net.DecompressionMethods.Deflate> a <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="99cae-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>  
  
 <span data-ttu-id="99cae-243">**Soubory cookie**</span><span class="sxs-lookup"><span data-stu-id="99cae-243">**Cookies**</span></span>  
  
 <span data-ttu-id="99cae-244">Zpracování souborů cookie najednou pomocí provádí <xref:System.Net.Http.HttpClient> a rozhraní WinINet.</span><span class="sxs-lookup"><span data-stu-id="99cae-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="99cae-245">Soubory cookie z <xref:System.Net.CookieContainer> spolu se soubory cookie do mezipaměti rozhraní WinINet souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="99cae-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="99cae-246">Odebírá se soubor cookie z <xref:System.Net.CookieContainer> brání <xref:System.Net.Http.HttpClient> odesílání souboru cookie, ale pokud soubor cookie již viděla WinINet a soubory cookie nedošlo k odstranění tohoto uživatele z rozhraní WinINet odešle.</span><span class="sxs-lookup"><span data-stu-id="99cae-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="99cae-247">Není možné programově odebrat soubor cookie z rozhraní WinINet pomocí <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, nebo <xref:System.Net.CookieContainer> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="99cae-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="99cae-248">Nastavení <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> vlastnost `false` způsobí, že pouze <xref:System.Net.Http.HttpClient> aby přestalo odesílat soubory cookie. Wininet – může obsahovat stále její soubory cookie v požadavku.</span><span class="sxs-lookup"><span data-stu-id="99cae-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>  
  
 <span data-ttu-id="99cae-249">**Přihlašovací údaje**</span><span class="sxs-lookup"><span data-stu-id="99cae-249">**Credentials**</span></span>  
  
 <span data-ttu-id="99cae-250">V aplikacích .NET pro Windows Store <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> a <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> vlastnosti pracovat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="99cae-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="99cae-251">Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost přijímá libovolný objekt, který implementuje <xref:System.Net.ICredentials> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="99cae-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="99cae-252">V rozhraní .NET Native, nastavení <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> vlastnost `true` způsobí, že <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost `null`.</span><span class="sxs-lookup"><span data-stu-id="99cae-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="99cae-253">Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost lze nastavit pouze na `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, nebo objekt typu <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="99cae-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="99cae-254">Přiřazení jiného <xref:System.Net.ICredentials> objektu, nejoblíbenější z nich je <xref:System.Net.CredentialCache>do <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost vyvolá <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="99cae-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>  
  
 <span data-ttu-id="99cae-255">**Další funkce nepodporované nebo unconfigurable**</span><span class="sxs-lookup"><span data-stu-id="99cae-255">**Other unsupported or unconfigurable features**</span></span>  
  
 <span data-ttu-id="99cae-256">V .NET Native:</span><span class="sxs-lookup"><span data-stu-id="99cae-256">In .NET Native:</span></span>  
  
-   <span data-ttu-id="99cae-257">Hodnota <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> vlastnost je vždy <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="99cae-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="99cae-258">V aplikacích .NET pro Windows Store, výchozí hodnota je <xref:System.Net.Http.ClientCertificateOption.Manual>.</span><span class="sxs-lookup"><span data-stu-id="99cae-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>  
  
-   <span data-ttu-id="99cae-259"><xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Vlastnost není konfigurovatelné.</span><span class="sxs-lookup"><span data-stu-id="99cae-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>  
  
-   <span data-ttu-id="99cae-260"><xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Vlastnost je vždy `true`.</span><span class="sxs-lookup"><span data-stu-id="99cae-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="99cae-261">V aplikacích .NET pro Windows Store, výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="99cae-261">In .NET for Windows Store apps, the default is `false`.</span></span>  
  
-   <span data-ttu-id="99cae-262">`SetCookie2` Hlaviček v odpovědi se ignoruje jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="99cae-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a><span data-ttu-id="99cae-263">Spolupráce rozdíly</span><span class="sxs-lookup"><span data-stu-id="99cae-263">Interop differences</span></span>  
 <span data-ttu-id="99cae-264">**Zastaralé rozhraní API**</span><span class="sxs-lookup"><span data-stu-id="99cae-264">**Deprecated APIs**</span></span>  
  
 <span data-ttu-id="99cae-265">Počet zřídka používaný rozhraní API pro interoperabilitu se spravovaným kódem se již nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="99cae-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="99cae-266">Při použití s .NET Native, může vyvolat tato rozhraní API <xref:System.NotImplementedException> nebo <xref:System.PlatformNotSupportedException> výjimky nebo vyústí v chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="99cae-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="99cae-267">V aplikacích .NET pro Windows Store tato rozhraní API jsou označeny jako zastaralé, i když jejich volání generuje kompilátor varování spíše než chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="99cae-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>  
  
 <span data-ttu-id="99cae-268">Zastaralá rozhraní API pro `VARIANT` zařazování:</span><span class="sxs-lookup"><span data-stu-id="99cae-268">Deprecated APIs for `VARIANT` marshaling:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>|  
  
 <span data-ttu-id="99cae-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> je podporováno, ale vyvolá výjimku v některých případech, například při použití s [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) nebo varianty byref.</span><span class="sxs-lookup"><span data-stu-id="99cae-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) or byref variants.</span></span>  
  
 <span data-ttu-id="99cae-270">Zastaralá rozhraní API pro [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) podporují:</span><span class="sxs-lookup"><span data-stu-id="99cae-270">Deprecated APIs for [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) support:</span></span>  
  
|<span data-ttu-id="99cae-271">Typ</span><span class="sxs-lookup"><span data-stu-id="99cae-271">Type</span></span>|<span data-ttu-id="99cae-272">Člen</span><span class="sxs-lookup"><span data-stu-id="99cae-272">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>|<span data-ttu-id="99cae-273">Atribut není podporovaný.</span><span class="sxs-lookup"><span data-stu-id="99cae-273">Attribute isn't supported</span></span>|  
  
 <span data-ttu-id="99cae-274">Zastaralé rozhraní API classic událostí modelu COM:</span><span class="sxs-lookup"><span data-stu-id="99cae-274">Deprecated APIs for classic COM events:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 <span data-ttu-id="99cae-275">Zastaralá rozhraní API v <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> rozhraní, což není podporováno v .NET Native:</span><span class="sxs-lookup"><span data-stu-id="99cae-275">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native:</span></span>  
  
|<span data-ttu-id="99cae-276">Typ</span><span class="sxs-lookup"><span data-stu-id="99cae-276">Type</span></span>|<span data-ttu-id="99cae-277">Člen</span><span class="sxs-lookup"><span data-stu-id="99cae-277">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>|<span data-ttu-id="99cae-278">Všichni členové.</span><span class="sxs-lookup"><span data-stu-id="99cae-278">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>|<span data-ttu-id="99cae-279">Všichni členové.</span><span class="sxs-lookup"><span data-stu-id="99cae-279">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>|<span data-ttu-id="99cae-280">Všichni členové.</span><span class="sxs-lookup"><span data-stu-id="99cae-280">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=nameWithType>|  
  
 <span data-ttu-id="99cae-281">Nepodporované spolupráce funkce:</span><span class="sxs-lookup"><span data-stu-id="99cae-281">Other unsupported interop features:</span></span>  
  
|<span data-ttu-id="99cae-282">Typ</span><span class="sxs-lookup"><span data-stu-id="99cae-282">Type</span></span>|<span data-ttu-id="99cae-283">Člen</span><span class="sxs-lookup"><span data-stu-id="99cae-283">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>|<span data-ttu-id="99cae-284">Všichni členové.</span><span class="sxs-lookup"><span data-stu-id="99cae-284">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>|<span data-ttu-id="99cae-285">Všichni členové.</span><span class="sxs-lookup"><span data-stu-id="99cae-285">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 <span data-ttu-id="99cae-286">Zřídka se používá sběrného systému rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="99cae-286">Rarely used marshalling APIs:</span></span>  
  
|<span data-ttu-id="99cae-287">Typ</span><span class="sxs-lookup"><span data-stu-id="99cae-287">Type</span></span>|<span data-ttu-id="99cae-288">Člen</span><span class="sxs-lookup"><span data-stu-id="99cae-288">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 <span data-ttu-id="99cae-289">**Vyvolání platformy a kompatibilita vzájemné spolupráce COM**</span><span class="sxs-lookup"><span data-stu-id="99cae-289">**Platform invoke and COM interop compatibility**</span></span>  
  
 <span data-ttu-id="99cae-290">Většina nespravovaného kódu a modelu COM interop scénáře jsou stále podporovány v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-290">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="99cae-291">Konkrétně se podporuje všechny interoperability s modulem Windows Runtime (WinRT) rozhraní API a zařazování požadované pro prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="99cae-291">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="99cae-292">To zahrnuje podporu pro zařazování:</span><span class="sxs-lookup"><span data-stu-id="99cae-292">This includes marshaling support for:</span></span>  
  
-   <span data-ttu-id="99cae-293">Pole (včetně <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="99cae-293">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>  
  
-   `BStr`  
  
-   <span data-ttu-id="99cae-294">Delegáty</span><span class="sxs-lookup"><span data-stu-id="99cae-294">Delegates</span></span>  
  
-   <span data-ttu-id="99cae-295">Řetězce (kódování Unicode, Ansi a HSTRING)</span><span class="sxs-lookup"><span data-stu-id="99cae-295">Strings (Unicode, Ansi, and HSTRING)</span></span>  
  
-   <span data-ttu-id="99cae-296">Struktury (`byref` a `byval`)</span><span class="sxs-lookup"><span data-stu-id="99cae-296">Structs (`byref` and `byval`)</span></span>  
  
-   <span data-ttu-id="99cae-297">Sjednocení</span><span class="sxs-lookup"><span data-stu-id="99cae-297">Unions</span></span>  
  
-   <span data-ttu-id="99cae-298">Obslužné rutiny Win32</span><span class="sxs-lookup"><span data-stu-id="99cae-298">Win32 handles</span></span>  
  
-   <span data-ttu-id="99cae-299">Všechny konstruktory WinRT</span><span class="sxs-lookup"><span data-stu-id="99cae-299">All WinRT constructs</span></span>  
  
-   <span data-ttu-id="99cae-300">Částečně se podporuje pro zařazování typů variant.</span><span class="sxs-lookup"><span data-stu-id="99cae-300">Partial support for marshaling variant types.</span></span> <span data-ttu-id="99cae-301">Jsou podporovány následující:</span><span class="sxs-lookup"><span data-stu-id="99cae-301">The following are supported:</span></span>  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [<span data-ttu-id="99cae-302">IUnknown</span><span class="sxs-lookup"><span data-stu-id="99cae-302">IUnknown</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 <span data-ttu-id="99cae-303">Ale .NET Native nepodporuje následující:</span><span class="sxs-lookup"><span data-stu-id="99cae-303">However, .NET Native doesn't support the following:</span></span>  
  
-   <span data-ttu-id="99cae-304">Použití klasického událostí modelu COM</span><span class="sxs-lookup"><span data-stu-id="99cae-304">Using classic COM events</span></span>  
  
-   <span data-ttu-id="99cae-305">Implementace <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> na spravovaný typ rozhraní</span><span class="sxs-lookup"><span data-stu-id="99cae-305">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>  
  
-   <span data-ttu-id="99cae-306">Implementace [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) rozhraní pro spravovaný typ prostřednictvím <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> atribut.</span><span class="sxs-lookup"><span data-stu-id="99cae-306">Implementing the [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="99cae-307">Mějte však na paměti, že nelze volat COM objekty prostřednictvím `IDispatch`, a spravovaný objekt nemůže implementovat `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="99cae-307">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>  
  
 <span data-ttu-id="99cae-308">Použití reflexe pro vyvolání platformy volání metody není podporováno.</span><span class="sxs-lookup"><span data-stu-id="99cae-308">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="99cae-309">Toto omezení můžete obejít obtékání volání metody v jiné metody a místo toho Obálka volání pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="99cae-309">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="99cae-310">Další rozdíly v rozhraní .NET API pro Windows Store apps</span><span class="sxs-lookup"><span data-stu-id="99cae-310">Other differences from .NET APIs for Windows Store apps</span></span>  
 <span data-ttu-id="99cae-311">Tato část uvádí zbývající rozhraní API, která se v .NET Native nepodporují.</span><span class="sxs-lookup"><span data-stu-id="99cae-311">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="99cae-312">Největší sada nepodporované rozhraní API je Windows Communication Foundation (WCF) rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="99cae-312">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>  
  
 <span data-ttu-id="99cae-313">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="99cae-313">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>  
  
 <span data-ttu-id="99cae-314">Typy v <xref:System.ComponentModel.DataAnnotations> a <xref:System.ComponentModel.DataAnnotations.Schema> obory názvů v .NET Native nepodporují.</span><span class="sxs-lookup"><span data-stu-id="99cae-314">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="99cae-315">Patří mezi ně následující typy, které se nacházejí v aplikacích .NET pro Windows Store pro Windows 8:</span><span class="sxs-lookup"><span data-stu-id="99cae-315">These include the following types that are present in the .NET for Windows Store apps for Windows 8:</span></span>  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>|  
  
 <span data-ttu-id="99cae-316">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="99cae-316">**Visual Basic**</span></span>  
  
 <span data-ttu-id="99cae-317">Visual Basic se v .NET Native momentálně nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="99cae-317">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="99cae-318">Následující typy, které do <xref:Microsoft.VisualBasic> a <xref:Microsoft.VisualBasic.CompilerServices> obory názvů nejsou k dispozici v .NET Native:</span><span class="sxs-lookup"><span data-stu-id="99cae-318">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>|  
  
 <span data-ttu-id="99cae-319">**Kontext odrazu (obor názvů System.Reflection.Context)**</span><span class="sxs-lookup"><span data-stu-id="99cae-319">**Reflection Context (System.Reflection.Context namespace)**</span></span>  
  
 <span data-ttu-id="99cae-320"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Třída není podporována v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-320">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>  
  
 <span data-ttu-id="99cae-321">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="99cae-321">**RTC (System.Net.Http.Rtc)**</span></span>  
  
 <span data-ttu-id="99cae-322"><xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> Třída není podporována v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99cae-322">The <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>  
  
 <span data-ttu-id="99cae-323">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="99cae-323">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>  
  
 <span data-ttu-id="99cae-324">Typy v [obory názvů System.ServiceModel.\*](http://msdn.microsoft.com/library/gg145010.aspx) v .NET Native nepodporují.</span><span class="sxs-lookup"><span data-stu-id="99cae-324">The types in the [System.ServiceModel.\* namespaces](http://msdn.microsoft.com/library/gg145010.aspx) aren't supported in .NET Native.</span></span> <span data-ttu-id="99cae-325">To zahrnuje následující typy:</span><span class="sxs-lookup"><span data-stu-id="99cae-325">These includes the following types:</span></span>  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>|  
  
### <a name="differences-in-serializers"></a><span data-ttu-id="99cae-326">Rozdíly v serializátorů</span><span class="sxs-lookup"><span data-stu-id="99cae-326">Differences in serializers</span></span>  
 <span data-ttu-id="99cae-327">Tyto věci se týkají serializace a deserializace pomocí <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer> třídy:</span><span class="sxs-lookup"><span data-stu-id="99cae-327">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>  
  
-   <span data-ttu-id="99cae-328">V rozhraní .NET Native <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> selhání k serializaci nebo deserializaci odvozenou třídu, která má člena základní třídy, jejíž typ není kořenový typ serializace.</span><span class="sxs-lookup"><span data-stu-id="99cae-328">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="99cae-329">Například v následujícím kódu pokusu o serializaci nebo deserializaci `Y` způsobí chybu:</span><span class="sxs-lookup"><span data-stu-id="99cae-329">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     <span data-ttu-id="99cae-330">Typ `InnerType` nezná serializátor, protože se během serializace procházet členy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="99cae-330">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>  
  
-   <span data-ttu-id="99cae-331"><xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> selhání k serializaci třídy nebo struktury, která implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="99cae-331"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="99cae-332">Například následující typy selhání k serializaci nebo deserializaci:</span><span class="sxs-lookup"><span data-stu-id="99cae-332">For example, the following types fail to serialize or deserialize:</span></span>  
  
  
  
-   <span data-ttu-id="99cae-333"><xref:System.Xml.Serialization.XmlSerializer> selže při serializaci následující hodnotu objektu, protože nemá specifické znalosti přesného typu objekt, který má být serializován:</span><span class="sxs-lookup"><span data-stu-id="99cae-333"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>  
  
  
  
-   <span data-ttu-id="99cae-334"><xref:System.Xml.Serialization.XmlSerializer> k serializaci nebo deserializaci, pokud je typ serializovaný objekt se nezdaří <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="99cae-334"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>  
  
-   <span data-ttu-id="99cae-335">Všechny serializátory (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer>) nepovedlo se generovat Serializační kód pro typ <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> nebo pro typ, který obsahuje <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="99cae-335">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="99cae-336">Místo toho zobrazí chyby sestavení.</span><span class="sxs-lookup"><span data-stu-id="99cae-336">They display build-time errors instead.</span></span>  
  
-   <span data-ttu-id="99cae-337">Následující konstruktory typů serializace nemusí fungovat podle očekávání:</span><span class="sxs-lookup"><span data-stu-id="99cae-337">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>  
  
-   <span data-ttu-id="99cae-338"><xref:System.Xml.Serialization.XmlSerializer> selhání pro generování kódu pro typ, který obsahuje metody s některou z následujících atributů:</span><span class="sxs-lookup"><span data-stu-id="99cae-338"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <span data-ttu-id="99cae-339"><xref:System.Xml.Serialization.XmlSerializer> nebude respektovat <xref:System.Xml.Serialization.IXmlSerializable> vlastní serializace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="99cae-339"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="99cae-340">Pokud máte třídu, která implementuje toto rozhraní <xref:System.Xml.Serialization.XmlSerializer> bere v úvahu typ prostý původní typ objektu (POCO) CLR a serializuje pouze veřejné vlastností.</span><span class="sxs-lookup"><span data-stu-id="99cae-340">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>  
  
-   <span data-ttu-id="99cae-341">Serializace prostý <xref:System.Exception> objektu, například následující příkaz, nebude fungovat s <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="99cae-341">Serializing a plain <xref:System.Exception> object, such as the following, doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a><span data-ttu-id="99cae-342">Visual Studio rozdíly</span><span class="sxs-lookup"><span data-stu-id="99cae-342">Visual Studio differences</span></span>  
 <span data-ttu-id="99cae-343">**Ladění a výjimek**</span><span class="sxs-lookup"><span data-stu-id="99cae-343">**Exceptions and debugging**</span></span>  
  
 <span data-ttu-id="99cae-344">Pokud používáte aplikace kompilované pomocí .NET Native v ladicím programu, výjimkách first-chance jsou povolené pro následující typy výjimek:</span><span class="sxs-lookup"><span data-stu-id="99cae-344">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 <span data-ttu-id="99cae-345">**Vytváření aplikací**</span><span class="sxs-lookup"><span data-stu-id="99cae-345">**Building apps**</span></span>  
  
 <span data-ttu-id="99cae-346">Použít x86 sestavení nástroje, které se používají ve výchozím nastavení sada Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99cae-346">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="99cae-347">Nedoporučujeme ale používat nástroje AMD64 MSBuild, které jsou součástí C:\Program Files (x86)\MSBuild\12.0\bin\amd64; To může způsobit problémy sestavení.</span><span class="sxs-lookup"><span data-stu-id="99cae-347">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>  
  
 <span data-ttu-id="99cae-348">**Profilovací programy**</span><span class="sxs-lookup"><span data-stu-id="99cae-348">**Profilers**</span></span>  
  
-   <span data-ttu-id="99cae-349">Profiler procesoru Visual Studio a Profiler paměti XAML nezobrazují pouze můj kód správně.</span><span class="sxs-lookup"><span data-stu-id="99cae-349">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>  
  
-   <span data-ttu-id="99cae-350">Profiler paměti XAML nebude přesně zobrazovat data spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="99cae-350">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>  
  
-   <span data-ttu-id="99cae-351">Profiler procesoru není správně identifikovat moduly a zobrazí předponou názvy funkcí.</span><span class="sxs-lookup"><span data-stu-id="99cae-351">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>  
  
 <span data-ttu-id="99cae-352">**Projekty knihovny testů jednotek**</span><span class="sxs-lookup"><span data-stu-id="99cae-352">**Unit Test Library projects**</span></span>  
  
 <span data-ttu-id="99cae-353">Povolení .NET Native v knihovna testů jednotek pro projekt aplikace Windows Store se nepodporuje a způsobí, že projekt tak, aby se nesestaví.</span><span class="sxs-lookup"><span data-stu-id="99cae-353">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99cae-354">Viz také</span><span class="sxs-lookup"><span data-stu-id="99cae-354">See Also</span></span>  
 [<span data-ttu-id="99cae-355">Začínáme</span><span class="sxs-lookup"><span data-stu-id="99cae-355">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="99cae-356">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="99cae-356">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="99cae-357">.NET pro Windows Store apps – přehled</span><span class="sxs-lookup"><span data-stu-id="99cae-357">.NET For Windows Store apps overview</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [<span data-ttu-id="99cae-358">Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="99cae-358">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
