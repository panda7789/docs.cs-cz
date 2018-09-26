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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47079540"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Postupy: Povolení a zákaz automatického přesměrování vazby

Při sestavování aplikací v sadě Visual Studio, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a novější verze, přesměrování vazby může automaticky přidá do konfiguračního souboru aplikace pro přepsání sjednocení sestavení. Přesměrování vazby je přidáno, pokud vaše aplikace nebo její komponenty odkazují na více verzí stejného sestavení, i když ručně zadáte přesměrování vazby v konfiguračním souboru pro vaši aplikaci. Funkce automatického přesměrování vazby ovlivňuje aplikace klasické pracovní plochy a webové aplikace, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] nebo novější verze, ačkoli chování se mírně liší pro webovou aplikaci. Pokud máte existující aplikace, které jsou určeny pro předchozí verze rozhraní .NET Framework, můžete povolit automatické přesměrování vazby nebo tuto funkci můžete zakázat, pokud chcete zachovat ručně vytvořená přesměrování vazby.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Zakázat automatické přesměrování vazby v aplikacích klasické pracovní plochy

Automatické přesměrování vazeb je povoleno standardně pro tradiční stolní aplikace, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a novějších verzích. Přesměrování vazby jsou přidána do výstupního souboru konfigurace (app.config) při kompilaci aplikace a přepíšou sjednocení sestavení, které jinak může probíhat. Zdrojový soubor app.config není změněn. Tuto funkci můžete zakázat úpravou souboru projektu pro aplikaci.

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

Automatické přesměrování vazby je pro webové aplikace implementováno jinak. Vzhledem k tomu, že je třeba upravit zdrojový soubor konfigurace (web.config) pro webové aplikace, přesměrování vazeb nejsou automaticky přidána do konfiguračního souboru. Sada Visual Studio vás však upozorní na konflikty ve vazbách a můžete tak pomocí přesměrování vazby tyto konflikty vyřešit. Protože vždy zobrazí výzva k přidání přesměrování vazby, není nutné explicitně zakázat tuto funkci pro webovou aplikaci.

Chcete-li přidat přesměrování vazby do souboru web.config:

1. V sadě Visual Studio zkompilujte aplikaci a zkontrolujte upozornění na sestavení.

   ![Vytváření upozornění pro sestavení odkazu konflikty](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. Pokud existují konflikty vazeb sestavení, zobrazí se upozornění. Dvakrát klikněte na upozornění, nebo vyberte upozornění a stiskněte klávesu **Enter**.

   Zobrazí se dialogové okno, které umožňuje automaticky přidat nezbytná přesměrování vazby na zdrojový soubor web.config.

   ![Dialogové okno oprávnění přesměrování vazby](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Viz také:

- [\<bindingRedirect > – Element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Přesměrování verzí sestavení](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
