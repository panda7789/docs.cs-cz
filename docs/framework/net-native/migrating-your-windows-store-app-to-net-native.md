---
title: Migrace aplikace pro Windows Store do .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a316cd8ed82f9833b23fe313b8f4c4903bd0a433
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397777"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="022e7-102">Migrace aplikace pro Windows Store do .NET Native</span><span class="sxs-lookup"><span data-stu-id="022e7-102">Migrating Your Windows Store App to .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="022e7-103"> poskytuje statické kompilace aplikací ve službě Windows Store nebo na počítači pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="022e7-103"> provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="022e7-104">Tím se liší od dynamická kompilace provádí kompilátoru v běhu (JIT) pro aplikace Windows Store nebo [generátor (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) na zařízení.</span><span class="sxs-lookup"><span data-stu-id="022e7-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="022e7-105">Bez ohledu rozdíly [!INCLUDE[net_native](../../../includes/net-native-md.md)] pokusí zachování kompatibility s [aplikace .NET pro Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span><span class="sxs-lookup"><span data-stu-id="022e7-105">Despite the differences, [!INCLUDE[net_native](../../../includes/net-native-md.md)] tries to maintain compatibility with the [.NET for Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span></span> <span data-ttu-id="022e7-106">Ve většině případů věcí, které fungují v aplikacích .NET pro Windows Store se taky pracovat s [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-106">For the most part, things that work on the .NET for Windows Store apps also work with [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  <span data-ttu-id="022e7-107">Ale v některých případech se můžete setkat s nějaké změny.</span><span class="sxs-lookup"><span data-stu-id="022e7-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="022e7-108">Tento dokument popisuje tyto rozdíly mezi standardní aplikace .NET pro Windows Store a [!INCLUDE[net_native](../../../includes/net-native-md.md)] v těchto oblastech:</span><span class="sxs-lookup"><span data-stu-id="022e7-108">This document discusses these differences between the standard .NET for Windows Store apps and [!INCLUDE[net_native](../../../includes/net-native-md.md)] in the following areas:</span></span>  
  
-   [<span data-ttu-id="022e7-109">Rozdíly obecné runtime</span><span class="sxs-lookup"><span data-stu-id="022e7-109">General runtime differences</span></span>](#Runtime)  
  
-   [<span data-ttu-id="022e7-110">Dynamické programování rozdílů</span><span class="sxs-lookup"><span data-stu-id="022e7-110">Dynamic programming differences</span></span>](#Dynamic)  
  
-   [<span data-ttu-id="022e7-111">Další související reflexe rozdíly</span><span class="sxs-lookup"><span data-stu-id="022e7-111">Other reflection-related differences</span></span>](#Reflection)  
  
-   [<span data-ttu-id="022e7-112">Nepodporované scénáře a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="022e7-112">Unsupported scenarios and APIs</span></span>](#Unsupported)  
  
-   [<span data-ttu-id="022e7-113">Rozdíly Visual Studio</span><span class="sxs-lookup"><span data-stu-id="022e7-113">Visual Studio differences</span></span>](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a><span data-ttu-id="022e7-114">Rozdíly obecné runtime</span><span class="sxs-lookup"><span data-stu-id="022e7-114">General runtime differences</span></span>  
  
-   <span data-ttu-id="022e7-115">Výjimky, jako například <xref:System.TypeLoadException>, která jsou vyvolané kompilátoru za běhu, když aplikace běží na nejběžnější language runtime (CLR) obecně mít za následek chyby při kompilaci při zpracování [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="022e7-116">Nemůžete volat <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metoda z vlákna uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="022e7-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="022e7-117">Může dojít k zablokování na [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-117">This can result in a deadlock on [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="022e7-118">Nemusíte spoléhat na statická třída konstruktor volání řazení.</span><span class="sxs-lookup"><span data-stu-id="022e7-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="022e7-119">V [!INCLUDE[net_native](../../../includes/net-native-md.md)], se liší od pořadí na standardní runtime pořadí volání.</span><span class="sxs-lookup"><span data-stu-id="022e7-119">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="022e7-120">(I s standardní modul runtime, neměli byste tedy spoléhat v řádu provádění statická třída konstruktory.)</span><span class="sxs-lookup"><span data-stu-id="022e7-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>  
  
-   <span data-ttu-id="022e7-121">Nekonečné opakování ve smyčce bez provedení volání (například `while(true);`) na všechny přístup z více vláken, mohou způsobit aplikace zastavení.</span><span class="sxs-lookup"><span data-stu-id="022e7-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="022e7-122">Podobně velké soubory nebo nekonečné počká, mohou způsobit aplikace zastavení.</span><span class="sxs-lookup"><span data-stu-id="022e7-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>  
  
-   <span data-ttu-id="022e7-123">Některé obecné inicializace cykly nemáte generování výjimek [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-123">Certain generic initialization cycles don't throw exceptions in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="022e7-124">Například následující kód vrátí <xref:System.TypeLoadException> výjimky na standardní CLR.</span><span class="sxs-lookup"><span data-stu-id="022e7-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="022e7-125">V [!INCLUDE[net_native](../../../includes/net-native-md.md)], nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="022e7-125">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], it doesn't.</span></span>  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   <span data-ttu-id="022e7-126">V některých případech [!INCLUDE[net_native](../../../includes/net-native-md.md)] poskytuje různé implementace knihovny tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="022e7-126">In some cases, [!INCLUDE[net_native](../../../includes/net-native-md.md)] provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="022e7-127">Objekt, vrátí metoda bude vždy implementovat členy vráceného typu.</span><span class="sxs-lookup"><span data-stu-id="022e7-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="022e7-128">Ale vzhledem k tomu, že jeho implementace zálohování se liší, nelze přetypovat na stejnou sadu typy, jako by na jiných platformách rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="022e7-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="022e7-129">Například v některých případech nelze přetypovat <xref:System.Collections.Generic.IEnumerable%601> rozhraní objektů vrácené objektem metody, jako <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> k `T[]`.</span><span class="sxs-lookup"><span data-stu-id="022e7-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>  
  
-   <span data-ttu-id="022e7-130">Mezipaměť WinInet není povolená ve výchozím nastavení pro aplikace .NET pro Windows Store, ale je na [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="022e7-131">To zvyšuje výkon, ale má pracujícího sadu dopad.</span><span class="sxs-lookup"><span data-stu-id="022e7-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="022e7-132">Není nutná žádná akce developer.</span><span class="sxs-lookup"><span data-stu-id="022e7-132">No developer action is necessary.</span></span>  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a><span data-ttu-id="022e7-133">Dynamické programování rozdílů</span><span class="sxs-lookup"><span data-stu-id="022e7-133">Dynamic programming differences</span></span>  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="022e7-134"> staticky odkazuje kód rozhraní .NET Framework, chcete-li kód místní aplikace pro maximální výkon.</span><span class="sxs-lookup"><span data-stu-id="022e7-134"> statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="022e7-135">Binární velikosti je však nutné zůstávají malé, takže celý rozhraní .NET Framework není možné připojit v.</span><span class="sxs-lookup"><span data-stu-id="022e7-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="022e7-136">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilátoru přeloží toto omezení pomocí reduktorem závislost, která odebere odkazy na nepoužívané kódu.</span><span class="sxs-lookup"><span data-stu-id="022e7-136">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="022e7-137">Ale [!INCLUDE[net_native](../../../includes/net-native-md.md)] nemusí údržbě nebo při informace nelze odvodit staticky v době kompilace, ale místo toho se dynamicky načíst za běhu generovat některé informace o typu a kódu.</span><span class="sxs-lookup"><span data-stu-id="022e7-137">However, [!INCLUDE[net_native](../../../includes/net-native-md.md)] might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="022e7-138"> Povolit reflexe a dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="022e7-138"> does enable reflection and dynamic programming.</span></span> <span data-ttu-id="022e7-139">Ne všechny typy lze však označit pro reflexe, protože by velikost generovaného kódu příliš velký (hlavně proto odrážející na veřejné rozhraní API v rozhraní .NET Framework je podporuje).</span><span class="sxs-lookup"><span data-stu-id="022e7-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="022e7-140">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilátoru umožňuje inteligentní možností, které typy by měly podporovat reflexe, a udržuje metadata a generuje kód jenom pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="022e7-140">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>  
  
 <span data-ttu-id="022e7-141">Datová vazba například vyžaduje aplikaci, abyste mohli mapovat názvy vlastností na funkce.</span><span class="sxs-lookup"><span data-stu-id="022e7-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="022e7-142">V aplikacích .NET pro Windows Store modul common language runtime automaticky používá reflexe zajišťující tuto možnost pro veřejně dostupné typy nativní a spravované typy.</span><span class="sxs-lookup"><span data-stu-id="022e7-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="022e7-143">V [!INCLUDE[net_native](../../../includes/net-native-md.md)], kompilátor automaticky zahrne metadata pro typy, pro které vázat data.</span><span class="sxs-lookup"><span data-stu-id="022e7-143">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the compiler automatically includes metadata for types to which you bind data.</span></span>  
  
 <span data-ttu-id="022e7-144">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilátoru může také zpracovat běžně používané obecné typy, jako <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602>, které pracovní bez nutnosti jakékoli pomocné parametry nebo direktivy.</span><span class="sxs-lookup"><span data-stu-id="022e7-144">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="022e7-145">[Dynamické](~/docs/csharp/language-reference/keywords/dynamic.md) – klíčové slovo je podporováno také v rámci určitá omezení.</span><span class="sxs-lookup"><span data-stu-id="022e7-145">The [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="022e7-146">Měli byste otestovat všechny cesty kódu dynamické důkladně při portování aplikaci [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-146">You should test all dynamic code paths thoroughly when porting your app to [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="022e7-147">Výchozí konfiguraci pro [!INCLUDE[net_native](../../../includes/net-native-md.md)] je dostatečné pro většinu vývojáři, ale někteří vývojáři chtít jemnou optimalizace jejich konfigurace počítače pomocí direktivy modulu runtime (. rd.xml) souboru.</span><span class="sxs-lookup"><span data-stu-id="022e7-147">The default configuration for [!INCLUDE[net_native](../../../includes/net-native-md.md)] is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="022e7-148">Kromě toho, v některých případech [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilátoru se nepodařilo určit, které metadata musí být k dispozici pro reflexi a spoléhá na pomocné parametry, zejména v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="022e7-148">In addition, in some cases, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>  
  
-   <span data-ttu-id="022e7-149">Některé konstrukce, jako <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> a <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> nelze určit staticky.</span><span class="sxs-lookup"><span data-stu-id="022e7-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>  
  
-   <span data-ttu-id="022e7-150">Protože kompilátor nemůže zjistit, konkretizací, obecného typu, který chcete, aby odpovídala v musí být určena direktivy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="022e7-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="022e7-151">Tato akce není právě, protože všechny kód musí být zahrnut, ale důvodu reflexe v obecných typech, můžete nekonečné cyklus (například když obecná metoda je volána, obecného typu).</span><span class="sxs-lookup"><span data-stu-id="022e7-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="022e7-152">Direktivy modulu runtime jsou definovány v direktivy modulu runtime (. rd.xml) souboru.</span><span class="sxs-lookup"><span data-stu-id="022e7-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="022e7-153">Obecné informace o použití tohoto souboru najdete v tématu [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="022e7-153">For general information about using this file, see [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span> <span data-ttu-id="022e7-154">Informace o direktivy modulu runtime najdete v tématu [direktivy modulu Runtime (rd.xml) referenci na konfigurační soubor](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="022e7-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="022e7-155"> zahrnuje taky profilace nástroje, které pomáhají určit, jaké typy mimo výchozí sadu by měla podporovat reflexe vývojář.</span><span class="sxs-lookup"><span data-stu-id="022e7-155"> also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a><span data-ttu-id="022e7-156">Další související reflexe rozdíly</span><span class="sxs-lookup"><span data-stu-id="022e7-156">Other reflection-related differences</span></span>  
 <span data-ttu-id="022e7-157">Existuje několik dalších jednotlivých související reflexe rozdíly v chování mezi aplikace .NET pro Windows Store a [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="022e7-158">V [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="022e7-158">In [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
-   <span data-ttu-id="022e7-159">Privátní reflexe přes typy a členy v knihovně tříd rozhraní .NET Framework není podporována.</span><span class="sxs-lookup"><span data-stu-id="022e7-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="022e7-160">Můžete, ale projeví přes vlastní privátní typy a členy, jakož i typy a členy v knihovnách třetích stran.</span><span class="sxs-lookup"><span data-stu-id="022e7-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>  
  
-   <span data-ttu-id="022e7-161"><xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Vlastnost správně vrací `false` pro <xref:System.Reflection.ParameterInfo> objekt, který reprezentuje návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="022e7-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="022e7-162">V aplikacích .NET pro Windows Store, vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="022e7-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="022e7-163">Převodní jazyk (IL) nepodporuje tento přímo a výkladu je ponechán jazyk.</span><span class="sxs-lookup"><span data-stu-id="022e7-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>  
  
-   <span data-ttu-id="022e7-164">Veřejné členy na <xref:System.RuntimeFieldHandle> a <xref:System.RuntimeMethodHandle> struktury nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="022e7-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="022e7-165">Tyto typy jsou podporovány pouze u LINQ, stromy výrazů a inicializace statické pole.</span><span class="sxs-lookup"><span data-stu-id="022e7-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>  
  
-   <span data-ttu-id="022e7-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> a <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> zahrnout skryté členy základní třídy a proto může být přepsána bez explicitní přepsání.</span><span class="sxs-lookup"><span data-stu-id="022e7-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="022e7-167">To platí i jiné [RuntimeReflectionExtensions.GetRuntime\*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="022e7-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) methods.</span></span>  
  
-   <span data-ttu-id="022e7-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> a <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> nemáte selhání při pokusu o vytvoření určité kombinace (například pole byrefs).</span><span class="sxs-lookup"><span data-stu-id="022e7-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>  
  
-   <span data-ttu-id="022e7-169">Reflexe nelze použít k vyvolání členy, které mají parametry ukazatele.</span><span class="sxs-lookup"><span data-stu-id="022e7-169">You can't use reflection to invoke members that have pointer parameters.</span></span>  
  
-   <span data-ttu-id="022e7-170">Reflexe nelze použít k získání nebo nastavení pole ukazatele.</span><span class="sxs-lookup"><span data-stu-id="022e7-170">You can't use reflection to get or set a pointer field.</span></span>  
  
-   <span data-ttu-id="022e7-171">Když je nesprávný počet argumentů a typ jednoho z argumentů je nesprávný, [!INCLUDE[net_native](../../../includes/net-native-md.md)] vyvolá <xref:System.ArgumentException> místo <xref:System.Reflection.TargetParameterCountException>.</span><span class="sxs-lookup"><span data-stu-id="022e7-171">When the argument count is wrong and the type of one of the arguments is incorrect, [!INCLUDE[net_native](../../../includes/net-native-md.md)] throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>  
  
-   <span data-ttu-id="022e7-172">Binární serializace výjimek obecně není podporována.</span><span class="sxs-lookup"><span data-stu-id="022e7-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="022e7-173">V důsledku toho nejsou objekty mohou být přidány do <xref:System.Exception.Data%2A?displayProperty=nameWithType> slovníku.</span><span class="sxs-lookup"><span data-stu-id="022e7-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="022e7-174">Nepodporované scénáře a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="022e7-174">Unsupported scenarios and APIs</span></span>  
 <span data-ttu-id="022e7-175">Následující části uvádějí nepodporované scénáře a rozhraní API pro obecné vývoj, zprostředkovatel komunikace s objekty a technologie, jako je například HTTPClient a Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="022e7-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>  
  
-   [<span data-ttu-id="022e7-176">Obecné vývoj</span><span class="sxs-lookup"><span data-stu-id="022e7-176">General development</span></span>](#General)  
  
-   [<span data-ttu-id="022e7-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="022e7-177">HttpClient</span></span>](#HttpClient)  
  
-   [<span data-ttu-id="022e7-178">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="022e7-178">Interop</span></span>](#Interop)  
  
-   [<span data-ttu-id="022e7-179">Nepodporované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="022e7-179">Unsupported APIs</span></span>](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a><span data-ttu-id="022e7-180">Vývoj pro obecné rozdíly</span><span class="sxs-lookup"><span data-stu-id="022e7-180">General development differences</span></span>  
 <span data-ttu-id="022e7-181">**Typy hodnot**</span><span class="sxs-lookup"><span data-stu-id="022e7-181">**Value types**</span></span>  
  
-   <span data-ttu-id="022e7-182">Pokud přepíšete <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> a <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody pro typ hodnoty, nemůžete volat implementace základní třídy.</span><span class="sxs-lookup"><span data-stu-id="022e7-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="022e7-183">V aplikacích .NET pro Windows Store tyto metody závisí na reflexi.</span><span class="sxs-lookup"><span data-stu-id="022e7-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="022e7-184">Při kompilaci [!INCLUDE[net_native](../../../includes/net-native-md.md)] generuje implementace, která není závisí na reflexi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="022e7-184">At compile time, [!INCLUDE[net_native](../../../includes/net-native-md.md)] generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="022e7-185">To znamená, že pokud nemáte přepsat tyto dvě metody, budou fungovat podle očekávání, protože [!INCLUDE[net_native](../../../includes/net-native-md.md)] generuje implementace v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="022e7-185">This means that if you don't override these two methods, they will work as expected, because [!INCLUDE[net_native](../../../includes/net-native-md.md)] generates the implementation at compile time.</span></span> <span data-ttu-id="022e7-186">Přepsání těchto metod, ale volání implementaci základní třídy výsledkem však výjimku.</span><span class="sxs-lookup"><span data-stu-id="022e7-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>  
  
-   <span data-ttu-id="022e7-187">Typy hodnot, které jsou větší než 1 MB nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="022e7-187">Value types larger than one megabyte aren't supported.</span></span>  
  
-   <span data-ttu-id="022e7-188">Typy hodnot nemůže mít výchozí konstruktor v [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-188">Value types can't have a default constructor in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="022e7-189">(C# a Visual Basic zakázat výchozí konstruktory u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="022e7-189">(C# and Visual Basic prohibit default constructors on value types.</span></span> <span data-ttu-id="022e7-190">Ale ty lze vytvořit v IL.)</span><span class="sxs-lookup"><span data-stu-id="022e7-190">However, these can be created in IL.)</span></span>  
  
 <span data-ttu-id="022e7-191">**Pole**</span><span class="sxs-lookup"><span data-stu-id="022e7-191">**Arrays**</span></span>  
  
-   <span data-ttu-id="022e7-192">Pole s dolní mez než nulu nejsou podporována.</span><span class="sxs-lookup"><span data-stu-id="022e7-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="022e7-193">Obvykle jsou tato pole vytvořena voláním <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> přetížení.</span><span class="sxs-lookup"><span data-stu-id="022e7-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
-   <span data-ttu-id="022e7-194">Dynamické vytváření vícerozměrná pole není podporováno.</span><span class="sxs-lookup"><span data-stu-id="022e7-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="022e7-195">Takovými poli se obvykle vytvářejí voláním přetížení <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metoda, která zahrnuje `lengths` parametr, nebo při volání <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="022e7-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="022e7-196">Vícerozměrná pole, které mají čtyři nebo více dimenzí nejsou podporovány; To znamená jejich <xref:System.Array.Rank%2A?displayProperty=nameWithType> hodnota vlastnosti je 4 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="022e7-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="022e7-197">Použití [Vícenásobná pole](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (pole polí) místo.</span><span class="sxs-lookup"><span data-stu-id="022e7-197">Use [jagged arrays](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="022e7-198">Například `array[x,y,z]` je neplatná, ale `array[x][y][z]` není.</span><span class="sxs-lookup"><span data-stu-id="022e7-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>  
  
-   <span data-ttu-id="022e7-199">Odchylky pro vícerozměrná pole nepodporuje a způsobí, že <xref:System.InvalidCastException> výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="022e7-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>  
  
 <span data-ttu-id="022e7-200">**Obecné typy**</span><span class="sxs-lookup"><span data-stu-id="022e7-200">**Generics**</span></span>  
  
-   <span data-ttu-id="022e7-201">Chyba kompilátoru za následek rozšíření nekonečné obecného typu.</span><span class="sxs-lookup"><span data-stu-id="022e7-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="022e7-202">Například tento kód se nepovede zkompilovat:</span><span class="sxs-lookup"><span data-stu-id="022e7-202">For example, this code fails to compile:</span></span>  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 <span data-ttu-id="022e7-203">**Ukazatele**</span><span class="sxs-lookup"><span data-stu-id="022e7-203">**Pointers**</span></span>  
  
-   <span data-ttu-id="022e7-204">Pole ukazatele nejsou podporována.</span><span class="sxs-lookup"><span data-stu-id="022e7-204">Arrays of pointers aren't supported.</span></span>  
  
-   <span data-ttu-id="022e7-205">Reflexe nelze použít k získání nebo nastavení pole ukazatele.</span><span class="sxs-lookup"><span data-stu-id="022e7-205">You can't use reflection to get or set a pointer field.</span></span>  
  
 <span data-ttu-id="022e7-206">**Serializace**</span><span class="sxs-lookup"><span data-stu-id="022e7-206">**Serialization**</span></span>  
  
 <span data-ttu-id="022e7-207"><xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Atribut není podporován.</span><span class="sxs-lookup"><span data-stu-id="022e7-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="022e7-208">Použití <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> atribut místo.</span><span class="sxs-lookup"><span data-stu-id="022e7-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>  
  
 <span data-ttu-id="022e7-209">**Prostředky**</span><span class="sxs-lookup"><span data-stu-id="022e7-209">**Resources**</span></span>  
  
 <span data-ttu-id="022e7-210">Použití lokalizované prostředky s <xref:System.Diagnostics.Tracing.EventSource> třída není podporována.</span><span class="sxs-lookup"><span data-stu-id="022e7-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="022e7-211"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Nedefinuje vlastnost lokalizované prostředky.</span><span class="sxs-lookup"><span data-stu-id="022e7-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>  
  
 <span data-ttu-id="022e7-212">**Delegáti**</span><span class="sxs-lookup"><span data-stu-id="022e7-212">**Delegates**</span></span>  
  
 <span data-ttu-id="022e7-213">`Delegate.BeginInvoke` a `Delegate.EndInvoke` nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="022e7-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>  
  
 <span data-ttu-id="022e7-214">**Async**</span><span class="sxs-lookup"><span data-stu-id="022e7-214">**Async**</span></span>  
  
 <span data-ttu-id="022e7-215">Dělení na vlákna logiku přetížení IAsync úloh není podporována.</span><span class="sxs-lookup"><span data-stu-id="022e7-215">Threading logic in overloads of Task IAsync isn't supported.</span></span>  
  
 <span data-ttu-id="022e7-216">**Ostatní rozhraní API**</span><span class="sxs-lookup"><span data-stu-id="022e7-216">**Miscellaneous APIs**</span></span>  
  
-   <span data-ttu-id="022e7-217"><xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> Vlastnost vyvolává <xref:System.PlatformNotSupportedException> výjimka pokud <xref:System.Runtime.InteropServices.GuidAttribute> není použit atribut typu.</span><span class="sxs-lookup"><span data-stu-id="022e7-217">The <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="022e7-218">Identifikátor GUID slouží především pro podporu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="022e7-218">The GUID is used primarily for COM support.</span></span>  
  
-   <span data-ttu-id="022e7-219"><xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Metoda správně analyzuje řetězce, které obsahují krátká data v [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-219">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="022e7-220">Ale ho nebude zachování kompatibility s změny v datum a čas analýza popsané v článcích znalostní báze Microsoft Knowledge Base [KB2803771](http://support.microsoft.com/kb/2803771) a [KB2803755](http://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="022e7-220">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](http://support.microsoft.com/kb/2803771) and [KB2803755](http://support.microsoft.com/kb/2803755).</span></span>  
  
-   <span data-ttu-id="022e7-221"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` se správně zaokrouhlí v [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-221"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="022e7-222">V některé verze modulu CLR se zkrátí na výsledný řetězec místo zaokrouhlené.</span><span class="sxs-lookup"><span data-stu-id="022e7-222">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a><span data-ttu-id="022e7-223">Rozdíly HttpClient</span><span class="sxs-lookup"><span data-stu-id="022e7-223">HttpClient differences</span></span>  
 <span data-ttu-id="022e7-224">V [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Net.Http.HttpClientHandler> třída se používá interně WinINet (prostřednictvím [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třída) místo <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy používané ve standardní aplikace .NET pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="022e7-224">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="022e7-225">WinINet nepodporuje všechny možnosti konfigurace, který <xref:System.Net.Http.HttpClientHandler> třídy podporuje.</span><span class="sxs-lookup"><span data-stu-id="022e7-225">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="022e7-226">Výsledek:</span><span class="sxs-lookup"><span data-stu-id="022e7-226">As a result:</span></span>  
  
-   <span data-ttu-id="022e7-227">Některé vlastnosti schopností na <xref:System.Net.Http.HttpClientHandler> vrátit `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], vzhledem k tomu, že budou vracet `true` v standardní aplikace .NET pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="022e7-227">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas they return `true` in the standard .NET for Windows Store apps.</span></span>  
  
-   <span data-ttu-id="022e7-228">Některé vlastnosti konfigurace `get` přístupové objekty vždy vrátit pevnou hodnotu na [!INCLUDE[net_native](../../../includes/net-native-md.md)] , je jiná než výchozí hodnota konfigurovat v aplikacích .NET pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="022e7-228">Some of the configuration property `get` accessors always return a fixed value on [!INCLUDE[net_native](../../../includes/net-native-md.md)] that is different than the default configurable value in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="022e7-229">Některé další chování rozdíly jsou popsané v následující témata.</span><span class="sxs-lookup"><span data-stu-id="022e7-229">Some additional behavior differences are covered in the following subsections.</span></span>  
  
 <span data-ttu-id="022e7-230">**Proxy server**</span><span class="sxs-lookup"><span data-stu-id="022e7-230">**Proxy**</span></span>  
  
 <span data-ttu-id="022e7-231">[HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třída nepodporuje konfiguraci nebo přepsání proxy serveru na základě požadavků.</span><span class="sxs-lookup"><span data-stu-id="022e7-231">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="022e7-232">To znamená, že všechny požadavky na [!INCLUDE[net_native](../../../includes/net-native-md.md)] používat systém nakonfigurován server proxy server nebo žádný proxy server, v závislosti na hodnotě <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="022e7-232">This means that all requests on [!INCLUDE[net_native](../../../includes/net-native-md.md)] use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="022e7-233">V aplikacích .NET pro Windows Store je definované proxy serveru <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="022e7-233">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="022e7-234">Na [!INCLUDE[net_native](../../../includes/net-native-md.md)], nastavení <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> hodnotu jinou než `null` vyvolá <xref:System.PlatformNotSupportedException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="022e7-234">On [!INCLUDE[net_native](../../../includes/net-native-md.md)], setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="022e7-235"><xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Vlastnost vrátí `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], zatímco vrátí `true` v standardní aplikace rozhraní .NET Framework pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="022e7-235">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>  
  
 <span data-ttu-id="022e7-236">**Automatické přesměrování**</span><span class="sxs-lookup"><span data-stu-id="022e7-236">**Automatic redirection**</span></span>  
  
 <span data-ttu-id="022e7-237">[HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třída neumožňuje maximální počet automatické přesměrování nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="022e7-237">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="022e7-238">Hodnota <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> vlastnost je 50 ve výchozím nastavení v standardní aplikace .NET pro Windows Store a nelze jej změnit.</span><span class="sxs-lookup"><span data-stu-id="022e7-238">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="022e7-239">Na [!INCLUDE[net_native](../../../includes/net-native-md.md)], hodnota této vlastnosti je 10 a upravit ho generuje při pokusu <xref:System.PlatformNotSupportedException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="022e7-239">On [!INCLUDE[net_native](../../../includes/net-native-md.md)], the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="022e7-240"><xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Vlastnost vrátí `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], zatímco vrátí `true` v aplikacích .NET pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="022e7-240">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas it returns `true` in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="022e7-241">**Automatickou dekompresi**</span><span class="sxs-lookup"><span data-stu-id="022e7-241">**Automatic decompression**</span></span>  
  
 <span data-ttu-id="022e7-242">Aplikace .NET pro Windows Store můžete nastavit <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> vlastnost <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, oba <xref:System.Net.DecompressionMethods.Deflate> a <xref:System.Net.DecompressionMethods.GZip>, nebo <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="022e7-242">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="022e7-243"> podporuje pouze <xref:System.Net.DecompressionMethods.Deflate> společně s <xref:System.Net.DecompressionMethods.GZip>, nebo <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="022e7-243"> only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="022e7-244">Pokusu o nastavení <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> vlastnost, která má buď <xref:System.Net.DecompressionMethods.Deflate> nebo <xref:System.Net.DecompressionMethods.GZip> samostatně bezobslužně nastaví na obě <xref:System.Net.DecompressionMethods.Deflate> a <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="022e7-244">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>  
  
 <span data-ttu-id="022e7-245">**Soubory cookie**</span><span class="sxs-lookup"><span data-stu-id="022e7-245">**Cookies**</span></span>  
  
 <span data-ttu-id="022e7-246">Zpracování souborů cookie se provádí současně pomocí <xref:System.Net.Http.HttpClient> a WinINet.</span><span class="sxs-lookup"><span data-stu-id="022e7-246">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="022e7-247">Soubory cookie z <xref:System.Net.CookieContainer> spolu se soubory cookie v mezipaměti souborů cookie WinINet.</span><span class="sxs-lookup"><span data-stu-id="022e7-247">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="022e7-248">Odebrání souborů cookie z <xref:System.Net.CookieContainer> brání <xref:System.Net.Http.HttpClient> odesílání souboru cookie, ale pokud WinINet už zobrazila souboru cookie a uživatelem, nebyly odstraněny soubory cookie z WinINet odešle ji.</span><span class="sxs-lookup"><span data-stu-id="022e7-248">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="022e7-249">Není možné programově odebrat soubor cookie z WinINet pomocí <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, nebo <xref:System.Net.CookieContainer> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="022e7-249">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="022e7-250">Nastavení <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> vlastnost `false` způsobí, že pouze <xref:System.Net.Http.HttpClient> zastavit odesílání soubory cookie. WinINet stále mohou zahrnovat jeho soubory cookie v požadavku.</span><span class="sxs-lookup"><span data-stu-id="022e7-250">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>  
  
 <span data-ttu-id="022e7-251">**přihlašovací údaje**</span><span class="sxs-lookup"><span data-stu-id="022e7-251">**Credentials**</span></span>  
  
 <span data-ttu-id="022e7-252">V aplikacích .NET pro Windows Store <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> a <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> vlastnosti pracují nezávisle.</span><span class="sxs-lookup"><span data-stu-id="022e7-252">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="022e7-253">Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> tato vlastnost přijímá parametry libovolný objekt, který implementuje <xref:System.Net.ICredentials> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="022e7-253">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="022e7-254">V [!INCLUDE[net_native](../../../includes/net-native-md.md)], nastavení <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> vlastnost `true` způsobí, že <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost `null`.</span><span class="sxs-lookup"><span data-stu-id="022e7-254">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="022e7-255">Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost lze nastavit pouze na `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, nebo objekt typu <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="022e7-255">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="022e7-256">Přiřazení jakékoliv <xref:System.Net.ICredentials> objekt, nejoblíbenější z nich je <xref:System.Net.CredentialCache>do <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost vyvolává <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="022e7-256">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>  
  
 <span data-ttu-id="022e7-257">**Další funkce nepodporované nebo unconfigurable**</span><span class="sxs-lookup"><span data-stu-id="022e7-257">**Other unsupported or unconfigurable features**</span></span>  
  
 <span data-ttu-id="022e7-258">V [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="022e7-258">In [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
-   <span data-ttu-id="022e7-259">Hodnota <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> vlastnost je vždy <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="022e7-259">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="022e7-260">V aplikacích .NET pro Windows Store, výchozí hodnota je <xref:System.Net.Http.ClientCertificateOption.Manual>.</span><span class="sxs-lookup"><span data-stu-id="022e7-260">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>  
  
-   <span data-ttu-id="022e7-261"><xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Vlastnost není konfigurovatelné.</span><span class="sxs-lookup"><span data-stu-id="022e7-261">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>  
  
-   <span data-ttu-id="022e7-262"><xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Vlastnost je vždy `true`.</span><span class="sxs-lookup"><span data-stu-id="022e7-262">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="022e7-263">V aplikacích .NET pro Windows Store, výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="022e7-263">In .NET for Windows Store apps, the default is `false`.</span></span>  
  
-   <span data-ttu-id="022e7-264">`SetCookie2` Záhlaví v odpovědi se ignoruje jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="022e7-264">The `SetCookie2` header in responses is ignored as obsolete.</span></span>  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a><span data-ttu-id="022e7-265">Rozdílech spolupráce</span><span class="sxs-lookup"><span data-stu-id="022e7-265">Interop differences</span></span>  
 <span data-ttu-id="022e7-266">**Zastaralá rozhraní API**</span><span class="sxs-lookup"><span data-stu-id="022e7-266">**Deprecated APIs**</span></span>  
  
 <span data-ttu-id="022e7-267">Počet zřídka používaný rozhraní API pro spolupráci se spravovaným kódem jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="022e7-267">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="022e7-268">Při použití s [!INCLUDE[net_native](../../../includes/net-native-md.md)], může tato rozhraní API throw <xref:System.NotImplementedException> nebo <xref:System.PlatformNotSupportedException> výjimky nebo vést k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="022e7-268">When used with [!INCLUDE[net_native](../../../includes/net-native-md.md)], these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="022e7-269">V aplikacích .NET pro Windows Store tato rozhraní API jsou označeny jako zastaralé, i když je volání vygeneruje upozornění kompilátoru, nikoli k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="022e7-269">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>  
  
 <span data-ttu-id="022e7-270">Zastaralá rozhraní API pro `VARIANT` zařazování:</span><span class="sxs-lookup"><span data-stu-id="022e7-270">Deprecated APIs for `VARIANT` marshaling:</span></span>  
  
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
  
 <span data-ttu-id="022e7-271"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> je podporováno, ale vyvolá výjimku, v některých případech, například při použití s [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) nebo byref variant.</span><span class="sxs-lookup"><span data-stu-id="022e7-271"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) or byref variants.</span></span>  
  
 <span data-ttu-id="022e7-272">Zastaralá rozhraní API pro [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) podporují:</span><span class="sxs-lookup"><span data-stu-id="022e7-272">Deprecated APIs for [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) support:</span></span>  
  
|<span data-ttu-id="022e7-273">Typ</span><span class="sxs-lookup"><span data-stu-id="022e7-273">Type</span></span>|<span data-ttu-id="022e7-274">Člen</span><span class="sxs-lookup"><span data-stu-id="022e7-274">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>|<span data-ttu-id="022e7-275">Atribut není podporován.</span><span class="sxs-lookup"><span data-stu-id="022e7-275">Attribute isn't supported</span></span>|  
  
 <span data-ttu-id="022e7-276">Zastaralá rozhraní API pro classic COM události:</span><span class="sxs-lookup"><span data-stu-id="022e7-276">Deprecated APIs for classic COM events:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 <span data-ttu-id="022e7-277">Zastaralá rozhraní API v <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> rozhraní, což není podporováno v [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="022e7-277">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
|<span data-ttu-id="022e7-278">Typ</span><span class="sxs-lookup"><span data-stu-id="022e7-278">Type</span></span>|<span data-ttu-id="022e7-279">Člen</span><span class="sxs-lookup"><span data-stu-id="022e7-279">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>|<span data-ttu-id="022e7-280">Všechny členy.</span><span class="sxs-lookup"><span data-stu-id="022e7-280">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>|<span data-ttu-id="022e7-281">Všechny členy.</span><span class="sxs-lookup"><span data-stu-id="022e7-281">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>|<span data-ttu-id="022e7-282">Všechny členy.</span><span class="sxs-lookup"><span data-stu-id="022e7-282">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=nameWithType>|  
  
 <span data-ttu-id="022e7-283">Jiné nepodporované funkce zprostředkovatele komunikace s objekty:</span><span class="sxs-lookup"><span data-stu-id="022e7-283">Other unsupported interop features:</span></span>  
  
|<span data-ttu-id="022e7-284">Typ</span><span class="sxs-lookup"><span data-stu-id="022e7-284">Type</span></span>|<span data-ttu-id="022e7-285">Člen</span><span class="sxs-lookup"><span data-stu-id="022e7-285">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>|<span data-ttu-id="022e7-286">Všechny členy.</span><span class="sxs-lookup"><span data-stu-id="022e7-286">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>|<span data-ttu-id="022e7-287">Všechny členy.</span><span class="sxs-lookup"><span data-stu-id="022e7-287">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 <span data-ttu-id="022e7-288">Je používána zřídka mezipaměti sdružených dat rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="022e7-288">Rarely used marshalling APIs:</span></span>  
  
|<span data-ttu-id="022e7-289">Typ</span><span class="sxs-lookup"><span data-stu-id="022e7-289">Type</span></span>|<span data-ttu-id="022e7-290">Člen</span><span class="sxs-lookup"><span data-stu-id="022e7-290">Member</span></span>|  
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
  
 <span data-ttu-id="022e7-291">**Vyvolání platformy a kompatibility zprostředkovatele komunikace s objekty COM**</span><span class="sxs-lookup"><span data-stu-id="022e7-291">**Platform invoke and COM interop compatibility**</span></span>  
  
 <span data-ttu-id="022e7-292">Vyvolání platformy většina a scénáře zprostředkovatele komunikace s objekty COM jsou stále podporovány v [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-292">Most platform invoke and COM interop scenarios are still supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="022e7-293">Konkrétně je podporována všechny interoperabilitu se prostředí Windows Runtime (WinRT) rozhraní API a zařazování požadované pro prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="022e7-293">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="022e7-294">To zahrnuje podporu pro zařazování:</span><span class="sxs-lookup"><span data-stu-id="022e7-294">This includes marshaling support for:</span></span>  
  
-   <span data-ttu-id="022e7-295">Pole (včetně <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="022e7-295">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>  
  
-   `BStr`  
  
-   <span data-ttu-id="022e7-296">Delegáty</span><span class="sxs-lookup"><span data-stu-id="022e7-296">Delegates</span></span>  
  
-   <span data-ttu-id="022e7-297">Řetězce (znakové sady Unicode, Ansi a HSTRING)</span><span class="sxs-lookup"><span data-stu-id="022e7-297">Strings (Unicode, Ansi, and HSTRING)</span></span>  
  
-   <span data-ttu-id="022e7-298">Struktury (`byref` a `byval`)</span><span class="sxs-lookup"><span data-stu-id="022e7-298">Structs (`byref` and `byval`)</span></span>  
  
-   <span data-ttu-id="022e7-299">Sjednocení</span><span class="sxs-lookup"><span data-stu-id="022e7-299">Unions</span></span>  
  
-   <span data-ttu-id="022e7-300">Obslužné rutiny Win32</span><span class="sxs-lookup"><span data-stu-id="022e7-300">Win32 handles</span></span>  
  
-   <span data-ttu-id="022e7-301">Všechny WinRT konstrukce</span><span class="sxs-lookup"><span data-stu-id="022e7-301">All WinRT constructs</span></span>  
  
-   <span data-ttu-id="022e7-302">Částečná podpora zařazování typů variant.</span><span class="sxs-lookup"><span data-stu-id="022e7-302">Partial support for marshaling variant types.</span></span> <span data-ttu-id="022e7-303">Jsou podporovány následující:</span><span class="sxs-lookup"><span data-stu-id="022e7-303">The following are supported:</span></span>  
  
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
  
    -   [<span data-ttu-id="022e7-304">IUnknown</span><span class="sxs-lookup"><span data-stu-id="022e7-304">IUnknown</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 <span data-ttu-id="022e7-305">Ale [!INCLUDE[net_native](../../../includes/net-native-md.md)] nepodporuje následující:</span><span class="sxs-lookup"><span data-stu-id="022e7-305">However, [!INCLUDE[net_native](../../../includes/net-native-md.md)] doesn't support the following:</span></span>  
  
-   <span data-ttu-id="022e7-306">Pomocí klasického modelu COM události</span><span class="sxs-lookup"><span data-stu-id="022e7-306">Using classic COM events</span></span>  
  
-   <span data-ttu-id="022e7-307">Implementace <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> rozhraní na spravovaného typu</span><span class="sxs-lookup"><span data-stu-id="022e7-307">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>  
  
-   <span data-ttu-id="022e7-308">Implementace [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) rozhraní pro spravovaný typ prostřednictvím <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> atribut.</span><span class="sxs-lookup"><span data-stu-id="022e7-308">Implementing the [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="022e7-309">Ale Všimněte si, že nelze volat objekty modelu COM pomocí `IDispatch`, a spravovaného objektu nelze implementovat, `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="022e7-309">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>  
  
 <span data-ttu-id="022e7-310">Pomocí reflexe k vyvolání platformu vyvolání metody se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="022e7-310">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="022e7-311">Toto omezení můžete obejít tak zabalení volání metody v jiné metody a místo toho volejte obálku pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="022e7-311">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="022e7-312">Další rozdíly z aplikace rozhraní API .NET pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="022e7-312">Other differences from .NET APIs for Windows Store apps</span></span>  
 <span data-ttu-id="022e7-313">Tato část uvádí zbývající rozhraní API, které nejsou podporovány v [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-313">This section lists the remaining APIs that aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="022e7-314">Největší sadu nepodporované rozhraní API jsou Windows Communication Foundation (WCF) rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="022e7-314">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>  
  
 <span data-ttu-id="022e7-315">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="022e7-315">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>  
  
 <span data-ttu-id="022e7-316">Typy v <xref:System.ComponentModel.DataAnnotations> a <xref:System.ComponentModel.DataAnnotations.Schema> obory názvů nejsou podporovány v [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-316">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="022e7-317">Mezi ně patří následující typy, které se nacházejí v aplikacích .NET pro Windows Store pro systém Windows 8:</span><span class="sxs-lookup"><span data-stu-id="022e7-317">These include the following types that are present in the .NET for Windows Store apps for Windows 8:</span></span>  
  
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
  
 <span data-ttu-id="022e7-318">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="022e7-318">**Visual Basic**</span></span>  
  
 <span data-ttu-id="022e7-319">Visual Basic není podporován v [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-319">Visual Basic isn't currently supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="022e7-320">Následující typy, které do <xref:Microsoft.VisualBasic> a <xref:Microsoft.VisualBasic.CompilerServices> obory názvů nejsou k dispozici v [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="022e7-320">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
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
  
 <span data-ttu-id="022e7-321">**Kontext reflexe (obor názvů System.Reflection.Context)**</span><span class="sxs-lookup"><span data-stu-id="022e7-321">**Reflection Context (System.Reflection.Context namespace)**</span></span>  
  
 <span data-ttu-id="022e7-322"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Třída není podporována v [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-322">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="022e7-323">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="022e7-323">**RTC (System.Net.Http.Rtc)**</span></span>  
  
 <span data-ttu-id="022e7-324"><xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> Třída není podporována v [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-324">The <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> class isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="022e7-325">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="022e7-325">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>  
  
 <span data-ttu-id="022e7-326">Typy v [obory názvů System.ServiceModel.\*](http://msdn.microsoft.com/library/gg145010.aspx) nejsou podporovány v [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022e7-326">The types in the [System.ServiceModel.\* namespaces](http://msdn.microsoft.com/library/gg145010.aspx) aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="022e7-327">To zahrnuje následující typy:</span><span class="sxs-lookup"><span data-stu-id="022e7-327">These includes the following types:</span></span>  
  
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
  
### <a name="differences-in-serializers"></a><span data-ttu-id="022e7-328">Rozdíly v serializátorů</span><span class="sxs-lookup"><span data-stu-id="022e7-328">Differences in serializers</span></span>  
 <span data-ttu-id="022e7-329">Následující rozdíly týkají serializace a deserializace pomocí <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer> třídy:</span><span class="sxs-lookup"><span data-stu-id="022e7-329">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>  
  
-   <span data-ttu-id="022e7-330">V [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k serializaci nebo deserializaci odvozené třídy, která má základní třída člena, jehož typ není typu serializace kořenové nezdaří.</span><span class="sxs-lookup"><span data-stu-id="022e7-330">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="022e7-331">Například následující kód, pokusu o serializaci nebo deserializaci `Y` vede k chybě:</span><span class="sxs-lookup"><span data-stu-id="022e7-331">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     <span data-ttu-id="022e7-332">Typ `InnerType` nezná serializátor, protože nejsou členy základní třídy provázán během serializace.</span><span class="sxs-lookup"><span data-stu-id="022e7-332">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>  
  
-   <span data-ttu-id="022e7-333"><xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nepodaří serializovat třídu nebo strukturu, která implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="022e7-333"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="022e7-334">Například následující typy selhat k serializaci nebo deserializaci:</span><span class="sxs-lookup"><span data-stu-id="022e7-334">For example, the following types fail to serialize or deserialize:</span></span>  
  
  
  
-   <span data-ttu-id="022e7-335"><xref:System.Xml.Serialization.XmlSerializer> selže k serializaci následující hodnotu objektu, protože neví přesný typ objektu k serializaci:</span><span class="sxs-lookup"><span data-stu-id="022e7-335"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>  
  
  
  
-   <span data-ttu-id="022e7-336"><xref:System.Xml.Serialization.XmlSerializer> selže k serializaci nebo deserializaci, pokud je typ serializovaný objekt <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="022e7-336"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>  
  
-   <span data-ttu-id="022e7-337">Všechny serializátorů (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer>) se nepodařilo vygenerovat kód serializace typu <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> nebo typu, který obsahuje <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="022e7-337">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="022e7-338">Místo toho se zobrazit chyby čase vytvoření buildu.</span><span class="sxs-lookup"><span data-stu-id="022e7-338">They display build-time errors instead.</span></span>  
  
-   <span data-ttu-id="022e7-339">Těchto konstruktorů typy serializace nemusí fungovat podle očekávání:</span><span class="sxs-lookup"><span data-stu-id="022e7-339">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>  
  
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
  
-   <span data-ttu-id="022e7-340"><xref:System.Xml.Serialization.XmlSerializer> Nepodařilo se generovat kód pro typ, který má metody s atributy s žádným z následujících atributů:</span><span class="sxs-lookup"><span data-stu-id="022e7-340"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <span data-ttu-id="022e7-341"><xref:System.Xml.Serialization.XmlSerializer> není respektovat <xref:System.Xml.Serialization.IXmlSerializable> vlastní serializace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="022e7-341"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="022e7-342">Pokud máte třídu, která toto rozhraní implementuje <xref:System.Xml.Serialization.XmlSerializer> považovat za typ prostý starý typ objektu (objektů POCO) CLR a serializuje jenom jeho veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="022e7-342">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>  
  
-   <span data-ttu-id="022e7-343">Serializace prostý <xref:System.Exception> objektu, například následující příkaz, nebude fungovat správně s <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="022e7-343">Serializing a plain <xref:System.Exception> object, such as the following, doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a><span data-ttu-id="022e7-344">Rozdíly Visual Studio</span><span class="sxs-lookup"><span data-stu-id="022e7-344">Visual Studio differences</span></span>  
 <span data-ttu-id="022e7-345">**Výjimky a ladění**</span><span class="sxs-lookup"><span data-stu-id="022e7-345">**Exceptions and debugging**</span></span>  
  
 <span data-ttu-id="022e7-346">Pokud používáte aplikace, kompilovat s použitím [!INCLUDE[net_native](../../../includes/net-native-md.md)] v ladicím programu, první možnosti výjimky jsou povolené pro následující typy výjimka:</span><span class="sxs-lookup"><span data-stu-id="022e7-346">When you're running apps compiled by using [!INCLUDE[net_native](../../../includes/net-native-md.md)] in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 <span data-ttu-id="022e7-347">**Vytváření aplikací**</span><span class="sxs-lookup"><span data-stu-id="022e7-347">**Building apps**</span></span>  
  
 <span data-ttu-id="022e7-348">Použijte x86 sestavení nástroje, které se používají ve výchozím nastavení Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="022e7-348">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="022e7-349">Nedoporučujeme používat nástroje AMD64 MSBuild, které se nacházejí v C:\Program Files (x86)\MSBuild\12.0\bin\amd64; To může způsobit problémy s sestavení.</span><span class="sxs-lookup"><span data-stu-id="022e7-349">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>  
  
 <span data-ttu-id="022e7-350">**Profilery**</span><span class="sxs-lookup"><span data-stu-id="022e7-350">**Profilers**</span></span>  
  
-   <span data-ttu-id="022e7-351">Visual Studio Profiler procesoru a paměti profileru XAML nezobrazí pouze můj kód správně.</span><span class="sxs-lookup"><span data-stu-id="022e7-351">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>  
  
-   <span data-ttu-id="022e7-352">XAML paměti profileru nebude přesně zobrazovat data spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="022e7-352">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>  
  
-   <span data-ttu-id="022e7-353">Procesor profileru není správně identifikovat moduly a zobrazí předponu názvy funkcí.</span><span class="sxs-lookup"><span data-stu-id="022e7-353">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>  
  
 <span data-ttu-id="022e7-354">**Projekty knihovny testů jednotek**</span><span class="sxs-lookup"><span data-stu-id="022e7-354">**Unit Test Library projects**</span></span>  
  
 <span data-ttu-id="022e7-355">Povolení [!INCLUDE[net_native](../../../includes/net-native-md.md)] na knihovně testů jednotek pro Windows Store projekt aplikace se nepodporuje a způsobí, že projekt nepovede.</span><span class="sxs-lookup"><span data-stu-id="022e7-355">Enabling [!INCLUDE[net_native](../../../includes/net-native-md.md)] on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="022e7-356">Viz také</span><span class="sxs-lookup"><span data-stu-id="022e7-356">See Also</span></span>  
 [<span data-ttu-id="022e7-357">Začínáme</span><span class="sxs-lookup"><span data-stu-id="022e7-357">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="022e7-358">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="022e7-358">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="022e7-359">Přehled aplikace .NET pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="022e7-359">.NET For Windows Store apps overview</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [<span data-ttu-id="022e7-360">Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="022e7-360">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
