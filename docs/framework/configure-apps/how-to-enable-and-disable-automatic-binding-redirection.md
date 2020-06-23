---
title: Povolit nebo zakázat přesměrování automaticky generovaných vazeb
description: Přečtěte si, jak povolit nebo zakázat automatické přesměrování vazby. Tato funkce má vliv na desktopové aplikace a webové aplikace cílené na rozhraní .NET 4.5.1 nebo novější.
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: edee95f6c3b2c2d74c4f1b68e0a65e5cb0e85f54
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105386"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="774b4-104">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="774b4-104">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="774b4-105">Při kompilaci aplikací v aplikaci Visual Studio cílících na .NET Framework 4.5.1 a novějších verzích může být přesměrování vazby automaticky přidáno do konfiguračního souboru aplikace, aby bylo možné přepsat sjednocení sestavení.</span><span class="sxs-lookup"><span data-stu-id="774b4-105">When you compile apps in Visual Studio that target the .NET Framework 4.5.1 and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="774b4-106">Přesměrování vazby je přidáno, pokud vaše aplikace nebo její komponenty odkazují na více verzí stejného sestavení, i když ručně zadáte přesměrování vazby v konfiguračním souboru pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="774b4-106">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="774b4-107">Funkce automatického přesměrování vazby má vliv na desktopové aplikace a webové aplikace, které cílí na .NET Framework 4.5.1 nebo novější verzi, i když se chování u webové aplikace mírně liší.</span><span class="sxs-lookup"><span data-stu-id="774b4-107">The automatic binding redirection feature affects desktop apps and web apps that target the .NET Framework 4.5.1 or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="774b4-108">Pokud máte existující aplikace, které cílí na předchozí verze .NET Framework, můžete povolit automatické přesměrování vazby nebo tuto funkci můžete zakázat, pokud chcete ručně vytvořit přesměrování vazby.</span><span class="sxs-lookup"><span data-stu-id="774b4-108">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to manually author binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="774b4-109">Zakázat automatické přesměrování vazby v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="774b4-109">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="774b4-110">Automatické přesměrování vazby jsou ve výchozím nastavení povolena pro aplikace pro stolní počítače se systémem Windows, které cílí na .NET Framework 4.5.1 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="774b4-110">Automatic binding redirects are enabled by default for Windows desktop apps that target the .NET Framework 4.5.1 and later versions.</span></span> <span data-ttu-id="774b4-111">Přesměrování vazby jsou přidána do výstupního konfiguračního souboru (**app.config**), když je aplikace kompilována, a přepíše sjednocení sestavení, které by jinak mohlo probíhat.</span><span class="sxs-lookup"><span data-stu-id="774b4-111">The binding redirects are added to the output configuration (**app.config**) file when the app is compiled and override the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="774b4-112">Zdrojový **app.config** soubor se nemění.</span><span class="sxs-lookup"><span data-stu-id="774b4-112">The source **app.config** file is not modified.</span></span> <span data-ttu-id="774b4-113">Tuto funkci můžete zakázat úpravou souboru projektu pro aplikaci nebo tím, že zrušíte zaškrtnutí políčka ve vlastnostech projektu v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="774b4-113">You can disable this feature by modifying the project file for the app or by deselecting a checkbox in the project's properties in Visual Studio.</span></span>

### <a name="disable-through-project-properties"></a><span data-ttu-id="774b4-114">Zakázat prostřednictvím vlastností projektu</span><span class="sxs-lookup"><span data-stu-id="774b4-114">Disable through project properties</span></span>

<span data-ttu-id="774b4-115">Pokud máte Visual Studio 2017 verze 15,7 nebo novější, můžete snadno zakázat automaticky generované přesměrování vazby na stránkách vlastností projektu.</span><span class="sxs-lookup"><span data-stu-id="774b4-115">If you have Visual Studio 2017 version 15.7 or later, you can easily disable autogenerated binding redirects in the project's property pages.</span></span>

1. <span data-ttu-id="774b4-116">Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="774b4-116">Right-click the project in **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="774b4-117">Na stránce **aplikace** zrušte možnost **automatického generování přesměrování vazby** .</span><span class="sxs-lookup"><span data-stu-id="774b4-117">On the **Application** page, uncheck the **Auto-generate binding redirects** option.</span></span>

3. <span data-ttu-id="774b4-118">Změny uložíte stisknutím **kombinace kláves CTRL +** + **S** .</span><span class="sxs-lookup"><span data-stu-id="774b4-118">Press **Ctrl**+**S** to save the change.</span></span>

### <a name="disable-manually-in-the-project-file"></a><span data-ttu-id="774b4-119">Zakázat ručně v souboru projektu</span><span class="sxs-lookup"><span data-stu-id="774b4-119">Disable manually in the project file</span></span>

