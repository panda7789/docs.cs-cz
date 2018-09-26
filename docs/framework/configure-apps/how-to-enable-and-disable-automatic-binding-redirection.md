---
title: 'Postupy: Povolení a zákaz automatického přesměrování vazby'
ms.date: 09/12/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9b9c9cbdb89ccf67942dcccee37ea410c6fa39a5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208669"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="505fc-102">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="505fc-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="505fc-103">Při sestavování aplikací v sadě Visual Studio, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a novější verze, přesměrování vazby může automaticky přidá do konfiguračního souboru aplikace pro přepsání sjednocení sestavení.</span><span class="sxs-lookup"><span data-stu-id="505fc-103">When you compile apps in Visual Studio that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="505fc-104">Přesměrování vazby je přidáno, pokud vaše aplikace nebo její komponenty odkazují na více verzí stejného sestavení, i když ručně zadáte přesměrování vazby v konfiguračním souboru pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="505fc-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="505fc-105">Funkce automatického přesměrování vazby ovlivňuje aplikace klasické pracovní plochy a webové aplikace, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] nebo novější verze, ačkoli chování se mírně liší pro webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="505fc-105">The automatic binding redirection feature affects traditional desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="505fc-106">Pokud máte existující aplikace, které jsou určeny pro předchozí verze rozhraní .NET Framework, můžete povolit automatické přesměrování vazby nebo tuto funkci můžete zakázat, pokud chcete zachovat ručně vytvořená přesměrování vazby.</span><span class="sxs-lookup"><span data-stu-id="505fc-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to keep manually authored binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="505fc-107">Zakázat automatické přesměrování vazby v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="505fc-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="505fc-108">Automatické přesměrování vazeb je povoleno standardně pro tradiční stolní aplikace, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="505fc-108">Automatic binding redirects are enabled by default for traditional desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="505fc-109">Přesměrování vazby jsou přidána do výstupního souboru konfigurace (app.config) při kompilaci aplikace a přepíšou sjednocení sestavení, které jinak může probíhat.</span><span class="sxs-lookup"><span data-stu-id="505fc-109">The binding redirects are added to the output configuration (app.config) file when the app is compiled and overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="505fc-110">Zdrojový soubor app.config není změněn.</span><span class="sxs-lookup"><span data-stu-id="505fc-110">The source app.config file is not modified.</span></span> <span data-ttu-id="505fc-111">Tuto funkci můžete zakázat úpravou souboru projektu pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="505fc-111">You can disable this feature by modifying the project file for the app.</span></span>

