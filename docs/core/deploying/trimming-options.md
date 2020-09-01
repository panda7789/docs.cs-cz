---
title: Možnosti ořezávání
description: Naučte se řídit oříznutí aplikací, které jsou v ní obsažené.
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: d6081a24cc18e424b55d40e152f519c680f11aa0
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271877"
---
# <a name="trimming-options"></a><span data-ttu-id="27d22-103">Možnosti ořezávání</span><span class="sxs-lookup"><span data-stu-id="27d22-103">Trimming options</span></span>

<span data-ttu-id="27d22-104">Následující vlastnosti a položky nástroje MSBuild mají vliv na chování [oříznutých samostatných nasazení](trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="27d22-104">The following MSBuild properties and items influence the behavior of [trimmed self-contained deployments](trim-self-contained.md).</span></span> <span data-ttu-id="27d22-105">Některé z zmíněných možností `ILLink` , což je název základního nástroje, který implementuje ořezávání.</span><span class="sxs-lookup"><span data-stu-id="27d22-105">Some of the options mention `ILLink`, which is the name of the underlying tool that implements trimming.</span></span> <span data-ttu-id="27d22-106">Další informace o `ILLink` nástroji příkazového řádku najdete v části [illink Options](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span><span class="sxs-lookup"><span data-stu-id="27d22-106">More information about the `ILLink` command-line tool can be found at [illink options](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

## <a name="enable-trimming"></a><span data-ttu-id="27d22-107">Povolit oříznutí</span><span class="sxs-lookup"><span data-stu-id="27d22-107">Enable trimming</span></span>

- `<PublishTrimmed>true</PublishTrimmed>`

   <span data-ttu-id="27d22-108">Povolí ořezávání během publikování s výchozím nastavením definovaným sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="27d22-108">Enable trimming during publish, with the default settings defined by the SDK.</span></span>

<span data-ttu-id="27d22-109">Při použití nástroje `Microsoft.NET.Sdk` bude provedeno ořezávání sestavení rozhraní architektury na úrovni sestavení ze sady netcoreapp runtime Pack.</span><span class="sxs-lookup"><span data-stu-id="27d22-109">When using `Microsoft.NET.Sdk`, this will perform assembly-level trimming of the framework assemblies from the netcoreapp runtime pack.</span></span> <span data-ttu-id="27d22-110">Kód aplikace a knihovny bez architektury nejsou oříznuty.</span><span class="sxs-lookup"><span data-stu-id="27d22-110">Application code and non-framework libraries are not trimmed.</span></span> <span data-ttu-id="27d22-111">Jiné sady SDK mohou definovat různé výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="27d22-111">Other SDKs may define different defaults.</span></span>

## <a name="trimming-granularity"></a><span data-ttu-id="27d22-112">Rozřezání členitosti</span><span class="sxs-lookup"><span data-stu-id="27d22-112">Trimming granularity</span></span>

<span data-ttu-id="27d22-113">Následující nastavení členitosti určují, jak se zruší agresivní nevyužité IL.</span><span class="sxs-lookup"><span data-stu-id="27d22-113">The following granularity settings control how aggressively unused IL is discarded.</span></span> <span data-ttu-id="27d22-114">To lze nastavit jako vlastnost nebo jako metadata v [jednotlivých sestaveních](#trimmed-assemblies).</span><span class="sxs-lookup"><span data-stu-id="27d22-114">This can be set as a property, or as metadata on an [individual assembly](#trimmed-assemblies).</span></span>

- `<TrimMode>copyused</TrimMode>`

   <span data-ttu-id="27d22-115">Povolit ořezávání na úrovni sestavení, které uchová celé sestavení, pokud je použita kterákoli jeho část (staticky srozumitelným způsobem).</span><span class="sxs-lookup"><span data-stu-id="27d22-115">Enable assembly-level trimming, which will keep an entire assembly if any part of it is used (in a statically-understood way).</span></span>

- `<TrimMode>link</TrimMode>`

    <span data-ttu-id="27d22-116">Povolí ořezávání na úrovni člena, které odebere nepoužívané členy z typů.</span><span class="sxs-lookup"><span data-stu-id="27d22-116">Enable member-level trimming, which removes unused members from types.</span></span>

<span data-ttu-id="27d22-117">Sestavení s `<IsTrimmable>true</IsTrimmable>` metadaty, ale bez explicitní `TrimMode` , budou používat globální `TrimMode` .</span><span class="sxs-lookup"><span data-stu-id="27d22-117">Assemblies with `<IsTrimmable>true</IsTrimmable>` metadata but no explicit `TrimMode` will use the global `TrimMode`.</span></span> <span data-ttu-id="27d22-118">Výchozí hodnota `TrimMode` pro `Microsoft.NET.Sdk` je `copyused` .</span><span class="sxs-lookup"><span data-stu-id="27d22-118">The default `TrimMode` for `Microsoft.NET.Sdk` is `copyused`.</span></span>

## <a name="trimmed-assemblies"></a><span data-ttu-id="27d22-119">Vystříhat sestavení</span><span class="sxs-lookup"><span data-stu-id="27d22-119">Trimmed assemblies</span></span>

<span data-ttu-id="27d22-120">Při publikování aplikace s oříznutou sadou SDK vypočítá výjimku `ItemGroup` `ManagedAssemblyToLink` , která představuje sadu souborů, které mají být zpracovány pro ořezávání.</span><span class="sxs-lookup"><span data-stu-id="27d22-120">When publishing a trimmed app, the SDK computes an `ItemGroup` called `ManagedAssemblyToLink` that represents the set of files to be processed for trimming.</span></span> <span data-ttu-id="27d22-121">`ManagedAssemblyToLink` může mít metadata, která řídí chování ořezávání na sestavení.</span><span class="sxs-lookup"><span data-stu-id="27d22-121">`ManagedAssemblyToLink` may have metadata that controls the trimming behavior per assembly.</span></span> <span data-ttu-id="27d22-122">Chcete-li nastavit tato metadata, vytvořte cíl, který bude spuštěn před předdefinovaným `PrepareForILLink` cílem.</span><span class="sxs-lookup"><span data-stu-id="27d22-122">To set this metadata, create a target that runs before the built-in `PrepareForILLink` target.</span></span> <span data-ttu-id="27d22-123">Tento příklad ukazuje, jak povolit oříznutí `MyAssembly` :</span><span class="sxs-lookup"><span data-stu-id="27d22-123">This example shows how to enable trimming of `MyAssembly`:</span></span>

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

<span data-ttu-id="27d22-124">Nepřidávejte nebo Neodstraňujte položky do/z `ManagedAssemblyToLink` , protože sada SDK počítá tuto sadu během publikování a očekává, že se nemění.</span><span class="sxs-lookup"><span data-stu-id="27d22-124">Do not add or remove items to/from `ManagedAssemblyToLink`, because the SDK computes this set during publish and expects it not to change.</span></span> <span data-ttu-id="27d22-125">Podporovaná metadata:</span><span class="sxs-lookup"><span data-stu-id="27d22-125">The supported metadata is:</span></span>

- `<IsTrimmable>true</IsTrimmable>`

  <span data-ttu-id="27d22-126">Určuje, zda je dané sestavení oříznuto.</span><span class="sxs-lookup"><span data-stu-id="27d22-126">Control whether the given assembly is trimmed.</span></span>

- <span data-ttu-id="27d22-127">`<TrimMode>copyused</TrimMode>` nebo `<TrimMode>link</TrimMode>`</span><span class="sxs-lookup"><span data-stu-id="27d22-127">`<TrimMode>copyused</TrimMode>` or `<TrimMode>link</TrimMode>`</span></span>

  <span data-ttu-id="27d22-128">Řídí [členitost ořezávání](#trimming-granularity) tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="27d22-128">Control the [trimming granularity](#trimming-granularity) of this assembly.</span></span> <span data-ttu-id="27d22-129">Má přednost před globálním `TrimMode` .</span><span class="sxs-lookup"><span data-stu-id="27d22-129">This takes precedence over the global `TrimMode`.</span></span> <span data-ttu-id="27d22-130">Nastavení `TrimMode` v sestavení implikuje `<IsTrimmable>true</IsTrimmable>` .</span><span class="sxs-lookup"><span data-stu-id="27d22-130">Setting `TrimMode` on an assembly implies `<IsTrimmable>true</IsTrimmable>`.</span></span>

## <a name="root-assemblies"></a><span data-ttu-id="27d22-131">Kořenová sestavení</span><span class="sxs-lookup"><span data-stu-id="27d22-131">Root assemblies</span></span>

<span data-ttu-id="27d22-132">Všechna sestavení, která nejsou `<IsTrimmable>true</IsTrimmable>` považována za kořene pro analýzu, což znamená, že budou zachovány všechny své staticky srozumitelné závislosti.</span><span class="sxs-lookup"><span data-stu-id="27d22-132">All assemblies which do not have `<IsTrimmable>true</IsTrimmable>` are considered roots for the analysis, which means that they and all of their statically understood dependencies will be kept.</span></span> <span data-ttu-id="27d22-133">Další sestavení mohou být "rooted" podle názvu (bez `.dll` přípony):</span><span class="sxs-lookup"><span data-stu-id="27d22-133">Additional assemblies may be "rooted" by name (without the `.dll` extension):</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a><span data-ttu-id="27d22-134">Kořenové deskriptory</span><span class="sxs-lookup"><span data-stu-id="27d22-134">Root descriptors</span></span>

<span data-ttu-id="27d22-135">Dalším způsobem, jak zadat kořeny pro analýzu, je použít soubor XML, který používá [Formát popisovače](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)linkeru.</span><span class="sxs-lookup"><span data-stu-id="27d22-135">Another way to specify roots for analysis is using an XML file that uses the linker [descriptor format](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format).</span></span> <span data-ttu-id="27d22-136">To vám umožní rootem konkrétní členy namísto celého sestavení.</span><span class="sxs-lookup"><span data-stu-id="27d22-136">This lets you root specific members instead of a whole assembly.</span></span>

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

<span data-ttu-id="27d22-137">Například `MyRoots.xml` může být kořenem konkrétní metoda, která je dynamicky k dispozici v aplikaci:</span><span class="sxs-lookup"><span data-stu-id="27d22-137">For example, `MyRoots.xml` might root a specific method that is dynamically accessed by the application:</span></span>

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a><span data-ttu-id="27d22-138">Upozornění analýzy</span><span class="sxs-lookup"><span data-stu-id="27d22-138">Analysis warnings</span></span>

<span data-ttu-id="27d22-139">Při ořezávání dojde k odebrání IL, který není staticky dosažitelný.</span><span class="sxs-lookup"><span data-stu-id="27d22-139">Trimming will remove IL that is not statically reachable.</span></span> <span data-ttu-id="27d22-140">Aplikace, které používají reflexi nebo jiné vzory, které vytvářejí dynamické závislosti, mohou být přerušeny oříznutím.</span><span class="sxs-lookup"><span data-stu-id="27d22-140">Apps that use reflection or other patterns that create dynamic dependencies may be broken by trimming.</span></span> <span data-ttu-id="27d22-141">Upozornění na tyto vzory:</span><span class="sxs-lookup"><span data-stu-id="27d22-141">To warn about such patterns:</span></span>

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    <span data-ttu-id="27d22-142">Povolit upozornění analýzy střihu</span><span class="sxs-lookup"><span data-stu-id="27d22-142">Enable trim analysis warnings.</span></span>

<span data-ttu-id="27d22-143">Bude obsahovat upozornění na celou aplikaci, včetně vlastního kódu, kódu knihovny a kódu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="27d22-143">This will include warnings about the entire app, including your own code, library code, and framework code.</span></span>

## <a name="warning-versions"></a><span data-ttu-id="27d22-144">Verze upozornění</span><span class="sxs-lookup"><span data-stu-id="27d22-144">Warning versions</span></span>

<span data-ttu-id="27d22-145">Trim analýza ctí [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) vlastnost, která řídí verzi upozornění analýzy v rámci sady SDK.</span><span class="sxs-lookup"><span data-stu-id="27d22-145">Trim analysis respects the [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) property that controls the version of analysis warnings across the SDK.</span></span> <span data-ttu-id="27d22-146">Existuje další vlastnost, která řídí verzi upozornění analýzy střihně nezávisle (podobně jako `WarningLevel` u kompilátoru):</span><span class="sxs-lookup"><span data-stu-id="27d22-146">There is another property that controls the version of trim analysis warnings independently (similar to `WarningLevel` for the compiler):</span></span>

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    <span data-ttu-id="27d22-147">Emituje jenom upozornění na danou úroveň nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="27d22-147">Emit only warnings of the given level or lower.</span></span> <span data-ttu-id="27d22-148">To může `9999` zahrnovat všechny verze upozornění.</span><span class="sxs-lookup"><span data-stu-id="27d22-148">This can be `9999` to include all warning versions.</span></span>

## <a name="suppressing-warnings"></a><span data-ttu-id="27d22-149">Potlačení upozornění</span><span class="sxs-lookup"><span data-stu-id="27d22-149">Suppressing warnings</span></span>

<span data-ttu-id="27d22-150">Jednotlivé [kódy upozornění](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) je možné potlačit pomocí běžných vlastností MSBuild, které jsou v sada nástrojů, včetně `NoWarn` , `WarningsAsErrors` , `WarningsNotAsErrors` a `TreatWarningsAsErrors` .</span><span class="sxs-lookup"><span data-stu-id="27d22-150">Individual [warning codes](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) can be suppressed using the usual MSBuild properties respected by the toolchain, including `NoWarn`, `WarningsAsErrors`, `WarningsNotAsErrors`, and `TreatWarningsAsErrors`.</span></span> <span data-ttu-id="27d22-151">Existuje další možnost, která řídí chování ILLink upozorňující na chybu nezávisle:</span><span class="sxs-lookup"><span data-stu-id="27d22-151">There is an additional option that controls the ILLink warn-as-error behavior independently:</span></span>

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    <span data-ttu-id="27d22-152">Nepovažujte upozornění ILLink za chyby.</span><span class="sxs-lookup"><span data-stu-id="27d22-152">Don't treat ILLink warnings as errors.</span></span> <span data-ttu-id="27d22-153">To může být užitečné, pokud chcete zabránit tomu, aby se upozornění analýzy při vystřihování zobrazovala chyby, když se chyby kompilátorů globálně zpracovávají</span><span class="sxs-lookup"><span data-stu-id="27d22-153">This may be useful to avoid turning trim analysis warnings into errors when treating compiler warnings as errors globally.</span></span>

## <a name="removing-symbols"></a><span data-ttu-id="27d22-154">Odebírání symbolů</span><span class="sxs-lookup"><span data-stu-id="27d22-154">Removing symbols</span></span>

<span data-ttu-id="27d22-155">Symboly se obvykle oříznou tak, aby odpovídaly oříznutým sestavením.</span><span class="sxs-lookup"><span data-stu-id="27d22-155">Symbols will normally be trimmed to match the trimmed assemblies.</span></span> <span data-ttu-id="27d22-156">Můžete také odebrat všechny symboly:</span><span class="sxs-lookup"><span data-stu-id="27d22-156">You can also remove all symbols:</span></span>

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    <span data-ttu-id="27d22-157">Odeberte symboly z oříznuté aplikace, včetně vložených soubory PDB a samostatných souborů PDB.</span><span class="sxs-lookup"><span data-stu-id="27d22-157">Remove symbols from the trimmed application, including embedded PDBs and separate PDB files.</span></span> <span data-ttu-id="27d22-158">To platí pro kód aplikace i všechny závislosti, které jsou dodávány se symboly.</span><span class="sxs-lookup"><span data-stu-id="27d22-158">This applies to both the application code and any dependencies that come with symbols.</span></span>

<span data-ttu-id="27d22-159">Sada SDK také umožňuje zakázat podporu ladicího programu pomocí vlastnosti `DebuggerSupport` .</span><span class="sxs-lookup"><span data-stu-id="27d22-159">The SDK also makes it possible to disable debugger support using the property `DebuggerSupport`.</span></span> <span data-ttu-id="27d22-160">Pokud je podpora ladicího programu zakázána, ořezávání odstraní symboly automaticky ( `TrimmerRemoveSymbols` Výchozí hodnota je true).</span><span class="sxs-lookup"><span data-stu-id="27d22-160">When debugger support is disabled, trimming will remove symbols automatically (`TrimmerRemoveSymbols` will default to true).</span></span>
