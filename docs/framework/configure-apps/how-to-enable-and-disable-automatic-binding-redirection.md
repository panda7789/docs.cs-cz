---
title: 'Postupy: Povolení a zákaz automatického přesměrování vazby'
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d71da1b48938f9f98221d86f0f9badee3a17919
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757564"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="dcee5-102">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="dcee5-102">How to: Enable and Disable Automatic Binding Redirection</span></span>
<span data-ttu-id="dcee5-103">Počínaje [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], při kompilaci aplikace cílených [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], přesměrování vazby mohou být automaticky přidány do konfiguračního souboru aplikace k přepsání sjednocení sestavení.</span><span class="sxs-lookup"><span data-stu-id="dcee5-103">Starting with [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], when you compile apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="dcee5-104">Přesměrování vazby je přidáno, pokud vaše aplikace nebo její komponenty odkazují na více verzí stejného sestavení, i když ručně zadáte přesměrování vazby v konfiguračním souboru pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dcee5-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="dcee5-105">Funkce přesměrování vazby automatické ovlivňuje tradiční desktopové aplikace a webové aplikace cílených [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], i když toto chování je mírně odlišný pro webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dcee5-105">The automatic binding redirection feature affects traditional desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="dcee5-106">Pokud máte existující aplikace, které jsou určeny pro předchozí verze rozhraní .NET Framework, můžete povolit automatické přesměrování vazby nebo tuto funkci můžete zakázat, pokud chcete zachovat ručně vytvořená přesměrování vazby.</span><span class="sxs-lookup"><span data-stu-id="dcee5-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to keep manually authored binding redirects.</span></span>  
  
