---
title: Oříznutí samostatných aplikací
description: Přečtěte si, jak oříznout samostatné aplikace, aby se zmenšila jejich velikost. .NET Core sdružuje runtime s aplikací, která je publikována samostatně a obecně obsahuje více runtime pak je nezbytné.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242900"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="f5170-104">Odebrání nechtěných součástí a zachování pouze samostatně nasaditelných součástí a spustitelných souborů</span><span class="sxs-lookup"><span data-stu-id="f5170-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="f5170-105">Při publikování samostatné aplikace je runtime .NET Core dodáván společně s aplikací.</span><span class="sxs-lookup"><span data-stu-id="f5170-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="f5170-106">Toto sdružování přidá značné množství obsahu do vaší balené aplikace.</span><span class="sxs-lookup"><span data-stu-id="f5170-106">This bundling adds a significant amount of content to your packaged application.</span></span> <span data-ttu-id="f5170-107">Pokud jde o nasazení aplikace, velikost je často důležitým faktorem.</span><span class="sxs-lookup"><span data-stu-id="f5170-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="f5170-108">Zachování velikosti aplikace balíčku co nejmenší je obvykle cílem pro vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="f5170-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="f5170-109">V závislosti na složitosti aplikace je ke spuštění aplikace vyžadována pouze podmnožina runtime.</span><span class="sxs-lookup"><span data-stu-id="f5170-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="f5170-110">Tyto nepoužívané části runtime jsou zbytečné a lze je oříznout z balené aplikace.</span><span class="sxs-lookup"><span data-stu-id="f5170-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="f5170-111">Funkce oříznutí funguje tak, že zkoumá binární soubory aplikace, aby zjistila a vytvořila graf požadovaných sestav za běhu.</span><span class="sxs-lookup"><span data-stu-id="f5170-111">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="f5170-112">Zbývající sestavení za běhu, na která se neodkazuje, jsou vyloučena.</span><span class="sxs-lookup"><span data-stu-id="f5170-112">The remaining runtime assemblies that aren't referenced are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="f5170-113">Oříznutí je experimentální funkce v rozhraní .NET Core 3.1 a je k dispozici _pouze_ pro aplikace, které jsou publikovány samostatně.</span><span class="sxs-lookup"><span data-stu-id="f5170-113">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="f5170-114">Zabránit oříznutí sestav</span><span class="sxs-lookup"><span data-stu-id="f5170-114">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="f5170-115">Existují scénáře, ve kterých funkce oříznutí se nezdaří rozpoznat odkazy.</span><span class="sxs-lookup"><span data-stu-id="f5170-115">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="f5170-116">Například při odrazu se používá v sestavení za běhu, buď aplikace nebo knihovny, která je odkazována vaší aplikací, sestavení není přímo odkazuje.</span><span class="sxs-lookup"><span data-stu-id="f5170-116">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="f5170-117">Oříznutí není vědoma těchto nepřímých odkazů a by vyloučit knihovnu z publikované složky.</span><span class="sxs-lookup"><span data-stu-id="f5170-117">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="f5170-118">Pokud kód nepřímo odkazuje na sestavení prostřednictvím reflexe, můžete zabránit oříznutí `<TrimmerRootAssembly>` sestavení s nastavením.</span><span class="sxs-lookup"><span data-stu-id="f5170-118">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="f5170-119">Následující příklad ukazuje, jak zabránit `System.Security` oříznutí sestavení nazývaného sestavení:</span><span class="sxs-lookup"><span data-stu-id="f5170-119">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="f5170-120">Oříznutí aplikace – CLI</span><span class="sxs-lookup"><span data-stu-id="f5170-120">Trim your app - CLI</span></span>

