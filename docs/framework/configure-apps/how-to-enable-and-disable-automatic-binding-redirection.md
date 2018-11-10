---
title: Povolení nebo zakázání přesměrování vazby automaticky generované
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 284c2a08f2b78d2c6a1ab9752a3f2283e87fd734
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "50980830"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Postupy: Povolení a zákaz automatického přesměrování vazby

Při sestavování aplikací v sadě Visual Studio, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a novější verze, přesměrování vazby může automaticky přidá do konfiguračního souboru aplikace pro přepsání sjednocení sestavení. Přesměrování vazby je přidáno, pokud vaše aplikace nebo její komponenty odkazují na více verzí stejného sestavení, i když ručně zadáte přesměrování vazby v konfiguračním souboru pro vaši aplikaci. Funkce automatického přesměrování vazby ovlivňuje aplikace klasické pracovní plochy a webové aplikace, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] nebo novější verze, ačkoli chování se mírně liší pro webovou aplikaci. Pokud máte existující aplikace, které předchozí verze cílového rozhraní .NET Framework, nebo tuto funkci můžete zakázat, pokud chcete ručně vytvořit přesměrování vazby, můžete povolit automatické přesměrování vazby.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Zakázat automatické přesměrování vazby v aplikacích klasické pracovní plochy

Automatické přesměrování vazeb je povoleno standardně pro aplikace klasické pracovní plochy Windows, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a novějších verzích. Přesměrování vazby jsou přidána do konfigurace výstup (**app.config**) soubor při kompilaci aplikace a přepsání sjednocení sestavení, které jinak může probíhat. Zdroj **app.config** soubor nezměnil. Tuto funkci můžete zakázat úpravou souboru projektu pro aplikaci nebo zrušením výběru zaškrtávací políčko ve vlastnostech projektu v sadě Visual Studio.

### <a name="disable-through-project-properties"></a>Zakázat prostřednictvím vlastnosti projektu

Pokud máte Visual Studio 2017 verze 15.7 nebo novější, můžete snadno zakázat automaticky generované přesměrování vazby na stránkách vlastností projektu.

1. Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **vlastnosti**.

2. Na **aplikace** stránce, zrušte zaškrtnutí políčka **automaticky generovat přesměrování vazeb** možnost.

3. Stisknutím klávesy **Ctrl**+**S** uložte změnu.

### <a name="disable-manually-in-the-project-file"></a>Zakázat ručně v souboru projektu

1. Otevřete soubor projektu s možností úprav pomocí jedné z následujících metod:

   - V sadě Visual Studio vyberte projekt v **Průzkumníka řešení**a klikněte na tlačítko **otevřít složku v Průzkumníku souborů** z místní nabídky. V Průzkumníku souborů vyhledejte soubor projektu (.csproj nebo .vbproj) a otevřete v poznámkovém bloku.
   - V sadě Visual Studio v **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a zvolte **uvolnit projekt**. Znovu klikněte pravým tlačítkem na projekt uvolněn a klikněte na tlačítko **upravit [projectname.csproj]**.

2. V souboru projektu vyhledejte položku následující vlastnosti:

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. Změna `true` k `false`:

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>Ručně povolte automatické přesměrování vazby

Můžete povolit automatické přesměrování vazby v existujících aplikacích, které starší verze cílového rozhraní .NET Framework, nebo v případech, kde se zobrazí výzva k automaticky přidat přesměrování. Pokud cílíte novější verzi rozhraní framework, ale se mi výzva automaticky přidat přesměrování, zobrazí se pravděpodobně výstup sestavení, který naznačuje, že přemapování sestavení.

1. Otevřete soubor projektu s možností úprav pomocí jedné z následujících metod:

   - V sadě Visual Studio vyberte projekt v **Průzkumníka řešení**a klikněte na tlačítko **otevřít složku v Průzkumníku souborů** z místní nabídky. V Průzkumníku souborů vyhledejte soubor projektu (.csproj nebo .vbproj) a otevřete v poznámkovém bloku.
   - V sadě Visual Studio v **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a zvolte **uvolnit projekt**. Znovu klikněte pravým tlačítkem na projekt uvolněn a klikněte na tlačítko **upravit [projectname.csproj]**.

2. Přidejte následující element do první skupiny vlastností konfigurace (pod \<PropertyGroup > značky):

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   Následuje příklad souboru projektu v prvku vložen:

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

3. Zkompilujte aplikaci.

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Povolit automatické přesměrování vazby ve službě web apps

Automatické přesměrování vazby je pro webové aplikace implementováno jinak. Protože konfigurace zdroje (**web.config**) pro webové aplikace musí být změněn soubor, přesměrování vazeb nejsou automaticky přidáni do konfiguračního souboru. Sada Visual Studio vás však upozorní na konflikty ve vazbách a můžete tak pomocí přesměrování vazby tyto konflikty vyřešit. Protože vždy zobrazí výzva k přidání přesměrování vazby, není nutné explicitně zakázat tuto funkci pro webovou aplikaci.

Chcete-li přidat přesměrování vazby na **web.config** souboru:

1. V sadě Visual Studio zkompilujte aplikaci a zkontrolujte upozornění na sestavení.

   ![Vytváření upozornění pro sestavení odkazu konflikty](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. Pokud existují konflikty vazeb sestavení, zobrazí se upozornění. Dvakrát klikněte na upozornění, nebo vyberte upozornění a stiskněte klávesu **Enter**.

   Dialogové okno, které umožňuje automaticky přidat nezbytná vazbu přesměruje do zdroje **web.config** soubor se zobrazí.

   ![Dialogové okno oprávnění přesměrování vazby](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Viz také:

- [\<bindingRedirect > – Element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Přesměrování verzí sestavení](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
