---
title: Povolit nebo zakázat přesměrování automaticky generovaných vazeb
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: 178d5070dd7018bbc0fce474cdd0b31ba3d17f77
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "69913037"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Postupy: Povolení a zákaz automatického přesměrování vazby

Při kompilaci aplikací v aplikaci Visual Studio cílících na .NET Framework 4.5.1 a novějších verzích může být přesměrování vazby automaticky přidáno do konfiguračního souboru aplikace, aby bylo možné přepsat sjednocení sestavení. Přesměrování vazby je přidáno, pokud vaše aplikace nebo její komponenty odkazují na více verzí stejného sestavení, i když ručně zadáte přesměrování vazby v konfiguračním souboru pro vaši aplikaci. Funkce automatického přesměrování vazby má vliv na desktopové aplikace a webové aplikace, které cílí na .NET Framework 4.5.1 nebo novější verzi, i když se chování u webové aplikace mírně liší. Pokud máte existující aplikace, které cílí na předchozí verze .NET Framework, můžete povolit automatické přesměrování vazby nebo tuto funkci můžete zakázat, pokud chcete ručně vytvořit přesměrování vazby.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Zakázat automatické přesměrování vazby v aplikacích klasické pracovní plochy

Automatické přesměrování vazby jsou ve výchozím nastavení povolena pro aplikace pro stolní počítače se systémem Windows, které cílí na .NET Framework 4.5.1 a novějších verzích. Přesměrování vazby jsou přidána do výstupu konfiguračního souboru (**App. config**) při kompilování aplikace a přepíší sjednocení sestavení, které by jinak mohlo probíhat. Zdrojový soubor **App. config** není změněn. Tuto funkci můžete zakázat úpravou souboru projektu pro aplikaci nebo tím, že zrušíte zaškrtnutí políčka ve vlastnostech projektu v aplikaci Visual Studio.

### <a name="disable-through-project-properties"></a>Zakázat prostřednictvím vlastností projektu

Pokud máte Visual Studio 2017 verze 15,7 nebo novější, můžete snadno zakázat automaticky generované přesměrování vazby na stránkách vlastností projektu.

1. Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **vlastnosti**.

2. Na stránce **aplikace** zrušte možnost **automatického generování přesměrování vazby** .

3. Změny uložíte stisknutím **kombinace kláves CTRL +** + **S** .

### <a name="disable-manually-in-the-project-file"></a>Zakázat ručně v souboru projektu

1. Otevřete soubor projektu pro úpravy pomocí jedné z následujících metod:

   - V aplikaci Visual Studio vyberte projekt v **Průzkumník řešení**a pak v místní nabídce zvolte možnost **Otevřít složku v Průzkumníku souborů** . V Průzkumníku souborů vyhledejte soubor projektu (. csproj nebo. vbproj) a otevřete jej v programu Poznámkový blok.
   - V aplikaci Visual Studio v **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Uvolnit projekt**. Znovu klikněte pravým tlačítkem na znovu načtený projekt a pak zvolte **Upravit [ProjectName. csproj]**.

2. V souboru projektu vyhledejte položku následující vlastnosti:

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. Změnit `true` na `false` :

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>Povolit automatické přesměrování vazby ručně

Můžete povolit automatické přesměrování vazby v existujících aplikacích, které jsou cíleny na starší verze .NET Framework, nebo v případech, kdy nejste automaticky vyzváni k přidání přesměrování. Pokud cílíte na novější verzi rozhraní, ale nebudete automaticky vyzváni k přidání přesměrování, pravděpodobně získáte výstup sestavení, který navrhuje přemapování sestavení.

1. Otevřete soubor projektu pro úpravy pomocí jedné z následujících metod:

   - V aplikaci Visual Studio vyberte projekt v **Průzkumník řešení**a pak v místní nabídce zvolte možnost **Otevřít složku v Průzkumníku souborů** . V Průzkumníku souborů vyhledejte soubor projektu (. csproj nebo. vbproj) a otevřete jej v programu Poznámkový blok.
   - V aplikaci Visual Studio v **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Uvolnit projekt**. Znovu klikněte pravým tlačítkem na znovu načtený projekt a pak zvolte **Upravit [ProjectName. csproj]**.

2. Přidejte následující element do první skupiny vlastností konfigurace (pod \<PropertyGroup> značkou):

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   Následující příklad ukazuje soubor projektu s vloženým prvkem:

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

3. Zkompilujte aplikaci.

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Povolit automatické přesměrování vazby ve webových aplikacích

Automatické přesměrování vazby je pro webové aplikace implementováno jinak. Vzhledem k tomu, že je nutné upravit zdrojový soubor konfigurace (**Web. config**) pro webové aplikace, přesměrování vazeb nejsou automaticky přidána do konfiguračního souboru. Sada Visual Studio vás však upozorní na konflikty ve vazbách a můžete tak pomocí přesměrování vazby tyto konflikty vyřešit. Vzhledem k tomu, že se vždycky zobrazuje výzva k přidání přesměrování vazby, není nutné explicitně zakázat tuto funkci pro webovou aplikaci.

Přidání přesměrování vazby do souboru **Web. config** :

1. V sadě Visual Studio zkompilujte aplikaci a zkontrolujte upozornění na sestavení.

   ![Upozornění sestavení pro konflikty odkazů na sestavení](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. Pokud existují konflikty vazeb sestavení, zobrazí se upozornění. Dvakrát klikněte na upozornění nebo vyberte upozornění a stiskněte klávesu **ENTER**.

   Zobrazí se dialogové okno, které umožňuje automaticky přidat nezbytná přesměrování vazby na zdrojový soubor **Web. config** .

   ![Dialogové okno oprávnění přesměrování vazby](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Viz také

- [\<bindingRedirect>Objekt](./file-schema/runtime/bindingredirect-element.md)
- [Přesměrování verzí sestavení](redirect-assembly-versions.md)
