---
title: Oříznout samostatně obsažené aplikace
description: Naučte se oříznout samostatné aplikace a zmenšit jejich velikost. .NET Core obsahuje modul runtime s aplikací, která je publikovaná samostatně a obecně zahrnuje více prostředí runtime, a je to nezbytné.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 0fde409e9e5911213855ab206368d302b73eebb3
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720121"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="7ef00-104">Odebrání nechtěných součástí a zachování pouze samostatně nasaditelných součástí a spustitelných souborů</span><span class="sxs-lookup"><span data-stu-id="7ef00-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="7ef00-105">[Model nasazení závislý na rozhraní](index.md#publish-framework-dependent) byl nejaktivnějším modelem nasazení od okamžiku spuštění .NET.</span><span class="sxs-lookup"><span data-stu-id="7ef00-105">The [framework-dependent deployment model](index.md#publish-framework-dependent) has been the most successful deployment model since the inception of .NET.</span></span> <span data-ttu-id="7ef00-106">V tomto scénáři vývojář aplikace sady sestaví pouze aplikace a sestavení třetích stran s očekáváním, že v klientském počítači budou k dispozici knihovny .NET runtime a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7ef00-106">In this scenario, the application developer bundles only the application and third-party assemblies with the expectation that the .NET runtime and framework libraries will be available in the client machine.</span></span> <span data-ttu-id="7ef00-107">Tento model nasazení se v .NET Core i nadále považuje za dominantní, ale existují scénáře, kdy model závislý na rozhraní není optimální.</span><span class="sxs-lookup"><span data-stu-id="7ef00-107">This deployment model continues to be the dominant one in .NET Core as well but there are some scenarios where the framework-dependent model is not optimal.</span></span> <span data-ttu-id="7ef00-108">Alternativou je publikování [samostatné aplikace](index.md#publish-self-contained), kde se modul runtime .NET Core a rozhraní seskupí spolu s aplikacemi a sestaveními třetích stran.</span><span class="sxs-lookup"><span data-stu-id="7ef00-108">The alternative is to publish a [self-contained application](index.md#publish-self-contained), where the .NET Core runtime and framework are bundled together with the application and third-party assemblies.</span></span>

<span data-ttu-id="7ef00-109">Model nasazení Trim – samostatně zahrnutý je specializovaná verze modelu nasazení, která je optimalizována pro snížení velikosti nasazení.</span><span class="sxs-lookup"><span data-stu-id="7ef00-109">The trim-self-contained deployment model is a specialized version of the self-contained deployment model that is optimized to reduce deployment size.</span></span> <span data-ttu-id="7ef00-110">Minimalizace velikosti nasazení je zásadním požadavkem pro některé scénáře na straně klienta, jako jsou Blazor aplikace.</span><span class="sxs-lookup"><span data-stu-id="7ef00-110">Minimizing deployment size is a critical requirement for some client-side scenarios like Blazor applications.</span></span> <span data-ttu-id="7ef00-111">V závislosti na složitosti aplikace je pro spuštění aplikace nutná pouze podmnožina sestavení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7ef00-111">Depending on the complexity of the application, only a subset of the framework assemblies is required to run the application.</span></span> <span data-ttu-id="7ef00-112">Tyto nepoužívané části knihovny jsou zbytečné a je možné je z zabalených aplikací oříznout.</span><span class="sxs-lookup"><span data-stu-id="7ef00-112">These unused parts of the library are unnecessary and can be trimmed from the packaged application.</span></span> <span data-ttu-id="7ef00-113">Nicméně existuje riziko, že analýza času sestavení aplikace může způsobit selhání za běhu, protože není schopná spolehlivě analyzovat různé problematické vzorce kódu (v podstatě na střed, na kterém je reflexe použito).</span><span class="sxs-lookup"><span data-stu-id="7ef00-113">However, there is a risk that the build time analysis of the application can cause failures at runtime, due to not being able to reliably analyze various problematic code patterns (largely centered on reflection use).</span></span> <span data-ttu-id="7ef00-114">Vzhledem k tomu, že spolehlivost nejde zaručit, tento model nasazení se nabízí jako funkce ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="7ef00-114">Because reliability can't be guaranteed, this deployment model is offered as a preview feature.</span></span> <span data-ttu-id="7ef00-115">Modul analýzy času sestavení poskytuje upozornění vývojářům vzorů kódu, které jsou problematické, a očekává se, že tyto vzory kódu budou opraveny.</span><span class="sxs-lookup"><span data-stu-id="7ef00-115">The build time analysis engine provides warnings to the developer of code patterns that are problematic, with the expectation that these code patterns will be fixed.</span></span> <span data-ttu-id="7ef00-116">Pokud je to možné, doporučujeme, abyste přesunuli všechny závislosti na reflexi modulu runtime v aplikaci na čas sestavení pomocí kódu, který splňuje stejné požadavky.</span><span class="sxs-lookup"><span data-stu-id="7ef00-116">Where possible, we recommend that you move any runtime reflection dependencies in your application to build time by using code that meets the same requirements.</span></span>

<span data-ttu-id="7ef00-117">Režim ořezávání pro aplikace lze konfigurovat prostřednictvím TrimMode a ve výchozím nastavení ( `copyused` ) pro sestavení sady prostředků, které se používají v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7ef00-117">The trim mode for the applications can be configured via the TrimMode and will default (`copyused`) to bundle assemblies that are used in the application.</span></span> <span data-ttu-id="7ef00-118">Blazor aplikace WebAssembly budou používat účinnější režim ( `link` ), který ořízne nepoužitý kód v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="7ef00-118">Blazor WebAssembly applications will use a more aggressive mode (`link`) that will trim unused code within assemblies.</span></span> <span data-ttu-id="7ef00-119">Upozornění analýzy střihu poskytují informace o vzorech kódu, u kterých není možné provést úplnou analýzu závislostí.</span><span class="sxs-lookup"><span data-stu-id="7ef00-119">Trim analysis warnings give information on code patterns where a full dependency analysis was not possible.</span></span> <span data-ttu-id="7ef00-120">Tato upozornění se ve výchozím nastavení potlačí a dají se zapnout nastavením příznaku `SuppressTrimAnalysisWarnings` na false.</span><span class="sxs-lookup"><span data-stu-id="7ef00-120">These warnings are suppressed by default and can be turned on by setting the flag, `SuppressTrimAnalysisWarnings`, to false.</span></span> <span data-ttu-id="7ef00-121">Další informace o dostupných možnostech ořezávání najdete na [stránce ILLinker](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span><span class="sxs-lookup"><span data-stu-id="7ef00-121">More information on the trim options available can be found at the [ILLinker page](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7ef00-122">Ořezávání je experimentální funkce v rozhraní .NET Core 3,1, 5,0 a je dostupná _pouze_ pro aplikace, které jsou publikovány samostatně.</span><span class="sxs-lookup"><span data-stu-id="7ef00-122">Trimming is an experimental feature in .NET Core 3.1, 5.0 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="7ef00-123">Zabránit oříznutí sestavení</span><span class="sxs-lookup"><span data-stu-id="7ef00-123">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="7ef00-124">Existují scénáře, ve kterých funkce ořezávání nedokáže detekovat odkazy.</span><span class="sxs-lookup"><span data-stu-id="7ef00-124">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="7ef00-125">Například pokud se reflexe používá v sestavení modulu runtime, buď vaší aplikací, nebo knihovnou, na kterou odkazuje vaše aplikace, sestavení není přímo odkazováno.</span><span class="sxs-lookup"><span data-stu-id="7ef00-125">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="7ef00-126">Ořezávání neví o těchto nepřímých odkazech a vyloučí knihovnu z publikované složky.</span><span class="sxs-lookup"><span data-stu-id="7ef00-126">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="7ef00-127">Pokud kód nepřímo odkazuje na sestavení prostřednictvím reflexe, můžete zabránit oříznutí sestavení s `<TrimmerRootAssembly>` nastavením.</span><span class="sxs-lookup"><span data-stu-id="7ef00-127">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="7ef00-128">Následující příklad ukazuje, jak zabránit oříznutí sestavení nazývaného `System.Security` sestavení:</span><span class="sxs-lookup"><span data-stu-id="7ef00-128">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="7ef00-129">Stříhání aplikace – CLI</span><span class="sxs-lookup"><span data-stu-id="7ef00-129">Trim your app - CLI</span></span>

<span data-ttu-id="7ef00-130">Aplikaci ořízněte pomocí příkazu [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="7ef00-130">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="7ef00-131">Při publikování aplikace nastavte následující tři nastavení:</span><span class="sxs-lookup"><span data-stu-id="7ef00-131">When you publish your app, set the following three settings:</span></span>

- <span data-ttu-id="7ef00-132">Publikovat jako samostatnou: `--self-contained true`</span><span class="sxs-lookup"><span data-stu-id="7ef00-132">Publish as self-contained: `--self-contained true`</span></span>
- <span data-ttu-id="7ef00-133">Povolit oříznutí: `p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="7ef00-133">Enable trimming: `p:PublishTrimmed=true`</span></span>

<span data-ttu-id="7ef00-134">Následující příklad publikuje aplikaci pro Windows jako samostatně obsaženou a ořízne výstup.</span><span class="sxs-lookup"><span data-stu-id="7ef00-134">The following example publishes an app for Windows as self-contained and trims the output.</span></span>

```xml
<ItemGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <PublishTrimmed>true</PublishTrimmed>
</ItemGroup>
```

<span data-ttu-id="7ef00-135">Následující příklad publikuje aplikaci v agresivním režimu střihu, kdy se nepoužívaný kód v sestaveních ořízne a jsou povolena upozornění ořezávání.</span><span class="sxs-lookup"><span data-stu-id="7ef00-135">The following example publishes an app in the aggressive trim mode where unused code within assemblies will be trimmed and  trimmer warnings enabled.</span></span>

```xml
<ItemGroup>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</ItemGroup>
```

<span data-ttu-id="7ef00-136">Další informace najdete v tématu [publikování aplikací .NET Core pomocí .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="7ef00-136">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="7ef00-137">Střih aplikace – Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7ef00-137">Trim your app - Visual Studio</span></span>

<span data-ttu-id="7ef00-138">Visual Studio vytvoří opakovaně použitelné publikační profily, které určují, jak je vaše aplikace publikovaná.</span><span class="sxs-lookup"><span data-stu-id="7ef00-138">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="7ef00-139">V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt, který chcete publikovat.</span><span class="sxs-lookup"><span data-stu-id="7ef00-139">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="7ef00-140">Vybrat **publikování...**.</span><span class="sxs-lookup"><span data-stu-id="7ef00-140">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Průzkumník řešení pomocí nabídky po kliknutí pravým tlačítkem myši zvýraznění možnosti Publikovat.":::

    <span data-ttu-id="7ef00-142">Pokud ještě nemáte profil publikování, postupujte podle pokynů, abyste ho vytvořili, a vyberte cílový typ **složky** .</span><span class="sxs-lookup"><span data-stu-id="7ef00-142">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="7ef00-143">Klikněte na tlačítko **Upravit**.</span><span class="sxs-lookup"><span data-stu-id="7ef00-143">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Publikovat profil sady Visual Studio s tlačítkem Upravit":::

01. <span data-ttu-id="7ef00-145">V dialogovém okně **nastavení profilu** nastavte následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="7ef00-145">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="7ef00-146">Nastavte **režim nasazení** na **samostatné**.</span><span class="sxs-lookup"><span data-stu-id="7ef00-146">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="7ef00-147">Nastavte **cílový modul runtime** na platformu, do které chcete publikovat.</span><span class="sxs-lookup"><span data-stu-id="7ef00-147">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="7ef00-148">Vyberte **oříznout nepoužívaná sestavení (ve verzi Preview)**.</span><span class="sxs-lookup"><span data-stu-id="7ef00-148">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="7ef00-149">Kliknutím na **Uložit** uložte nastavení a vraťte se do dialogového okna pro **publikování** .</span><span class="sxs-lookup"><span data-stu-id="7ef00-149">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Dialogové okno nastavení profilu s vybraným režimem nasazení, cílovým modulem runtime a oříznout nepoužité možnosti sestavení":::

01. <span data-ttu-id="7ef00-151">Kliknutím na **publikovat** publikujte aplikaci oříznutou.</span><span class="sxs-lookup"><span data-stu-id="7ef00-151">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="7ef00-152">Další informace najdete v tématu [publikování aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="7ef00-152">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="7ef00-153">Stříhání aplikace – Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="7ef00-153">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="7ef00-154">Visual Studio pro Mac neposkytuje možnosti pro oříznutí vaší aplikace během publikování.</span><span class="sxs-lookup"><span data-stu-id="7ef00-154">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="7ef00-155">Podle pokynů v oddílu [vystřihování rozhraní CLI aplikace](#trim-your-app---cli) budete muset publikovat ručně.</span><span class="sxs-lookup"><span data-stu-id="7ef00-155">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="7ef00-156">Další informace najdete v tématu [publikování aplikací .NET Core pomocí .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="7ef00-156">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ef00-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ef00-157">See also</span></span>

- <span data-ttu-id="7ef00-158">[Nasazení aplikace .NET Core](index.md)</span><span class="sxs-lookup"><span data-stu-id="7ef00-158">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="7ef00-159">[Publikování aplikací .NET Core pomocí .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="7ef00-159">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="7ef00-160">[Publikování aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md)</span><span class="sxs-lookup"><span data-stu-id="7ef00-160">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="7ef00-161">[dotnet Publish příkaz](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="7ef00-161">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
