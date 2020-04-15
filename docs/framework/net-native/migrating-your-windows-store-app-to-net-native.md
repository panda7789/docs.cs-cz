---
title: Migrace aplikace pro Windows Store do .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 987669fc51eeaf7e3bdef3e91a2f1ce23164a055
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389705"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a><span data-ttu-id="36464-102">Migrace aplikace pro Windows Store do nativní ho storu .NET</span><span class="sxs-lookup"><span data-stu-id="36464-102">Migrate Your Windows Store App to .NET Native</span></span>

<span data-ttu-id="36464-103">.NET Native poskytuje statickou kompilaci aplikací ve Windows Storu nebo v počítači vývojáře.</span><span class="sxs-lookup"><span data-stu-id="36464-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="36464-104">To se liší od dynamické kompilace prováděné pro aplikace pro Windows Store kompilátorem just-in-time (JIT) nebo [native image generator (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) v zařízení.</span><span class="sxs-lookup"><span data-stu-id="36464-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="36464-105">Navzdory rozdílům se nativní rozhraní .NET snaží zachovat kompatibilitu s [rozhraním .NET pro aplikace pro Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span><span class="sxs-lookup"><span data-stu-id="36464-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span></span> <span data-ttu-id="36464-106">Z větší části věci, které fungují na .NET pro aplikace pro Windows Store také pracovat s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36464-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="36464-107">V některých případech však může dojít ke změnám chování.</span><span class="sxs-lookup"><span data-stu-id="36464-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="36464-108">Tento dokument popisuje tyto rozdíly mezi standardní .NET pro aplikace pro Windows Store a .NET Native v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="36464-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>

- [<span data-ttu-id="36464-109">Obecné rozdíly za běhu</span><span class="sxs-lookup"><span data-stu-id="36464-109">General runtime differences</span></span>](#Runtime)

- [<span data-ttu-id="36464-110">Rozdíly dynamického programování</span><span class="sxs-lookup"><span data-stu-id="36464-110">Dynamic programming differences</span></span>](#Dynamic)

- [<span data-ttu-id="36464-111">Další rozdíly související s reflexí</span><span class="sxs-lookup"><span data-stu-id="36464-111">Other reflection-related differences</span></span>](#Reflection)

- [<span data-ttu-id="36464-112">Nepodporované scénáře a api</span><span class="sxs-lookup"><span data-stu-id="36464-112">Unsupported scenarios and APIs</span></span>](#Unsupported)

- [<span data-ttu-id="36464-113">Rozdíly v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="36464-113">Visual Studio differences</span></span>](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a><span data-ttu-id="36464-114">Obecné rozdíly za běhu</span><span class="sxs-lookup"><span data-stu-id="36464-114">General runtime differences</span></span>

- <span data-ttu-id="36464-115">Výjimky, jako <xref:System.TypeLoadException>je například , které jsou vyvolány kompilátorem JIT při spuštění aplikace na clr (COMMON Language) obecně za následek chyby v době kompilace při zpracování .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36464-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>

- <span data-ttu-id="36464-116">Nevolejte metodu <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> z vlákna uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="36464-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="36464-117">To může mít za následek zablokování na .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36464-117">This can result in a deadlock on .NET Native.</span></span>

- <span data-ttu-id="36464-118">Nespoléhejte na statické třídy konstruktoru vyvolání řazení.</span><span class="sxs-lookup"><span data-stu-id="36464-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="36464-119">V .NET Native pořadí vyvolání se liší od pořadí na standardní runtime.</span><span class="sxs-lookup"><span data-stu-id="36464-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="36464-120">(I při standardním běhu za běhu byste neměli spoléhat na pořadí provádění konstruktorů statické třídy.)</span><span class="sxs-lookup"><span data-stu-id="36464-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>

- <span data-ttu-id="36464-121">Nekonečné opakování bez volání `while(true);`(například) v libovolném vlákně může zastavit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="36464-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="36464-122">Podobně velké nebo nekonečné čekání může zastavit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="36464-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>

- <span data-ttu-id="36464-123">Některé obecné inicializační cykly nevyvolání výjimky v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36464-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="36464-124">Například následující kód vyvolá <xref:System.TypeLoadException> výjimku na standardní CLR.</span><span class="sxs-lookup"><span data-stu-id="36464-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="36464-125">V .NET Native, není.</span><span class="sxs-lookup"><span data-stu-id="36464-125">In .NET Native, it doesn't.</span></span>

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- <span data-ttu-id="36464-126">V některých případech .NET Native poskytuje různé implementace knihoven tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36464-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="36464-127">Objekt vrácený z metody bude vždy implementovat členy vráceného typu.</span><span class="sxs-lookup"><span data-stu-id="36464-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="36464-128">Však vzhledem k tomu, že jeho zálohování implementace je jiný, nemusí být možné přetypovat do stejné sady typů, jako byste mohli na jiných platformách rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36464-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="36464-129">Například v některých případech nemusí být možné <xref:System.Collections.Generic.IEnumerable%601> přetypovat objekt <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> rozhraní <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> `T[]`vrácené metody, jako je například nebo na .</span><span class="sxs-lookup"><span data-stu-id="36464-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>

- <span data-ttu-id="36464-130">Mezipaměť WinInet není ve výchozím nastavení povolena v rozhraní .NET pro aplikace pro Windows Store, ale je na nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="36464-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="36464-131">To zlepšuje výkon, ale má pracovní sadu důsledky.</span><span class="sxs-lookup"><span data-stu-id="36464-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="36464-132">Není nutná žádná akce vývojáře.</span><span class="sxs-lookup"><span data-stu-id="36464-132">No developer action is necessary.</span></span>

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a><span data-ttu-id="36464-133">Rozdíly dynamického programování</span><span class="sxs-lookup"><span data-stu-id="36464-133">Dynamic programming differences</span></span>

<span data-ttu-id="36464-134">.NET Native staticky odkazy v kódu z rozhraní .NET Framework, aby kód aplikace místní pro maximální výkon.</span><span class="sxs-lookup"><span data-stu-id="36464-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="36464-135">Binární velikosti však musí zůstat malé, takže nelze dovést celý rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36464-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="36464-136">Nativní kompilátor .NET řeší toto omezení pomocí reduktoru závislostí, který odebere odkazy na nepoužívaný kód.</span><span class="sxs-lookup"><span data-stu-id="36464-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="36464-137">Nativní .NET však nemusí udržovat nebo generovat některé informace o typu a kód, pokud tyto informace nelze odvodit staticky v době kompilace, ale místo toho je načten dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="36464-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>

<span data-ttu-id="36464-138">Nativní rozhraní .NET umožňuje reflexi a dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="36464-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="36464-139">Však ne všechny typy mohou být označeny pro reflexi, protože by to generované velikostkódu příliš velké (zejména proto, že odráží na veřejné rozhraní API v rozhraní .NET Framework je podporována).</span><span class="sxs-lookup"><span data-stu-id="36464-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="36464-140">Nativní kompilátor .NET provádí inteligentní volby o tom, které typy by měly podporovat reflexi a udržuje metadata a generuje kód pouze pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="36464-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>

<span data-ttu-id="36464-141">Například datová vazba vyžaduje, aby aplikace mohla mapovat názvy vlastností na funkce.</span><span class="sxs-lookup"><span data-stu-id="36464-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="36464-142">V rozhraní .NET pro aplikace pro Windows Store používá běžný jazykový běh automaticky reflexe k poskytování této funkce pro spravované typy a veřejně dostupné nativní typy.</span><span class="sxs-lookup"><span data-stu-id="36464-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="36464-143">V nativním rozhraní .NET kompilátor automaticky obsahuje metadata pro typy, ke kterým vázáte data.</span><span class="sxs-lookup"><span data-stu-id="36464-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>

<span data-ttu-id="36464-144">Kompilátor .NET Native může také zpracovávat <xref:System.Collections.Generic.List%601> běžně <xref:System.Collections.Generic.Dictionary%602>používané obecné typy, jako jsou a , které fungují bez nutnosti jakékoli rady nebo direktivy.</span><span class="sxs-lookup"><span data-stu-id="36464-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="36464-145">Klíčové slovo [dynamické](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) je také podporováno v určitých mezích.</span><span class="sxs-lookup"><span data-stu-id="36464-145">The [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) keyword is also supported within certain limits.</span></span>

> [!NOTE]
> <span data-ttu-id="36464-146">Při přenosu aplikace do nativního rozhraní .NET byste měli důkladně otestovat všechny cesty dynamického kódu.</span><span class="sxs-lookup"><span data-stu-id="36464-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>

<span data-ttu-id="36464-147">Výchozí konfigurace pro .NET Native je dostatečná pro většinu vývojářů, ale někteří vývojáři mohou chtít doladit své konfigurace pomocí souboru direktiv runtime (.rd.xml).</span><span class="sxs-lookup"><span data-stu-id="36464-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="36464-148">Kromě toho v některých případech kompilátor .NET Native není schopen určit, která metadata musí být k dispozici pro reflexi a spoléhá na rady, zejména v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="36464-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>

- <span data-ttu-id="36464-149">Některé konstrukce <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> jako <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> a nelze určit staticky.</span><span class="sxs-lookup"><span data-stu-id="36464-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>

- <span data-ttu-id="36464-150">Vzhledem k tomu, že kompilátor nemůže určit instance, obecný typ, který chcete uvažovat, musí být určen direktivy za běhu.</span><span class="sxs-lookup"><span data-stu-id="36464-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="36464-151">Není to jen proto, že musí být zahrnut veškerý kód, ale protože reflexe obecných typů může tvořit nekonečný cyklus (například když je obecná metoda vyvolána u obecného typu).</span><span class="sxs-lookup"><span data-stu-id="36464-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>

> [!NOTE]
> <span data-ttu-id="36464-152">Direktivy runtime jsou definovány v souboru direktiv runtime (.rd.xml).</span><span class="sxs-lookup"><span data-stu-id="36464-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="36464-153">Obecné informace o použití tohoto souboru naleznete v [tématu Začínáme](getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="36464-153">For general information about using this file, see [Getting Started](getting-started-with-net-native.md).</span></span> <span data-ttu-id="36464-154">Informace o direktivách runtime naleznete v [tématu Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="36464-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>

<span data-ttu-id="36464-155">.NET Native také obsahuje profilovací nástroje, které pomáhají vývojáři určit, které typy mimo výchozí sadu by měly podporovat reflexi.</span><span class="sxs-lookup"><span data-stu-id="36464-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a><span data-ttu-id="36464-156">Další rozdíly související s reflexí</span><span class="sxs-lookup"><span data-stu-id="36464-156">Other reflection-related differences</span></span>

<span data-ttu-id="36464-157">Existuje řada dalších rozdílů v chování souvisejících s odrazem mezi rozhraním .NET pro aplikace pro Windows Store a nativním rozhraním .NET.</span><span class="sxs-lookup"><span data-stu-id="36464-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>

<span data-ttu-id="36464-158">V nativním rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="36464-158">In .NET Native:</span></span>

- <span data-ttu-id="36464-159">Privátní reflexe nad typy a členy v knihovně tříd rozhraní .NET Framework není podporována.</span><span class="sxs-lookup"><span data-stu-id="36464-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="36464-160">Můžete však uvažovat o vlastních soukromých typech a členech, stejně jako o typech a členech v knihovnách třetích stran.</span><span class="sxs-lookup"><span data-stu-id="36464-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>

- <span data-ttu-id="36464-161">Vlastnost <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> správně `false` vrátí <xref:System.Reflection.ParameterInfo> pro objekt, který představuje vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="36464-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="36464-162">V rozhraní .NET pro aplikace `true`pro Windows Store vrátí .</span><span class="sxs-lookup"><span data-stu-id="36464-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="36464-163">Zprostředkující jazyk (IL) nepodporuje přímo a tlumočení je ponecháno na jazyku.</span><span class="sxs-lookup"><span data-stu-id="36464-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>

- <span data-ttu-id="36464-164">Veřejné členy <xref:System.RuntimeFieldHandle> na <xref:System.RuntimeMethodHandle> a struktury nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="36464-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="36464-165">Tyto typy jsou podporovány pouze pro LINQ, stromy výrazů a inicializaci statického pole.</span><span class="sxs-lookup"><span data-stu-id="36464-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>

- <span data-ttu-id="36464-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType>a <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> zahrnout skryté členy do základních tříd a proto mohou být přepsány bez explicitních přepsání.</span><span class="sxs-lookup"><span data-stu-id="36464-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="36464-167">To platí také pro jiné metody [RuntimeReflectionExtensions.GetRuntime\*.](xref:System.Reflection.RuntimeReflectionExtensions)</span><span class="sxs-lookup"><span data-stu-id="36464-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>

- <span data-ttu-id="36464-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>a <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> neselhat při pokusu o vytvoření určité kombinace `byref` (například pole objektů).</span><span class="sxs-lookup"><span data-stu-id="36464-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of `byref` objects).</span></span>

- <span data-ttu-id="36464-169">Reflexe nelze použít k vyvolání členů, které mají parametry ukazatele.</span><span class="sxs-lookup"><span data-stu-id="36464-169">You can't use reflection to invoke members that have pointer parameters.</span></span>

- <span data-ttu-id="36464-170">Odraz nelze použít k získání nebo nastavení pole ukazatele.</span><span class="sxs-lookup"><span data-stu-id="36464-170">You can't use reflection to get or set a pointer field.</span></span>

- <span data-ttu-id="36464-171">Pokud je počet argumentů chybný a typ jednoho z argumentů je <xref:System.ArgumentException> nesprávný, nativní .NET vyvolá místo <xref:System.Reflection.TargetParameterCountException>.</span><span class="sxs-lookup"><span data-stu-id="36464-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>

- <span data-ttu-id="36464-172">Binární serializace výjimek není obecně podporována.</span><span class="sxs-lookup"><span data-stu-id="36464-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="36464-173">V důsledku toho mohou být do slovníku <xref:System.Exception.Data%2A?displayProperty=nameWithType> přidány neserializovatelné objekty.</span><span class="sxs-lookup"><span data-stu-id="36464-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="36464-174">Nepodporované scénáře a api</span><span class="sxs-lookup"><span data-stu-id="36464-174">Unsupported scenarios and APIs</span></span>

<span data-ttu-id="36464-175">V následujících částech jsou uvedeny nepodporované scénáře a api pro obecný vývoj, interop a technologie, jako je httpclient a Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="36464-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>

- [<span data-ttu-id="36464-176">Obecný vývoj</span><span class="sxs-lookup"><span data-stu-id="36464-176">General development</span></span>](#General)

- [<span data-ttu-id="36464-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="36464-177">HttpClient</span></span>](#HttpClient)

- [<span data-ttu-id="36464-178">Interop</span><span class="sxs-lookup"><span data-stu-id="36464-178">Interop</span></span>](#Interop)

- [<span data-ttu-id="36464-179">Nepodporovaná api</span><span class="sxs-lookup"><span data-stu-id="36464-179">Unsupported APIs</span></span>](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a><span data-ttu-id="36464-180">Obecné rozdíly ve vývoji</span><span class="sxs-lookup"><span data-stu-id="36464-180">General development differences</span></span>

<span data-ttu-id="36464-181">**Typy hodnot**</span><span class="sxs-lookup"><span data-stu-id="36464-181">**Value types**</span></span>

- <span data-ttu-id="36464-182">Pokud přepíšete <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody a pro typ hodnoty, nevolejte implementace základní třídy.</span><span class="sxs-lookup"><span data-stu-id="36464-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="36464-183">V rozhraní .NET pro aplikace pro Windows Store tyto metody spoléhají na reflexi.</span><span class="sxs-lookup"><span data-stu-id="36464-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="36464-184">V době kompilace .NET Native generuje implementaci, která nespoléhá na odraz za běhu.</span><span class="sxs-lookup"><span data-stu-id="36464-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="36464-185">To znamená, že pokud tyto dvě metody nepřepíšete, budou fungovat podle očekávání, protože nativní rozhraní .NET generuje implementaci v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="36464-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="36464-186">Však přepsání těchto metod, ale volání implementace základní třídy výsledky výjimky.</span><span class="sxs-lookup"><span data-stu-id="36464-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>

- <span data-ttu-id="36464-187">Typy hodnot větší než 1 MB nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="36464-187">Value types larger than 1 megabyte aren't supported.</span></span>

- <span data-ttu-id="36464-188">Typy hodnot nemůže mít konstruktor bez parametrů v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36464-188">Value types can't have a parameterless constructor in .NET Native.</span></span> <span data-ttu-id="36464-189">(C# a Visual Basic zakázat konstruktory bez parametrů na typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="36464-189">(C# and Visual Basic prohibit parameterless constructors on value types.</span></span> <span data-ttu-id="36464-190">Ty však mohou být vytvořeny v IL.)</span><span class="sxs-lookup"><span data-stu-id="36464-190">However, these can be created in IL.)</span></span>

<span data-ttu-id="36464-191">**Pole**</span><span class="sxs-lookup"><span data-stu-id="36464-191">**Arrays**</span></span>

- <span data-ttu-id="36464-192">Pole s nižší mezí než nula nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="36464-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="36464-193">Obvykle tato pole jsou vytvořeny voláním <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> přetížení.</span><span class="sxs-lookup"><span data-stu-id="36464-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

- <span data-ttu-id="36464-194">Dynamické vytváření vícerozměrných polí není podporováno.</span><span class="sxs-lookup"><span data-stu-id="36464-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="36464-195">Tato pole jsou obvykle vytvořeny voláním <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> přetížení metody, `lengths` která obsahuje parametr, nebo voláním <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="36464-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="36464-196">Vícerozměrná pole, která mají čtyři nebo více dimenzí, nejsou podporována; to znamená, <xref:System.Array.Rank%2A?displayProperty=nameWithType> že jejich hodnota vlastnosti je čtyři nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="36464-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="36464-197">Místo toho použijte [zubaté pole](../../csharp/programming-guide/arrays/jagged-arrays.md) (pole polí).</span><span class="sxs-lookup"><span data-stu-id="36464-197">Use [jagged arrays](../../csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="36464-198">Například `array[x,y,z]` je neplatný, ale `array[x][y][z]` není.</span><span class="sxs-lookup"><span data-stu-id="36464-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>

- <span data-ttu-id="36464-199">Odchylka pro vícerozměrná pole není podporována a způsobuje výjimku <xref:System.InvalidCastException> za běhu.</span><span class="sxs-lookup"><span data-stu-id="36464-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>

<span data-ttu-id="36464-200">**Obecné typy**</span><span class="sxs-lookup"><span data-stu-id="36464-200">**Generics**</span></span>

- <span data-ttu-id="36464-201">Nekonečné rozšíření obecného typu má za následek chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="36464-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="36464-202">Například tento kód se nepodaří zkompilovat:</span><span class="sxs-lookup"><span data-stu-id="36464-202">For example, this code fails to compile:</span></span>

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

<span data-ttu-id="36464-203">**Ukazatele**</span><span class="sxs-lookup"><span data-stu-id="36464-203">**Pointers**</span></span>

- <span data-ttu-id="36464-204">Pole ukazatelů nejsou podporována.</span><span class="sxs-lookup"><span data-stu-id="36464-204">Arrays of pointers aren't supported.</span></span>

- <span data-ttu-id="36464-205">Odraz nelze použít k získání nebo nastavení pole ukazatele.</span><span class="sxs-lookup"><span data-stu-id="36464-205">You can't use reflection to get or set a pointer field.</span></span>

<span data-ttu-id="36464-206">**Serializace**</span><span class="sxs-lookup"><span data-stu-id="36464-206">**Serialization**</span></span>

<span data-ttu-id="36464-207">Atribut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> není podporován.</span><span class="sxs-lookup"><span data-stu-id="36464-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="36464-208">Místo <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> toho použijte atribut.</span><span class="sxs-lookup"><span data-stu-id="36464-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>

<span data-ttu-id="36464-209">**Materiály**</span><span class="sxs-lookup"><span data-stu-id="36464-209">**Resources**</span></span>

<span data-ttu-id="36464-210">Použití lokalizovaných prostředků <xref:System.Diagnostics.Tracing.EventSource> s třídou není podporováno.</span><span class="sxs-lookup"><span data-stu-id="36464-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="36464-211">Vlastnost <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> nedefinuje lokalizované prostředky.</span><span class="sxs-lookup"><span data-stu-id="36464-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>

<span data-ttu-id="36464-212">**Delegáty**</span><span class="sxs-lookup"><span data-stu-id="36464-212">**Delegates**</span></span>

<span data-ttu-id="36464-213">`Delegate.BeginInvoke`a `Delegate.EndInvoke` nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="36464-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>

<span data-ttu-id="36464-214">**Ostatní rozhraní API**</span><span class="sxs-lookup"><span data-stu-id="36464-214">**Miscellaneous APIs**</span></span>

- <span data-ttu-id="36464-215">Vlastnost [TypeInfo.GUID](xref:System.Type.GUID) vyvolá <xref:System.PlatformNotSupportedException> výjimku, <xref:System.Runtime.InteropServices.GuidAttribute> pokud atribut není použit pro typ.</span><span class="sxs-lookup"><span data-stu-id="36464-215">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="36464-216">Identifikátor GUID se používá především pro podporu com.</span><span class="sxs-lookup"><span data-stu-id="36464-216">The GUID is used primarily for COM support.</span></span>

- <span data-ttu-id="36464-217">Metoda <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> správně analyzuje řetězce, které obsahují krátká data v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36464-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="36464-218">Nezachovává však kompatibilitu se změnami analýzy data a času popsanými v článcích znalostní báze [KB2803771](https://support.microsoft.com/kb/2803771) a [KB2803755](https://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="36464-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>

- <span data-ttu-id="36464-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")` je správně zaokrouhlena v nativním rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="36464-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="36464-220">V některých verzích CLR je výsledný řetězec zkrácen namísto zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="36464-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a><span data-ttu-id="36464-221">Rozdíly mezi klienty HttpClient</span><span class="sxs-lookup"><span data-stu-id="36464-221">HttpClient differences</span></span>

<span data-ttu-id="36464-222">V .NET Native <xref:System.Net.Http.HttpClientHandler> třída interně používá WinINet (prostřednictvím <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> třídy) namísto <xref:System.Net.WebRequest> třídy a <xref:System.Net.WebResponse> používané ve standardním rozhraní .NET pro aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="36464-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="36464-223">WinINet nepodporuje všechny možnosti konfigurace, které <xref:System.Net.Http.HttpClientHandler> třída podporuje.</span><span class="sxs-lookup"><span data-stu-id="36464-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="36464-224">Výsledek:</span><span class="sxs-lookup"><span data-stu-id="36464-224">As a result:</span></span>

- <span data-ttu-id="36464-225">Některé vlastnosti schopností <xref:System.Net.Http.HttpClientHandler> `false` při návratu na .NET `true` Native, zatímco se vrátí ve standardní .NET pro aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="36464-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>

- <span data-ttu-id="36464-226">Některé přistupující objekty vlastností `get` konfigurace vždy vrátí pevnou hodnotu na .NET Native, která se liší od výchozí konfigurovatelné hodnoty v rozhraní .NET pro aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="36464-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>

<span data-ttu-id="36464-227">Některé další rozdíly chování jsou zahrnuty v následujících podsekcích.</span><span class="sxs-lookup"><span data-stu-id="36464-227">Some additional behavior differences are covered in the following subsections.</span></span>

<span data-ttu-id="36464-228">**Proxy server**</span><span class="sxs-lookup"><span data-stu-id="36464-228">**Proxy**</span></span>

<span data-ttu-id="36464-229">Třída <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> nepodporuje konfiguraci nebo přepsání proxy serveru na základě požadavku.</span><span class="sxs-lookup"><span data-stu-id="36464-229">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="36464-230">To znamená, že všechny požadavky na .NET Native používají systémově nakonfigurovaný <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> proxy server nebo žádný proxy server, v závislosti na hodnotě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="36464-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="36464-231">V rozhraní .NET pro aplikace pro Windows <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> Store je proxy server definován vlastností.</span><span class="sxs-lookup"><span data-stu-id="36464-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="36464-232">Na .NET Native, <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> nastavení na `null` hodnotu <xref:System.PlatformNotSupportedException> jinou než vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="36464-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="36464-233">Vlastnost <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> vrátí `false` na .NET Native, `true` vzhledem k tomu, že se vrátí ve standardním rozhraní .NET Framework pro aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="36464-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>

<span data-ttu-id="36464-234">**Automatické přesměrování**</span><span class="sxs-lookup"><span data-stu-id="36464-234">**Automatic redirection**</span></span>

<span data-ttu-id="36464-235">Třída <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> neumožňuje konfiguraci maximálního počtu automatických přesměrování.</span><span class="sxs-lookup"><span data-stu-id="36464-235">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="36464-236">Hodnota vlastnosti <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> je ve výchozím nastavení 50 ve standardní mj.</span><span class="sxs-lookup"><span data-stu-id="36464-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="36464-237">Na .NET Native hodnota této vlastnosti je 10 a pokus <xref:System.PlatformNotSupportedException> u jeho změny vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="36464-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="36464-238">Vlastnost <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> vrátí `false` na .NET Native, `true` vzhledem k tomu, že se vrátí v .NET pro aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="36464-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>

<span data-ttu-id="36464-239">**Automatická dekomprese**</span><span class="sxs-lookup"><span data-stu-id="36464-239">**Automatic decompression**</span></span>

<span data-ttu-id="36464-240">Rozhraní .NET pro aplikace pro <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> Windows <xref:System.Net.DecompressionMethods.Deflate>Store <xref:System.Net.DecompressionMethods.GZip>umožňuje <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>nastavit <xref:System.Net.DecompressionMethods.None>vlastnost na , , jak nebo .</span><span class="sxs-lookup"><span data-stu-id="36464-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="36464-241">Nativní rozhraní <xref:System.Net.DecompressionMethods.Deflate> .NET <xref:System.Net.DecompressionMethods.GZip>podporuje <xref:System.Net.DecompressionMethods.None>pouze společně s rozhraním . nebo .</span><span class="sxs-lookup"><span data-stu-id="36464-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="36464-242">Pokuso o <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> nastavení <xref:System.Net.DecompressionMethods.Deflate> vlastnosti buď nebo <xref:System.Net.DecompressionMethods.GZip> samostatně <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>tiše nastaví na obě a .</span><span class="sxs-lookup"><span data-stu-id="36464-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>

<span data-ttu-id="36464-243">**Soubory cookie**</span><span class="sxs-lookup"><span data-stu-id="36464-243">**Cookies**</span></span>

<span data-ttu-id="36464-244">Zpracování souborů cookie se <xref:System.Net.Http.HttpClient> provádí současně a WinINet.</span><span class="sxs-lookup"><span data-stu-id="36464-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="36464-245">Cookies z <xref:System.Net.CookieContainer> těchto souborů jsou kombinovány se soubory cookie v mezipaměti souborů cookie WinINet.</span><span class="sxs-lookup"><span data-stu-id="36464-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="36464-246">Odebrání souboru <xref:System.Net.CookieContainer> cookie <xref:System.Net.Http.HttpClient> z brání odeslání souboru cookie, ale pokud soubor cookie byl již vidět WinINet, a soubory cookie nebyly odstraněny uživatelem, WinINet odešle.</span><span class="sxs-lookup"><span data-stu-id="36464-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="36464-247">Není možné programově odebrat soubor cookie z WinINet <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClientHandler>pomocí <xref:System.Net.CookieContainer> rozhraní , nebo API.</span><span class="sxs-lookup"><span data-stu-id="36464-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="36464-248">Nastavení <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> vlastnosti `false` způsobí <xref:System.Net.Http.HttpClient> pouze zastavit odesílání souborů cookie; WinINet může stále obsahovat své cookies v žádosti.</span><span class="sxs-lookup"><span data-stu-id="36464-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>

<span data-ttu-id="36464-249">**Přihlašovací údaje**</span><span class="sxs-lookup"><span data-stu-id="36464-249">**Credentials**</span></span>

<span data-ttu-id="36464-250">V rozhraní .NET pro <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> aplikace <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> pro Windows Store fungují vlastnosti a vlastnosti nezávisle.</span><span class="sxs-lookup"><span data-stu-id="36464-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="36464-251">Navíc <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost přijímá libovolný objekt, který <xref:System.Net.ICredentials> implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36464-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="36464-252">V nativní .NET <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> nastavení `true` vlastnosti způsobí, že <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost stane `null`.</span><span class="sxs-lookup"><span data-stu-id="36464-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="36464-253">Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> lze vlastnost nastavit `null`pouze <xref:System.Net.CredentialCache.DefaultCredentials%2A>na , nebo <xref:System.Net.NetworkCredential>objekt typu .</span><span class="sxs-lookup"><span data-stu-id="36464-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="36464-254">Přiřazení jakýkoli <xref:System.Net.ICredentials> jiný objekt, nejoblíbenější z <xref:System.Net.CredentialCache>nich <xref:System.Net.Http.HttpClientHandler.Credentials%2A> je , <xref:System.PlatformNotSupportedException>vlastnost hází .</span><span class="sxs-lookup"><span data-stu-id="36464-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="36464-255">**Jiné nepodporované nebo nekonfigurovatelné funkce**</span><span class="sxs-lookup"><span data-stu-id="36464-255">**Other unsupported or unconfigurable features**</span></span>

<span data-ttu-id="36464-256">V nativním rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="36464-256">In .NET Native:</span></span>

- <span data-ttu-id="36464-257">Hodnota vlastnosti <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> je <xref:System.Net.Http.ClientCertificateOption.Automatic>vždy .</span><span class="sxs-lookup"><span data-stu-id="36464-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="36464-258">V rozhraní .NET pro aplikace <xref:System.Net.Http.ClientCertificateOption.Manual>pro Windows Store je výchozí hodnota .</span><span class="sxs-lookup"><span data-stu-id="36464-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>

- <span data-ttu-id="36464-259">Vlastnost <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> není konfigurovatelná.</span><span class="sxs-lookup"><span data-stu-id="36464-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>

- <span data-ttu-id="36464-260">Vlastnost <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> je `true`vždy .</span><span class="sxs-lookup"><span data-stu-id="36464-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="36464-261">V rozhraní .NET pro aplikace `false`pro Windows Store je výchozí hodnota .</span><span class="sxs-lookup"><span data-stu-id="36464-261">In .NET for Windows Store apps, the default is `false`.</span></span>

- <span data-ttu-id="36464-262">Záhlaví `SetCookie2` v odpovědích je ignorováno jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="36464-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>

<a name="Interop"></a>
### <a name="interop-differences"></a><span data-ttu-id="36464-263">Interop rozdíly</span><span class="sxs-lookup"><span data-stu-id="36464-263">Interop differences</span></span>
 <span data-ttu-id="36464-264">**Zastaralá api**</span><span class="sxs-lookup"><span data-stu-id="36464-264">**Deprecated APIs**</span></span>

 <span data-ttu-id="36464-265">Počet zřídka používaných api pro interoperabilitu se spravovaným kódem byly zastaralé.</span><span class="sxs-lookup"><span data-stu-id="36464-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="36464-266">Při použití s .NET Native, tato <xref:System.NotImplementedException> <xref:System.PlatformNotSupportedException> rozhraní API může vyvolat nebo výjimku nebo způsobit chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="36464-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="36464-267">V rozhraní .NET pro aplikace pro Windows Store jsou tato rozhraní API označena jako zastaralá, i když jejich volání generuje upozornění kompilátoru spíše než chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="36464-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>

 <span data-ttu-id="36464-268">Zastaralá api pro `VARIANT` zařazování zahrnují:</span><span class="sxs-lookup"><span data-stu-id="36464-268">Deprecated APIs for `VARIANT` marshaling include:</span></span>

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <span data-ttu-id="36464-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>je podporována, ale vyvolá výjimku v některých scénářích, například při použití s [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) nebo `byref` varianty.</span><span class="sxs-lookup"><span data-stu-id="36464-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or `byref` variants.</span></span>

 <span data-ttu-id="36464-270">Mezi zastaralá api pro podporu [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) patří:</span><span class="sxs-lookup"><span data-stu-id="36464-270">Deprecated APIs for [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

<span data-ttu-id="36464-271">Mezi zastaralá api pro klasické události COM patří:</span><span class="sxs-lookup"><span data-stu-id="36464-271">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<span data-ttu-id="36464-272">Zastaralá rozhraní API <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> v rozhraní, která nejsou v nativním rozhraní .NET podporována, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="36464-272">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>

- <span data-ttu-id="36464-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="36464-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="36464-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="36464-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="36464-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="36464-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

<span data-ttu-id="36464-276">Mezi další nepodporované funkce interop patří:</span><span class="sxs-lookup"><span data-stu-id="36464-276">Other unsupported interop features include:</span></span>

- <span data-ttu-id="36464-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="36464-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="36464-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="36464-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 <span data-ttu-id="36464-279">Zřídka používané zařazování API:</span><span class="sxs-lookup"><span data-stu-id="36464-279">Rarely used marshaling APIs:</span></span>

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

 <span data-ttu-id="36464-280">**Vyvolání platformy a kompatibilita interopu COM**</span><span class="sxs-lookup"><span data-stu-id="36464-280">**Platform invoke and COM interop compatibility**</span></span>

 <span data-ttu-id="36464-281">Většina scénářů vyvolání platformy a interop com jsou stále podporovány v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36464-281">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="36464-282">Zejména je podporována veškerá interoperabilita s windows runtime (WinRT) API a všechny zařazování požadované pro prostředí Windows Runtime je podporována.</span><span class="sxs-lookup"><span data-stu-id="36464-282">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="36464-283">To zahrnuje zařazování podporu pro:</span><span class="sxs-lookup"><span data-stu-id="36464-283">This includes marshaling support for:</span></span>

- <span data-ttu-id="36464-284">Pole (včetně <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="36464-284">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>

- `BStr`

- <span data-ttu-id="36464-285">Delegáty</span><span class="sxs-lookup"><span data-stu-id="36464-285">Delegates</span></span>

- <span data-ttu-id="36464-286">Řetězce (Unicode, Ansi a HSTRING)</span><span class="sxs-lookup"><span data-stu-id="36464-286">Strings (Unicode, Ansi, and HSTRING)</span></span>

- <span data-ttu-id="36464-287">Structs`byref` ( `byval`a )</span><span class="sxs-lookup"><span data-stu-id="36464-287">Structs (`byref` and `byval`)</span></span>

- <span data-ttu-id="36464-288">Sjednocení</span><span class="sxs-lookup"><span data-stu-id="36464-288">Unions</span></span>

- <span data-ttu-id="36464-289">Popisovače Win32</span><span class="sxs-lookup"><span data-stu-id="36464-289">Win32 handles</span></span>

- <span data-ttu-id="36464-290">Všechny konstrukce WinRT</span><span class="sxs-lookup"><span data-stu-id="36464-290">All WinRT constructs</span></span>

- <span data-ttu-id="36464-291">Částečná podpora pro zařazování typů variant.</span><span class="sxs-lookup"><span data-stu-id="36464-291">Partial support for marshaling variant types.</span></span> <span data-ttu-id="36464-292">Podporované systémy:</span><span class="sxs-lookup"><span data-stu-id="36464-292">The following are supported:</span></span>

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

  - [<span data-ttu-id="36464-293">IUnknown</span><span class="sxs-lookup"><span data-stu-id="36464-293">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

<span data-ttu-id="36464-294">Nativní rozhraní .NET však nepodporuje následující:</span><span class="sxs-lookup"><span data-stu-id="36464-294">However, .NET Native doesn't support the following:</span></span>

- <span data-ttu-id="36464-295">Použití klasických událostí com</span><span class="sxs-lookup"><span data-stu-id="36464-295">Using classic COM events</span></span>

- <span data-ttu-id="36464-296">Implementace rozhraní <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> spravovaného typu</span><span class="sxs-lookup"><span data-stu-id="36464-296">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>

- <span data-ttu-id="36464-297">Implementace rozhraní [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) na spravovaném <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> typu prostřednictvím atributu.</span><span class="sxs-lookup"><span data-stu-id="36464-297">Implementing the [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="36464-298">Nelze však volat objekty `IDispatch`COM prostřednictvím aplikace a `IDispatch`spravovaný objekt nelze implementovat .</span><span class="sxs-lookup"><span data-stu-id="36464-298">However, you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>

<span data-ttu-id="36464-299">Použití reflexe k vyvolání metody vyvolání platformy není podporováno.</span><span class="sxs-lookup"><span data-stu-id="36464-299">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="36464-300">Toto omezení můžete obejít zabalením volání metody v jiné metodě a pomocí reflexe místo toho volat obálku.</span><span class="sxs-lookup"><span data-stu-id="36464-300">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="36464-301">Další rozdíly oproti rozhraním API .NET pro aplikace pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="36464-301">Other differences from .NET APIs for Windows Store apps</span></span>

<span data-ttu-id="36464-302">V této části jsou uvedeny zbývající rozhraní API, která nejsou podporována v nativním rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="36464-302">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="36464-303">Největší sada nepodporovaných api je Windows Communication Foundation (WCF) API.</span><span class="sxs-lookup"><span data-stu-id="36464-303">The largest set of the unsupported APIs is the Windows Communication Foundation (WCF) APIs.</span></span>

<span data-ttu-id="36464-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="36464-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>

<span data-ttu-id="36464-305">Typy v <xref:System.ComponentModel.DataAnnotations> oborech názvů a <xref:System.ComponentModel.DataAnnotations.Schema> nejsou v nativním rozhraní .NET podporovány.</span><span class="sxs-lookup"><span data-stu-id="36464-305">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="36464-306">Patří mezi ně následující typy, které jsou k dispozici v rozhraní .NET pro aplikace pro Windows Store pro Windows 8:</span><span class="sxs-lookup"><span data-stu-id="36464-306">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>

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

 <span data-ttu-id="36464-307">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="36464-307">**Visual Basic**</span></span>

<span data-ttu-id="36464-308">Visual Basic není aktuálně podporován v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36464-308">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="36464-309">Následující typy v <xref:Microsoft.VisualBasic> <xref:Microsoft.VisualBasic.CompilerServices> oborech názvů a nejsou v nativním rozhraní .NET k dispozici:</span><span class="sxs-lookup"><span data-stu-id="36464-309">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>

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

<span data-ttu-id="36464-310">**Kontext reflexe (system.reflection.context obor názvů)**</span><span class="sxs-lookup"><span data-stu-id="36464-310">**Reflection Context (System.Reflection.Context namespace)**</span></span>

<span data-ttu-id="36464-311">Třída <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> není podporována v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36464-311">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>

<span data-ttu-id="36464-312">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="36464-312">**RTC (System.Net.Http.Rtc)**</span></span>

<span data-ttu-id="36464-313">Třída `System.Net.Http.RtcRequestFactory` není podporována v .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36464-313">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>

<span data-ttu-id="36464-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="36464-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>

<span data-ttu-id="36464-315">Typy v [oborech názvů System.ServiceModel.\*](xref:System.ServiceModel) nejsou v nativním rozhraní .NET podporovány.</span><span class="sxs-lookup"><span data-stu-id="36464-315">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="36464-316">Patří mezi ně následující typy:</span><span class="sxs-lookup"><span data-stu-id="36464-316">These include the following types:</span></span>

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

### <a name="differences-in-serializers"></a><span data-ttu-id="36464-317">Rozdíly v serializátorech</span><span class="sxs-lookup"><span data-stu-id="36464-317">Differences in serializers</span></span>

<span data-ttu-id="36464-318">Následující rozdíly se týkají serializace a <xref:System.Runtime.Serialization.DataContractSerializer>deserializace pomocí , <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>a <xref:System.Xml.Serialization.XmlSerializer> tříd:</span><span class="sxs-lookup"><span data-stu-id="36464-318">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>

- <span data-ttu-id="36464-319">V .NET <xref:System.Runtime.Serialization.DataContractSerializer> Native <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a nepodaří serializovat nebo rekonstruovat odvozenou třídu, která má člen základní třídy, jehož typ není typ kořenové serializace.</span><span class="sxs-lookup"><span data-stu-id="36464-319">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="36464-320">Například v následujícím kódu, pokus o serializaci nebo `Y` deserializovat má za následek chybu:</span><span class="sxs-lookup"><span data-stu-id="36464-320">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  <span data-ttu-id="36464-321">Typ `InnerType` není znám serializátoru, protože členy základní třídy nejsou provázány během serializace.</span><span class="sxs-lookup"><span data-stu-id="36464-321">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>

- <span data-ttu-id="36464-322"><xref:System.Runtime.Serialization.DataContractSerializer>a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nepodaří serializovat třídu nebo strukturu, která implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36464-322"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="36464-323">Například následující typy se nezdaří serializovat nebo rekonstruovat:</span><span class="sxs-lookup"><span data-stu-id="36464-323">For example, the following types fail to serialize or deserialize:</span></span>

- <span data-ttu-id="36464-324"><xref:System.Xml.Serialization.XmlSerializer>nepodaří serializovat následující hodnotu objektu, protože nezná přesný typ objektu, který má být serializován:</span><span class="sxs-lookup"><span data-stu-id="36464-324"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>

- <span data-ttu-id="36464-325"><xref:System.Xml.Serialization.XmlSerializer>nepodaří serializovat nebo rekonstruovat, pokud je <xref:System.Xml.XmlQualifiedName>typ serializovaného objektu .</span><span class="sxs-lookup"><span data-stu-id="36464-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>

- <span data-ttu-id="36464-326">Všechny serializátory <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>( <xref:System.Xml.Serialization.XmlSerializer><xref:System.Runtime.Serialization.DataContractSerializer>, , a ) <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> nepodaří generovat kód <xref:System.Xml.Linq.XElement>serializace pro typ nebo pro typ, který obsahuje .</span><span class="sxs-lookup"><span data-stu-id="36464-326">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="36464-327">Místo toho zobrazují chyby v době sestavení.</span><span class="sxs-lookup"><span data-stu-id="36464-327">They display build-time errors instead.</span></span>

- <span data-ttu-id="36464-328">Následující konstruktory serializace typy nejsou zaručena pracovat podle očekávání:</span><span class="sxs-lookup"><span data-stu-id="36464-328">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <span data-ttu-id="36464-329"><xref:System.Xml.Serialization.XmlSerializer>nepodaří generovat kód pro typ, který má metody přiřazené s některou z následujících atributů:</span><span class="sxs-lookup"><span data-stu-id="36464-329"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <span data-ttu-id="36464-330"><xref:System.Xml.Serialization.XmlSerializer>nerespektuje <xref:System.Xml.Serialization.IXmlSerializable> vlastní serializační rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36464-330"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="36464-331">Pokud máte třídu, která implementuje toto rozhraní, <xref:System.Xml.Serialization.XmlSerializer> považuje typ prostého starého typu CLR (POCO) a serializuje pouze jeho veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="36464-331">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>

- <span data-ttu-id="36464-332">Serializace prostého <xref:System.Exception> objektu nefunguje <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>dobře s a .</span><span class="sxs-lookup"><span data-stu-id="36464-332">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>

## <a name="visual-studio-differences"></a><span data-ttu-id="36464-333">Rozdíly v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="36464-333">Visual Studio differences</span></span>

<span data-ttu-id="36464-334">**Výjimky a ladění**</span><span class="sxs-lookup"><span data-stu-id="36464-334">**Exceptions and debugging**</span></span>

<span data-ttu-id="36464-335">Při spuštění aplikací zkompilovaných pomocí .NET Native v ladicím programu jsou povoleny výjimky první šance pro následující typy výjimek:</span><span class="sxs-lookup"><span data-stu-id="36464-335">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

<span data-ttu-id="36464-336">**Vytváření aplikací**</span><span class="sxs-lookup"><span data-stu-id="36464-336">**Building apps**</span></span>

<span data-ttu-id="36464-337">Použijte nástroje sestavení x86, které se používají ve výchozím nastavení visual studio.</span><span class="sxs-lookup"><span data-stu-id="36464-337">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="36464-338">Nedoporučujeme používat nástroje AMD64 MSBuild, které se nacházejí v c:\programových souborech (x86)\MSBuild\12.0\bin\amd64; Ty mohou způsobit problémy sestavení.</span><span class="sxs-lookup"><span data-stu-id="36464-338">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>

<span data-ttu-id="36464-339">**Profilovací programy**</span><span class="sxs-lookup"><span data-stu-id="36464-339">**Profilers**</span></span>

- <span data-ttu-id="36464-340">Profiler procesoru Visual Studio a profiler paměti XAML nezobrazují just-my-code správně.</span><span class="sxs-lookup"><span data-stu-id="36464-340">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>

- <span data-ttu-id="36464-341">Paměť Ový profilování XAML nezobrazuje přesně spravovaná data haldy.</span><span class="sxs-lookup"><span data-stu-id="36464-341">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>

- <span data-ttu-id="36464-342">Profiler procesoru neidentifikuje správně moduly a zobrazuje předponové názvy funkcí.</span><span class="sxs-lookup"><span data-stu-id="36464-342">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>

<span data-ttu-id="36464-343">**Projekty knihovny testování částí**</span><span class="sxs-lookup"><span data-stu-id="36464-343">**Unit Test Library projects**</span></span>

<span data-ttu-id="36464-344">Povolení nativního rozhraní .NET v knihovně testování částí pro projekt aplikací pro Windows Store není podporováno a způsobí, že se projekt nepodaří sestavit.</span><span class="sxs-lookup"><span data-stu-id="36464-344">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>

## <a name="see-also"></a><span data-ttu-id="36464-345">Viz také</span><span class="sxs-lookup"><span data-stu-id="36464-345">See also</span></span>

- [<span data-ttu-id="36464-346">Začínáme</span><span class="sxs-lookup"><span data-stu-id="36464-346">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="36464-347">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="36464-347">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="36464-348">Přehled aplikace .NET pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="36464-348">.NET For Windows Store apps overview</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [<span data-ttu-id="36464-349">Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="36464-349">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