1. <span data-ttu-id="505fc-112">Otevřete soubor projektu s možností úprav pomocí jedné z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="505fc-112">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="505fc-113">V sadě Visual Studio vyberte projekt v **Průzkumníka řešení**a klikněte na tlačítko **otevřít složku v Průzkumníku souborů** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="505fc-113">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="505fc-114">V Průzkumníku souborů vyhledejte soubor projektu (.csproj nebo .vbproj) a otevřete v poznámkovém bloku.</span><span class="sxs-lookup"><span data-stu-id="505fc-114">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="505fc-115">V sadě Visual Studio v **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a zvolte **uvolnit projekt**.</span><span class="sxs-lookup"><span data-stu-id="505fc-115">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="505fc-116">Znovu klikněte pravým tlačítkem na projekt uvolněn a klikněte na tlačítko **upravit [projectname.csproj]**.</span><span class="sxs-lookup"><span data-stu-id="505fc-116">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="505fc-117">V souboru projektu vyhledejte položku následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="505fc-117">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="505fc-118">Změna `true` k `false`:</span><span class="sxs-lookup"><span data-stu-id="505fc-118">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="505fc-119">Ručně povolte automatické přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="505fc-119">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="505fc-120">Můžete povolit automatické přesměrování vazby v existujících aplikacích, které starší verze cílového rozhraní .NET Framework, nebo v případech, kde se zobrazí výzva k automaticky přidat přesměrování.</span><span class="sxs-lookup"><span data-stu-id="505fc-120">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="505fc-121">Pokud cílíte novější verzi rozhraní framework, ale se mi výzva automaticky přidat přesměrování, zobrazí se pravděpodobně výstup sestavení, který naznačuje, že přemapování sestavení.</span><span class="sxs-lookup"><span data-stu-id="505fc-121">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="505fc-122">Otevřete soubor projektu s možností úprav pomocí jedné z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="505fc-122">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="505fc-123">V sadě Visual Studio vyberte projekt v **Průzkumníka řešení**a klikněte na tlačítko **otevřít složku v Průzkumníku souborů** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="505fc-123">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="505fc-124">V Průzkumníku souborů vyhledejte soubor projektu (.csproj nebo .vbproj) a otevřete v poznámkovém bloku.</span><span class="sxs-lookup"><span data-stu-id="505fc-124">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="505fc-125">V sadě Visual Studio v **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a zvolte **uvolnit projekt**.</span><span class="sxs-lookup"><span data-stu-id="505fc-125">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="505fc-126">Znovu klikněte pravým tlačítkem na projekt uvolněn a klikněte na tlačítko **upravit [projectname.csproj]**.</span><span class="sxs-lookup"><span data-stu-id="505fc-126">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="505fc-127">Přidejte následující element do první skupiny vlastností konfigurace (pod \<PropertyGroup > značky):</span><span class="sxs-lookup"><span data-stu-id="505fc-127">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="505fc-128">Následuje příklad souboru projektu v prvku vložen:</span><span class="sxs-lookup"><span data-stu-id="505fc-128">The following shows an example project file with the element inserted:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
       <PropertyGroup>
         <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>
         <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
         <ProjectGuid>{123334}</ProjectGuid>
         ...
         <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
       </PropertyGroup>
     ...
   </Project>
   ```

3. <span data-ttu-id="505fc-129">Zkompilujte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="505fc-129">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="505fc-130">Povolit automatické přesměrování vazby ve službě web apps</span><span class="sxs-lookup"><span data-stu-id="505fc-130">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="505fc-131">Automatické přesměrování vazby je pro webové aplikace implementováno jinak.</span><span class="sxs-lookup"><span data-stu-id="505fc-131">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="505fc-132">Vzhledem k tomu, že je třeba upravit zdrojový soubor konfigurace (web.config) pro webové aplikace, přesměrování vazeb nejsou automaticky přidána do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="505fc-132">Because the source configuration (web.config) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="505fc-133">Sada Visual Studio vás však upozorní na konflikty ve vazbách a můžete tak pomocí přesměrování vazby tyto konflikty vyřešit.</span><span class="sxs-lookup"><span data-stu-id="505fc-133">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="505fc-134">Protože vždy zobrazí výzva k přidání přesměrování vazby, není nutné explicitně zakázat tuto funkci pro webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="505fc-134">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="505fc-135">Chcete-li přidat přesměrování vazby do souboru web.config:</span><span class="sxs-lookup"><span data-stu-id="505fc-135">To add binding redirects to a web.config file:</span></span>

1. <span data-ttu-id="505fc-136">V sadě Visual Studio zkompilujte aplikaci a zkontrolujte upozornění na sestavení.</span><span class="sxs-lookup"><span data-stu-id="505fc-136">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="505fc-137">![Vytváření upozornění pro sestavení odkazu konflikty](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="505fc-137">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="505fc-138">Pokud existují konflikty vazeb sestavení, zobrazí se upozornění.</span><span class="sxs-lookup"><span data-stu-id="505fc-138">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="505fc-139">Dvakrát klikněte na upozornění, nebo vyberte upozornění a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="505fc-139">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="505fc-140">Zobrazí se dialogové okno, které umožňuje automaticky přidat nezbytná přesměrování vazby na zdrojový soubor web.config.</span><span class="sxs-lookup"><span data-stu-id="505fc-140">A dialog box that enables you to automatically add the necessary binding redirects to the source web.config file appears.</span></span>

   <span data-ttu-id="505fc-141">![Dialogové okno oprávnění přesměrování vazby](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="505fc-141">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="505fc-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="505fc-142">See also</span></span>

- [<span data-ttu-id="505fc-143">\<bindingRedirect > – Element</span><span class="sxs-lookup"><span data-stu-id="505fc-143">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="505fc-144">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="505fc-144">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