1. <span data-ttu-id="774b4-120">Otevřete soubor projektu pro úpravy pomocí jedné z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="774b4-120">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="774b4-121">V aplikaci Visual Studio vyberte projekt v **Průzkumník řešení**a pak v místní nabídce zvolte možnost **Otevřít složku v Průzkumníku souborů** .</span><span class="sxs-lookup"><span data-stu-id="774b4-121">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="774b4-122">V Průzkumníku souborů vyhledejte soubor projektu (. csproj nebo. vbproj) a otevřete jej v programu Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="774b4-122">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="774b4-123">V aplikaci Visual Studio v **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Uvolnit projekt**.</span><span class="sxs-lookup"><span data-stu-id="774b4-123">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="774b4-124">Znovu klikněte pravým tlačítkem na znovu načtený projekt a pak zvolte **Upravit [ProjectName. csproj]**.</span><span class="sxs-lookup"><span data-stu-id="774b4-124">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="774b4-125">V souboru projektu vyhledejte položku následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="774b4-125">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="774b4-126">Změnit `true` na `false` :</span><span class="sxs-lookup"><span data-stu-id="774b4-126">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="774b4-127">Povolit automatické přesměrování vazby ručně</span><span class="sxs-lookup"><span data-stu-id="774b4-127">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="774b4-128">Můžete povolit automatické přesměrování vazby v existujících aplikacích, které jsou cíleny na starší verze .NET Framework, nebo v případech, kdy nejste automaticky vyzváni k přidání přesměrování.</span><span class="sxs-lookup"><span data-stu-id="774b4-128">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="774b4-129">Pokud cílíte na novější verzi rozhraní, ale nebudete automaticky vyzváni k přidání přesměrování, pravděpodobně získáte výstup sestavení, který navrhuje přemapování sestavení.</span><span class="sxs-lookup"><span data-stu-id="774b4-129">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="774b4-130">Otevřete soubor projektu pro úpravy pomocí jedné z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="774b4-130">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="774b4-131">V aplikaci Visual Studio vyberte projekt v **Průzkumník řešení**a pak v místní nabídce zvolte možnost **Otevřít složku v Průzkumníku souborů** .</span><span class="sxs-lookup"><span data-stu-id="774b4-131">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="774b4-132">V Průzkumníku souborů vyhledejte soubor projektu (. csproj nebo. vbproj) a otevřete jej v programu Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="774b4-132">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="774b4-133">V aplikaci Visual Studio v **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Uvolnit projekt**.</span><span class="sxs-lookup"><span data-stu-id="774b4-133">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="774b4-134">Znovu klikněte pravým tlačítkem na znovu načtený projekt a pak zvolte **Upravit [ProjectName. csproj]**.</span><span class="sxs-lookup"><span data-stu-id="774b4-134">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="774b4-135">Přidejte následující element do první skupiny vlastností konfigurace (pod \<PropertyGroup> značkou):</span><span class="sxs-lookup"><span data-stu-id="774b4-135">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="774b4-136">Následující příklad ukazuje soubor projektu s vloženým prvkem:</span><span class="sxs-lookup"><span data-stu-id="774b4-136">The following shows an example project file with the element inserted:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
     <PropertyGroup>
       <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
       <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
       <ProjectGuid>{123334}</ProjectGuid>
       ...
       <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
     </PropertyGroup>
     ...
   </Project>
   ```

3. <span data-ttu-id="774b4-137">Zkompilujte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="774b4-137">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="774b4-138">Povolit automatické přesměrování vazby ve webových aplikacích</span><span class="sxs-lookup"><span data-stu-id="774b4-138">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="774b4-139">Automatické přesměrování vazby je pro webové aplikace implementováno jinak.</span><span class="sxs-lookup"><span data-stu-id="774b4-139">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="774b4-140">Vzhledem k tomu, že je třeba upravit zdrojový soubor konfigurace (**web.config**) pro webové aplikace, přesměrování vazeb nejsou automaticky přidána do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="774b4-140">Because the source configuration (**web.config**) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="774b4-141">Sada Visual Studio vás však upozorní na konflikty ve vazbách a můžete tak pomocí přesměrování vazby tyto konflikty vyřešit.</span><span class="sxs-lookup"><span data-stu-id="774b4-141">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="774b4-142">Vzhledem k tomu, že se vždycky zobrazuje výzva k přidání přesměrování vazby, není nutné explicitně zakázat tuto funkci pro webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="774b4-142">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="774b4-143">Přidání přesměrování vazby na soubor **web.config** :</span><span class="sxs-lookup"><span data-stu-id="774b4-143">To add binding redirects to a **web.config** file:</span></span>

1. <span data-ttu-id="774b4-144">V sadě Visual Studio zkompilujte aplikaci a zkontrolujte upozornění na sestavení.</span><span class="sxs-lookup"><span data-stu-id="774b4-144">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="774b4-145">![Upozornění sestavení pro konflikty odkazů na sestavení](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="774b4-145">![Build warning for assembly reference conflicts](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="774b4-146">Pokud existují konflikty vazeb sestavení, zobrazí se upozornění.</span><span class="sxs-lookup"><span data-stu-id="774b4-146">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="774b4-147">Dvakrát klikněte na upozornění nebo vyberte upozornění a stiskněte klávesu **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="774b4-147">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="774b4-148">Zobrazí se dialogové okno, které umožňuje automaticky přidat potřebné přesměrování vazby do zdrojového **web.config** souboru.</span><span class="sxs-lookup"><span data-stu-id="774b4-148">A dialog box that enables you to automatically add the necessary binding redirects to the source **web.config** file appears.</span></span>

   <span data-ttu-id="774b4-149">![Dialogové okno oprávnění přesměrování vazby](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="774b4-149">![Binding redirect permission dialog](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="774b4-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="774b4-150">See also</span></span>

- [<span data-ttu-id="774b4-151">\<bindingRedirect>Objekt</span><span class="sxs-lookup"><span data-stu-id="774b4-151">\<bindingRedirect> Element</span></span>](./file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="774b4-152">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="774b4-152">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