## <a name="disabling-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="dcee5-107">Zakázání automatické vazby přesměruje v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="dcee5-107">Disabling automatic binding redirects in desktop apps</span></span>  
 <span data-ttu-id="dcee5-108">Přesměrování vazby automatické jsou povolené ve výchozím nastavení tradiční aplikací klasické pracovní plochy, které cílí [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="dcee5-108">Automatic binding redirects are enabled by default for traditional desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="dcee5-109">Přesměrování vazby jsou přidána do výstupního souboru konfigurace (app.config) při kompilaci aplikace a přepíšou sjednocení sestavení, které jinak může probíhat.</span><span class="sxs-lookup"><span data-stu-id="dcee5-109">The binding redirects are added to the output configuration (app.config) file when the app is compiled and overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="dcee5-110">Zdrojový soubor app.config není změněn.</span><span class="sxs-lookup"><span data-stu-id="dcee5-110">The source app.config file is not modified.</span></span> <span data-ttu-id="dcee5-111">Tuto funkci můžete zakázat úpravou souboru projektu pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dcee5-111">You can disable this feature by modifying the project file for the app.</span></span>  
  
#### <a name="to-disable-automatic-binding-redirects"></a><span data-ttu-id="dcee5-112">Zakázání automatického přesměrování vazeb</span><span class="sxs-lookup"><span data-stu-id="dcee5-112">To disable automatic binding redirects</span></span>  
  
1.  <span data-ttu-id="dcee5-113">V sadě Visual Studio, vyberte na projekt v **Průzkumníku řešení**a potom zvolte **otevřít složku v Průzkumníku souborů** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="dcee5-113">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="dcee5-114">V Průzkumníku souborů vyhledejte soubor projektu (.csproj nebo .vbproj) a otevřete jej v programu Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="dcee5-114">In File Explorer, find the project (.csproj or .vbproj) file, and open it in Notepad.</span></span>  
  
3.  <span data-ttu-id="dcee5-115">V souboru projektu vyhledejte položku následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="dcee5-115">In the project file, find the following property entry:</span></span>  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  <span data-ttu-id="dcee5-116">Změna `true` k `false`:</span><span class="sxs-lookup"><span data-stu-id="dcee5-116">Change `true` to `false`:</span></span>  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## <a name="enabling-automatic-binding-redirects-manually"></a><span data-ttu-id="dcee5-117">Povolení automatického vazby přesměruje ručně</span><span class="sxs-lookup"><span data-stu-id="dcee5-117">Enabling automatic binding redirects manually</span></span>  
 <span data-ttu-id="dcee5-118">Můžete povolit přesměrování automatické vazby v existující aplikace tento cíl starší verze rozhraní .NET Framework, nebo v případech, kde se výzva automaticky přidat přesměrování.</span><span class="sxs-lookup"><span data-stu-id="dcee5-118">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you are not automatically prompted to add a redirect.</span></span> <span data-ttu-id="dcee5-119">Pokud jsou cílení na novější verzi rozhraní framework, ale výzva automaticky přidat přesměrování, zobrazí se pravděpodobně sestavení výstupu, který naznačuje, že přemapovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="dcee5-119">If you are targeting a newer version of the framework but do not get automatically prompted to add a redirect, you will likely get   build output that suggests you remap assemblies.</span></span>  
  
#### <a name="to-manually-add-an-automatic-binding-redirect-property"></a><span data-ttu-id="dcee5-120">Ruční přidání ve vlastnosti vazby automatické přesměrování</span><span class="sxs-lookup"><span data-stu-id="dcee5-120">To manually add an automatic binding redirect property</span></span>  
  
1.  <span data-ttu-id="dcee5-121">V sadě Visual Studio, vyberte na projekt v **Průzkumníku řešení**a potom zvolte **otevřít složku v Průzkumníku souborů** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="dcee5-121">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="dcee5-122">V Průzkumníku souborů vyhledejte soubor projektu (.csproj nebo .vbproj) a otevřete jej v programu Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="dcee5-122">In File Explorer, find the project (.csproj or .vbproj) file, and open it in Notepad.</span></span>  
  
3.  <span data-ttu-id="dcee5-123">Přidejte následující element ke skupině první vlastnost konfigurace (v části \<PropertyGroup > značka):</span><span class="sxs-lookup"><span data-stu-id="dcee5-123">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     <span data-ttu-id="dcee5-124">Na obrázku je příklad souboru projektu s elementem vložit.</span><span class="sxs-lookup"><span data-stu-id="dcee5-124">The following shows an example project file with the element inserted.</span></span>  
  
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
  
4.  <span data-ttu-id="dcee5-125">Zkompilujte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dcee5-125">Compile your app.</span></span>  
  
## <a name="enabling-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="dcee5-126">Povolení automatického přesměrování vazby ve webových aplikacích</span><span class="sxs-lookup"><span data-stu-id="dcee5-126">Enabling automatic binding redirects in web apps</span></span>  
 <span data-ttu-id="dcee5-127">Automatické přesměrování vazby je pro webové aplikace implementováno jinak.</span><span class="sxs-lookup"><span data-stu-id="dcee5-127">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="dcee5-128">Vzhledem k tomu, že je třeba upravit zdrojový soubor konfigurace (web.config) pro webové aplikace, přesměrování vazeb nejsou automaticky přidána do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="dcee5-128">Because the source configuration (web.config) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="dcee5-129">Sada Visual Studio vás však upozorní na konflikty ve vazbách a můžete tak pomocí přesměrování vazby tyto konflikty vyřešit.</span><span class="sxs-lookup"><span data-stu-id="dcee5-129">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="dcee5-130">Vzhledem k tomu, že se vždy zobrazí výzva k přidání přesměrování vazby, není nutné explicitně zakázat tuto funkci pro webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dcee5-130">Because you are always prompted to add binding redirects, you do not need to explicitly disable this feature for a web app.</span></span>  
  
#### <a name="to-add-binding-redirects-to-a-webconfig-file"></a><span data-ttu-id="dcee5-131">Přidání přesměrování vazeb v souboru web.config</span><span class="sxs-lookup"><span data-stu-id="dcee5-131">To add binding redirects to a web.config file</span></span>  
  
1.  <span data-ttu-id="dcee5-132">V sadě Visual Studio zkompilujte aplikaci a zkontrolujte upozornění na sestavení.</span><span class="sxs-lookup"><span data-stu-id="dcee5-132">In Visual Studio, compile the app, and check for build warnings.</span></span>  
  
     <span data-ttu-id="dcee5-133">![Sestavení upozornění konflikty odkaz na sestavení](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="dcee5-133">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>  
  
2.  <span data-ttu-id="dcee5-134">Pokud existují konflikty vazeb sestavení, zobrazí se upozornění.</span><span class="sxs-lookup"><span data-stu-id="dcee5-134">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="dcee5-135">Dvakrát klikněte na upozornění.</span><span class="sxs-lookup"><span data-stu-id="dcee5-135">Double-click the warning.</span></span> <span data-ttu-id="dcee5-136">(Klávesové: Vyberte upozornění a stiskněte klávesu **Enter**.)</span><span class="sxs-lookup"><span data-stu-id="dcee5-136">(Keyboard: Select the warning and press **Enter**.)</span></span>  
  
     <span data-ttu-id="dcee5-137">Zobrazí se dialogové okno, které umožňuje automaticky přidat nezbytná přesměrování vazby na zdrojový soubor web.config.</span><span class="sxs-lookup"><span data-stu-id="dcee5-137">A dialog box that enables you to automatically add the necessary binding redirects to the source web.config file appears.</span></span>  
  
     <span data-ttu-id="dcee5-138">![Dialogové okno oprávnění přesměrování vazby](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="dcee5-138">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcee5-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcee5-139">See Also</span></span>  
 [<span data-ttu-id="dcee5-140">\<bindingRedirect – > elementu</span><span class="sxs-lookup"><span data-stu-id="dcee5-140">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [<span data-ttu-id="dcee5-141">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="dcee5-141">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