<span data-ttu-id="f5170-121">Ořízněte aplikaci pomocí příkazu [dotnet publish.](../tools/dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="f5170-121">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="f5170-122">Při publikování aplikace nastavte následující tři nastavení:</span><span class="sxs-lookup"><span data-stu-id="f5170-122">When you publish your app, set the following three settings:</span></span>

- <span data-ttu-id="f5170-123">Publikovat jako samostatné:`--self-contained true`</span><span class="sxs-lookup"><span data-stu-id="f5170-123">Publish as self-contained: `--self-contained true`</span></span>
- <span data-ttu-id="f5170-124">Zakázat publikování na jednom souboru:`-p:PublishSingleFile=false`</span><span class="sxs-lookup"><span data-stu-id="f5170-124">Disable single-file publishing: `-p:PublishSingleFile=false`</span></span>
- <span data-ttu-id="f5170-125">Povolit oříznutí:`p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="f5170-125">Enable trimming: `p:PublishTrimmed=true`</span></span>

<span data-ttu-id="f5170-126">Následující příklad publikuje aplikaci pro Windows 10 jako samostatnou a ořízne výstup.</span><span class="sxs-lookup"><span data-stu-id="f5170-126">The following example publishes an app for Windows 10 as self-contained and trims the output.</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

<span data-ttu-id="f5170-127">Další informace naleznete v [tématu Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="f5170-127">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="f5170-128">Oříznutí aplikace – Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f5170-128">Trim your app - Visual Studio</span></span>

<span data-ttu-id="f5170-129">Visual Studio vytvoří opakovaně použitelné publikování profily, které řídí, jak je vaše aplikace publikována.</span><span class="sxs-lookup"><span data-stu-id="f5170-129">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="f5170-130">V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt, který chcete publikovat.</span><span class="sxs-lookup"><span data-stu-id="f5170-130">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="f5170-131">Vyberte **Publikovat...**.</span><span class="sxs-lookup"><span data-stu-id="f5170-131">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Průzkumník řešení s nabídkou po kliknutí pravým tlačítkem myši zvýrazňující možnost Publikovat.":::

    <span data-ttu-id="f5170-133">Pokud ještě nemáte profil publikování, postupujte podle pokynů k jeho vytvoření a zvolte typ cíle **složky.**</span><span class="sxs-lookup"><span data-stu-id="f5170-133">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="f5170-134">Zvolte **Upravit**.</span><span class="sxs-lookup"><span data-stu-id="f5170-134">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual studio publikuje profil pomocí tlačítka upravit.":::

01. <span data-ttu-id="f5170-136">V dialogovém okně **Nastavení profilu** nastavte následující volby:</span><span class="sxs-lookup"><span data-stu-id="f5170-136">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="f5170-137">Nastavte **režim nasazení** na samostatný **.**</span><span class="sxs-lookup"><span data-stu-id="f5170-137">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="f5170-138">Nastavte **cílový čas runtime** na platformu, na kterou chcete publikovat.</span><span class="sxs-lookup"><span data-stu-id="f5170-138">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="f5170-139">Vyberte **Oříznout nepoužité sestavy (v náhledu).**</span><span class="sxs-lookup"><span data-stu-id="f5170-139">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="f5170-140">Zvolte **Uložit,** chcete-li uložit nastavení a vrátit se do dialogového okna **Publikovat.**</span><span class="sxs-lookup"><span data-stu-id="f5170-140">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Dialogové okno nastavení profilu se zvýrazněným režimem nasazení, cílovým časem běhu a oříznutím nepoužívaných sestav.":::

01. <span data-ttu-id="f5170-142">Zvolte **Publikovat,** chcete-li aplikaci publikovat oříznutou.</span><span class="sxs-lookup"><span data-stu-id="f5170-142">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="f5170-143">Další informace najdete [v tématu Publikování aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f5170-143">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="f5170-144">Oříznutí aplikace – Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="f5170-144">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="f5170-145">Visual Studio pro Mac neposkytuje možnosti, jak aplikaci během publikování oříznout.</span><span class="sxs-lookup"><span data-stu-id="f5170-145">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="f5170-146">Budete muset publikovat ručně podle pokynů v části [Oříznout aplikaci – CLI.](#trim-your-app---cli)</span><span class="sxs-lookup"><span data-stu-id="f5170-146">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="f5170-147">Další informace naleznete v [tématu Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="f5170-147">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5170-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5170-148">See also</span></span>

- <span data-ttu-id="f5170-149">[Nasazení základní aplikace .NET](index.md).</span><span class="sxs-lookup"><span data-stu-id="f5170-149">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="f5170-150">[Publikování aplikací .NET Core pomocí rozhraní CLI jádra .NET](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="f5170-150">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="f5170-151">[Publikujte aplikace .NET Core pomocí sady Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f5170-151">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="f5170-152">[dotnet publish , příkaz](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="f5170-152">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
