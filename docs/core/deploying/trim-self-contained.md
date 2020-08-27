---
title: Oříznout samostatně obsažené aplikace
description: Naučte se oříznout samostatné aplikace a zmenšit jejich velikost. .NET Core obsahuje modul runtime s aplikací, která je publikovaná samostatně a obecně zahrnuje více prostředí runtime, a je to nezbytné.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 47bccf25b6f6a1b65742bb5e3f5f299932659c3c
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957550"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="8b9d9-104">Odebrání nechtěných součástí a zachování pouze samostatně nasaditelných součástí a spustitelných souborů</span><span class="sxs-lookup"><span data-stu-id="8b9d9-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="8b9d9-105">[Model nasazení závislý na rozhraní](index.md#publish-framework-dependent) byl nejaktivnějším modelem nasazení od okamžiku spuštění .NET.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-105">The [framework-dependent deployment model](index.md#publish-framework-dependent) has been the most successful deployment model since the inception of .NET.</span></span> <span data-ttu-id="8b9d9-106">V tomto scénáři vývojář aplikace sady sestaví pouze aplikace a sestavení třetích stran s očekáváním, že v klientském počítači budou k dispozici knihovny .NET runtime a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-106">In this scenario, the application developer bundles only the application and third-party assemblies with the expectation that the .NET runtime and framework libraries will be available in the client machine.</span></span> <span data-ttu-id="8b9d9-107">Tento model nasazení se v .NET Core i nadále považuje za dominantní, ale existují scénáře, kdy model závislý na rozhraní není optimální.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-107">This deployment model continues to be the dominant one in .NET Core as well but there are some scenarios where the framework-dependent model is not optimal.</span></span> <span data-ttu-id="8b9d9-108">Alternativou je publikování [samostatné aplikace](index.md#publish-self-contained), kde se modul runtime .NET Core a rozhraní seskupí spolu s aplikacemi a sestaveními třetích stran.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-108">The alternative is to publish a [self-contained application](index.md#publish-self-contained), where the .NET Core runtime and framework are bundled together with the application and third-party assemblies.</span></span>

<span data-ttu-id="8b9d9-109">Model nasazení Trim – samostatně zahrnutý je specializovaná verze modelu nasazení, která je optimalizována pro snížení velikosti nasazení.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-109">The trim-self-contained deployment model is a specialized version of the self-contained deployment model that is optimized to reduce deployment size.</span></span> <span data-ttu-id="8b9d9-110">Minimalizace velikosti nasazení je zásadním požadavkem pro některé scénáře na straně klienta, jako jsou Blazor aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-110">Minimizing deployment size is a critical requirement for some client-side scenarios like Blazor applications.</span></span> <span data-ttu-id="8b9d9-111">V závislosti na složitosti aplikace je odkazována pouze podmnožina sestavení rozhraní a podmnožina kódu v rámci každého sestavení je nutná ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-111">Depending on the complexity of the application, only a subset of the framework assemblies are referenced, and a subset of the code within each assembly is required to run the application.</span></span> <span data-ttu-id="8b9d9-112">Nepoužívané části knihoven nejsou zbytečné a je možné je z zabalených aplikací oříznout.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-112">The unused parts of the libraries are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="8b9d9-113">Nicméně existuje riziko, že analýza času sestavení aplikace může způsobit selhání za běhu, protože není schopná spolehlivě analyzovat různé problematické vzorce kódu (v podstatě na střed, na kterém je reflexe použito).</span><span class="sxs-lookup"><span data-stu-id="8b9d9-113">However, there is a risk that the build time analysis of the application can cause failures at runtime, due to not being able to reliably analyze various problematic code patterns (largely centered on reflection use).</span></span> <span data-ttu-id="8b9d9-114">Vzhledem k tomu, že spolehlivost nejde zaručit, tento model nasazení se nabízí jako funkce ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-114">Because reliability can't be guaranteed, this deployment model is offered as a preview feature.</span></span>

<span data-ttu-id="8b9d9-115">Modul analýzy času sestavení poskytuje upozornění vývojářům vzorů kódu, které jsou problemmatic k zjištění, který jiný kód je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-115">The build time analysis engine provides warnings to the developer of code patterns that are problemmatic to detect which other code is required.</span></span> <span data-ttu-id="8b9d9-116">Kód lze opatřit poznámkami pomocí atributů a sdělit tak oříznutí, které další mají zahrnout.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-116">Code can be annotated with attributes to tell the trimmer what else to include.</span></span> <span data-ttu-id="8b9d9-117">Mnoho vzorů reflexe lze nahradit generováním kódu při sestavení pomocí [zdrojových generátorů](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md).</span><span class="sxs-lookup"><span data-stu-id="8b9d9-117">Many reflection patterns can be replaced with build-time code generation using [Source Generators](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md).</span></span>

<span data-ttu-id="8b9d9-118">Režim ořezávání pro aplikace je nakonfigurován s `TrimMode` nastavením.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-118">The trim mode for the applications is configured with the `TrimMode` setting.</span></span> <span data-ttu-id="8b9d9-119">Výchozí hodnota je `copyused` a sady odkazují na sestavení s aplikací.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-119">The default value is `copyused` and bundles referenced assemblies with the application.</span></span> <span data-ttu-id="8b9d9-120">`link`Hodnota se používá s Blazor aplikacemi WebAssembly a ořízne nepoužitý kód v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-120">The `link` value is used with Blazor WebAssembly applications and trims unused code within assemblies.</span></span> <span data-ttu-id="8b9d9-121">Upozornění analýzy střihu poskytují informace o vzorech kódu, u kterých není možné provést úplnou analýzu závislostí.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-121">Trim analysis warnings give information on code patterns where a full dependency analysis was not possible.</span></span> <span data-ttu-id="8b9d9-122">Tato upozornění se ve výchozím nastavení potlačí a dají se zapnout nastavením příznaku `SuppressTrimAnalysisWarnings` na `false` .</span><span class="sxs-lookup"><span data-stu-id="8b9d9-122">These warnings are suppressed by default and can be turned on by setting the flag `SuppressTrimAnalysisWarnings` to `false`.</span></span> <span data-ttu-id="8b9d9-123">Další informace o dostupných možnostech ořezávání najdete na [stránce ILLinker](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span><span class="sxs-lookup"><span data-stu-id="8b9d9-123">For more information about the trim options available, see the [ILLinker page](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8b9d9-124">Ořezávání je experimentální funkce v rozhraní .NET Core 3,1, 5,0 a je dostupná _pouze_ pro aplikace, které jsou publikovány samostatně.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-124">Trimming is an experimental feature in .NET Core 3.1, 5.0 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="8b9d9-125">Zabránit oříznutí sestavení</span><span class="sxs-lookup"><span data-stu-id="8b9d9-125">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="8b9d9-126">Existují scénáře, ve kterých funkce ořezávání nedokáže detekovat odkazy.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-126">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="8b9d9-127">Například pokud se reflexe používá v sestavení modulu runtime, buď vaší aplikací, nebo knihovnou, na kterou odkazuje vaše aplikace, sestavení není přímo odkazováno.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-127">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="8b9d9-128">Ořezávání neví o těchto nepřímých odkazech a vyloučí knihovnu z publikované složky.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-128">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="8b9d9-129">Pokud kód nepřímo odkazuje na sestavení prostřednictvím reflexe, můžete zabránit oříznutí sestavení s `<TrimmerRootAssembly>` nastavením.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-129">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="8b9d9-130">Následující příklad ukazuje, jak zabránit oříznutí sestavení nazývaného `System.Security` sestavení:</span><span class="sxs-lookup"><span data-stu-id="8b9d9-130">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="8b9d9-131">Stříhání aplikace – CLI</span><span class="sxs-lookup"><span data-stu-id="8b9d9-131">Trim your app - CLI</span></span>

<span data-ttu-id="8b9d9-132">Aplikaci ořízněte pomocí příkazu [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="8b9d9-132">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="8b9d9-133">Při publikování aplikace nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="8b9d9-133">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="8b9d9-134">Publikovat jako samostatně uzavřenou aplikaci pro konkrétní modul runtime: `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="8b9d9-134">Publish as a self-contained app for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="8b9d9-135">Povolit oříznutí: `/p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="8b9d9-135">Enable trimming: `/p:PublishTrimmed=true`</span></span>

<span data-ttu-id="8b9d9-136">Následující příklad publikuje aplikaci pro Windows jako samostatně obsaženou a ořízne výstup.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-136">The following example publishes an app for Windows as self-contained and trims the output.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

<span data-ttu-id="8b9d9-137">Následující příklad publikuje aplikaci v agresivním režimu střihu, kdy se nepoužívaný kód v sestaveních ořízne a jsou povolena upozornění ořezávání.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-137">The following example publishes an app in the aggressive trim mode where unused code within assemblies will be trimmed and trimmer warnings enabled.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</PropertyGroup>
```

<span data-ttu-id="8b9d9-138">Další informace najdete v tématu [publikování aplikací .NET Core pomocí .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="8b9d9-138">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="8b9d9-139">Střih aplikace – Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8b9d9-139">Trim your app - Visual Studio</span></span>

<span data-ttu-id="8b9d9-140">Visual Studio vytvoří opakovaně použitelné publikační profily, které určují, jak je vaše aplikace publikovaná.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-140">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="8b9d9-141">V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt, který chcete publikovat.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-141">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="8b9d9-142">Vybrat **publikování...**.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-142">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Průzkumník řešení pomocí nabídky po kliknutí pravým tlačítkem myši zvýraznění možnosti Publikovat.":::

    <span data-ttu-id="8b9d9-144">Pokud ještě nemáte profil publikování, postupujte podle pokynů, abyste ho vytvořili, a vyberte cílový typ **složky** .</span><span class="sxs-lookup"><span data-stu-id="8b9d9-144">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="8b9d9-145">Klikněte na tlačítko **Upravit**.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-145">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Publikovat profil sady Visual Studio s tlačítkem Upravit":::

01. <span data-ttu-id="8b9d9-147">V dialogovém okně **nastavení profilu** nastavte následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="8b9d9-147">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="8b9d9-148">Nastavte **režim nasazení** na **samostatné**.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-148">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="8b9d9-149">Nastavte **cílový modul runtime** na platformu, do které chcete publikovat.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-149">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="8b9d9-150">Vyberte **oříznout nepoužívaná sestavení (ve verzi Preview)**.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-150">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="8b9d9-151">Kliknutím na **Uložit** uložte nastavení a vraťte se do dialogového okna pro **publikování** .</span><span class="sxs-lookup"><span data-stu-id="8b9d9-151">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Dialogové okno nastavení profilu s vybraným režimem nasazení, cílovým modulem runtime a oříznout nepoužité možnosti sestavení":::

01. <span data-ttu-id="8b9d9-153">Kliknutím na **publikovat** publikujte aplikaci oříznutou.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-153">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="8b9d9-154">Další informace najdete v tématu [publikování aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8b9d9-154">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="8b9d9-155">Stříhání aplikace – Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="8b9d9-155">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="8b9d9-156">Visual Studio pro Mac neposkytuje možnosti pro oříznutí vaší aplikace během publikování.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-156">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="8b9d9-157">Podle pokynů v oddílu [vystřihování rozhraní CLI aplikace](#trim-your-app---cli) budete muset publikovat ručně.</span><span class="sxs-lookup"><span data-stu-id="8b9d9-157">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="8b9d9-158">Další informace najdete v tématu [publikování aplikací .NET Core pomocí .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="8b9d9-158">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b9d9-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b9d9-159">See also</span></span>

- <span data-ttu-id="8b9d9-160">[Nasazení aplikace .NET Core](index.md)</span><span class="sxs-lookup"><span data-stu-id="8b9d9-160">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="8b9d9-161">[Publikování aplikací .NET Core pomocí .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="8b9d9-161">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="8b9d9-162">[Publikování aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md)</span><span class="sxs-lookup"><span data-stu-id="8b9d9-162">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="8b9d9-163">[dotnet Publish příkaz](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="8b9d9-163">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
