---
title: "Postupy: Povolení a zákaz automatického přesměrování vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b6887706aeef3855c1e02c8b1379856022cdac04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Postupy: Povolení a zákaz automatického přesměrování vazby
Počínaje [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], při kompilaci aplikace cílených [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], přesměrování vazby mohou být automaticky přidány do konfiguračního souboru aplikace k přepsání sjednocení sestavení. Přesměrování vazby je přidáno, pokud vaše aplikace nebo její komponenty odkazují na více verzí stejného sestavení, i když ručně zadáte přesměrování vazby v konfiguračním souboru pro vaši aplikaci. Funkce přesměrování vazby automatické ovlivňuje tradiční desktopové aplikace a webové aplikace cílených [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], i když toto chování je mírně odlišný pro webovou aplikaci. Pokud máte existující aplikace, které jsou určeny pro předchozí verze rozhraní .NET Framework, můžete povolit automatické přesměrování vazby nebo tuto funkci můžete zakázat, pokud chcete zachovat ručně vytvořená přesměrování vazby.  
  
## <a name="disabling-automatic-binding-redirects-in-desktop-apps"></a>Zakázání automatické vazby přesměruje v aplikacích klasické pracovní plochy  
 Přesměrování vazby automatické jsou povolené ve výchozím nastavení tradiční aplikací klasické pracovní plochy, které cílí [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a novějších verzích. Přesměrování vazby jsou přidána do výstupního souboru konfigurace (app.config) při kompilaci aplikace a přepíšou sjednocení sestavení, které jinak může probíhat. Zdrojový soubor app.config není změněn. Tuto funkci můžete zakázat úpravou souboru projektu pro aplikaci.  
  
#### <a name="to-disable-automatic-binding-redirects"></a>Zakázání automatického přesměrování vazeb  
  
1.  V sadě Visual Studio, vyberte na projekt v **Průzkumníku řešení**a potom zvolte **otevřít složku v Průzkumníku souborů** z místní nabídky.  
  
2.  V Průzkumníku souborů vyhledejte soubor projektu (.csproj nebo .vbproj) a otevřete jej v programu Poznámkový blok.  
  
3.  V souboru projektu vyhledejte položku následující vlastnosti:  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  Změna `true` k `false`:  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## <a name="enabling-automatic-binding-redirects-manually"></a>Povolení automatického vazby přesměruje ručně  
 Můžete povolit přesměrování automatické vazby v existující aplikace tento cíl starší verze rozhraní .NET Framework, nebo v případech, kde se výzva automaticky přidat přesměrování. Pokud jsou cílení na novější verzi rozhraní framework, ale výzva automaticky přidat přesměrování, zobrazí se pravděpodobně sestavení výstupu, který naznačuje, že přemapovat sestavení.  
  
#### <a name="to-manually-add-an-automatic-binding-redirect-property"></a>Ruční přidání ve vlastnosti vazby automatické přesměrování  
  
1.  V sadě Visual Studio, vyberte na projekt v **Průzkumníku řešení**a potom zvolte **otevřít složku v Průzkumníku souborů** z místní nabídky.  
  
2.  V Průzkumníku souborů vyhledejte soubor projektu (.csproj nebo .vbproj) a otevřete jej v programu Poznámkový blok.  
  
3.  Přidejte následující element ke skupině první vlastnost konfigurace (v části \<PropertyGroup > značka):  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     Na obrázku je příklad souboru projektu s elementem vložit.  
  
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
  
4.  Zkompilujte aplikaci.  
  
## <a name="enabling-automatic-binding-redirects-in-web-apps"></a>Povolení automatického přesměrování vazby ve webových aplikacích  
 Automatické přesměrování vazby je pro webové aplikace implementováno jinak. Vzhledem k tomu, že je třeba upravit zdrojový soubor konfigurace (web.config) pro webové aplikace, přesměrování vazeb nejsou automaticky přidána do konfiguračního souboru. Sada Visual Studio vás však upozorní na konflikty ve vazbách a můžete tak pomocí přesměrování vazby tyto konflikty vyřešit. Vzhledem k tomu, že se vždy zobrazí výzva k přidání přesměrování vazby, není nutné explicitně zakázat tuto funkci pro webovou aplikaci.  
  
#### <a name="to-add-binding-redirects-to-a-webconfig-file"></a>Přidání přesměrování vazeb v souboru web.config  
  
1.  V sadě Visual Studio zkompilujte aplikaci a zkontrolujte upozornění na sestavení.  
  
     ![Sestavení upozornění konflikty odkaz na sestavení](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")  
  
2.  Pokud existují konflikty vazeb sestavení, zobrazí se upozornění. Dvakrát klikněte na upozornění. (Klávesové: Vyberte upozornění a stiskněte klávesu **Enter**.)  
  
     Zobrazí se dialogové okno, které umožňuje automaticky přidat nezbytná přesměrování vazby na zdrojový soubor web.config.  
  
     ![Dialogové okno oprávnění přesměrování vazby](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")  
  
## <a name="see-also"></a>Viz také  
 [\<bindingRedirect – > elementu](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [Přesměrování verzí sestavení](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
