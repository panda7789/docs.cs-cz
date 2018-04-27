---
title: Globalizace pro WPF
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-wpf
ms.topic: article
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
caps.latest.revision: 35
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8bf63c59c0948dd8414232a52fc12fafa0d13aa1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="globalization-for-wpf"></a>Globalizace pro WPF
Toto téma představuje problémy, které byste měli vědět, když zápis [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací na globálním trhu. Globalizace programovací elementy jsou definovány v [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] v `System.Globalization`.  
  

  
<a name="xaml_globalization"></a>   
## <a name="xaml-globalization"></a>Globalizace XAML  
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] je založena na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] a využívá podpory globalizace definovaný v [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] specifikace. Následující části popisují některé [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] funkce, které byste měli vědět.  
  
<a name="char_reference"></a>   
### <a name="character-references"></a>Odkazy na znak  
Odkaz na znak dává UTF16 jednotka kódu konkrétní [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] znak ho představuje desetinné nebo šestnáctkové číslo. Následující příklad ukazuje odkaz decimal znak v KOPTŠTINA velké písmeno, nebo 'Ϩ':

```
&#1000;
```

Následující příklad ukazuje odkaz hexadecimálních znaků. Všimněte si, že má **x** před hexadecimální číslo.

```
&#x3E8;
```

<a name="encoding"></a>   
### <a name="encoding"></a>Kódování  
 Kódování nepodporuje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 a UTF-8. Příkaz kódování je na začátku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dokumentu. Pokud neexistuje žádný atribut kódování a není k dispozici žádné pořadí bajtů, analyzátor výchozí znakové sady UTF-8. Jsou upřednostňované kódování UTF-8 a UTF-16. Znakové sady UTF-7 není podporována. Následující příklad ukazuje, jak určit kódování UTF-8 v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru.  
  
```  
?xml encoding="UTF-8"?  
```  
  
<a name="lang_attrib"></a>   
### <a name="language-attribute"></a>Atribut jazyka  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používá [XML: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) představující atribut language elementu.  Chcete využít výhod <xref:System.Globalization.CultureInfo> třída, hodnotu atributu jazyka musí být jeden ze zadaných názvů jazykovou verzi, předdefinované podle <xref:System.Globalization.CultureInfo>. [XML: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) je zděditelné ve stromové struktuře – element (podle pravidla XML, nikoli nutně z důvodu závislosti dědičnost vlastnosti) a jeho výchozí hodnota je řetězec prázdný, pokud není explicitně přiřazeny.  
  
 Je velmi užitečná pro zadání dialekty atribut language. Například Francouzština má pravopisu, termínů a výslovnosti Francie, Quebec, Belgie, a Švýcarska. Také čínština, japonština nebo korejština sdílení bodů kódu v [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], ale ideografických tvarů se liší a uvidíte úplně jiné písem používají.  
  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad používá `fr-CA` atributu jazyk k určení francouzština (Kanada).  
  
```xml  
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>  
```  
  
<a name="unicode"></a>   
### <a name="unicode"></a>Kódování Unicode  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] podporuje všechny [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] funkce včetně náhrady. Tak dlouho, dokud znaková sada lze mapovat na [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], je podporována. Například GB18030 zavádí některé znaky, které jsou mapované na rozšíření čínština, japonština nebo korejština (CFK) A a B a náhradního páry, proto je plně podporovaný. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace můžete použít <xref:System.Globalization.StringInfo> k manipulaci s řetězci bez pochopení, zda mají náhradní dvojice nebo kombinace znaků.  
  
<a name="design_intl_ui_with_xaml"></a>   
## <a name="designing-an-international-user-interface-with-xaml"></a>Navrhování mezinárodní uživatelské rozhraní s XAML  
 Tato část popisuje [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] funkce, které byste měli zvážit při zápisu aplikace.  
  
<a name="intl_text"></a>   
### <a name="international-text"></a>Mezinárodní textu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahrnuje integrovanou zpracování pro zápis všech rozhraní Microsoft .NET Framework, které jsou podporovány systémy.  
  
 Tyto skripty jsou aktuálně podporovány:  
  
-   Arabština  
  
-   Bengálština  
  
-   Devanagari  
  
-   Cyrilici  
  
-   Řečtina  
  
-   Gudžarátština  
  
-   Gurmukhi  
  
-   Hebrejština  
  
-   Ideografických skripty  
  
-   Kannada  
  
-   Laoská  
  
-   Latinská  
  
-   Malajalámština  
  
-   Mongolština  
  
-   Udijština  
  
-   Syrské  
  
-   Tamilština  
  
-   Telugština  
  
-   Thána  
  
-   Thajštině *  
  
-   Tibetské  
  
 * V tomto vydání zobrazení a úpravy Thajská textu je podporovaná; dělení slov není.  
  
 Tyto skripty nejsou aktuálně podporovány:  
  
-   Khmerský  
  
-   Korejské staré písmo  
  
-   Barmské  
  
-   Sinhálské  
  
 Všechny používané písmo motorů podporu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písem. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] může zahrnovat písem [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] rozložení tabulky, které povolit písma tvůrcům návrh lépe mezinárodní a vyšší kategorie typografických písem. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Písma rozložení tabulky obsahují informace o nahrazení glyf, umístění glyfů, zarovnání do bloku a standardních hodnot umístění, povolení zpracování textu aplikací ke zlepšení rozložení textu.  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Povolit písem zpracování velkých glyfu nastaví pomocí [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] kódování. Takové kódování umožňuje široký Mezinárodní podpora také jako variant typografických glyfů.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá technologii vykreslování textu [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] dílčí pixelů technologie, která podporuje nezávislost řešení. To výrazně zlepšuje čitelnost a nabízí možnost podpory vysoké kvality katalogu styl dokumenty pro všechny skripty.  
  
<a name="intl_layout"></a>   
### <a name="international-layout"></a>Mezinárodní rozložení  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje velmi pohodlný způsob pro podporu vodorovné, obousměrné a svislém rozložení. V rámci prezentace <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost lze použít k definování rozložení. Vzory směr toku jsou:  
  
-   *LeftToRight* -vodorovném rozložení pro Latin, východoasijské a tak dále.  
  
-   *RightToLeft* -obousměrného arabština, hebrejština a tak dále.  
  
<a name="developing_localizable_apps"></a>   
## <a name="developing-localizable-applications"></a>Vývoj možnosti lokalizace aplikací  
 Při psaní aplikace pro globální spotřeba byste měli mít na paměti, že aplikace musí být lokalizovatelný. V následujících tématech upozorníme na co je třeba zvážit.  
  
<a name="mui"></a>   
### <a name="multilingual-user-interface"></a>Vícejazyčné uživatelské rozhraní  
 Vícejazyčné uživatelské rozhraní sady MUI (Multilingual) je [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] podporu pro přepínání [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] z jednoho jazyka do druhého. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace používá model sestavení pro podporu MUI. Jedna aplikace obsahuje jazykově neutrální sestavení, jakož i závislých na jazyku satelitní sestavení prostředků. Vstupní bod je spravované. EXE v hlavní sestavení.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zavaděč prostředku využívá [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]pro správce prostředků pro podporu vyhledávání prostředků a nouzového řešení ověření. Více satelitní sestavení pracovat se stejnou hlavní sestavení. Sestavení prostředků, které je načtena, závisí na <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> aktuálního vlákna.  
  
<a name="localizable_ui"></a>   
### <a name="localizable-user-interface"></a>Možnosti lokalizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace používat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] definovat jejich [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] umožňuje vývojářům zadat hierarchii objektů sadu vlastností a logiku. Primárním použitím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je vyvinout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, ale slouží k určení hierarchie libovolného [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty. Většina vývojářů používají [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a zadat jejich aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a používat programovací jazyk, například C# reagování na interakci s uživatelem.  
  
 Z prostředků hlediska [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů navržený tak, aby popisují jazyk závislé [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] je element prostředků a proto jeho poslední distribuce musí být ve formátu lokalizovatelný zajistit podporu mezinárodní jazyků. Protože [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemůže zpracovat události, mnoho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikace obsahují bloky kódu k tomu. Další informace najdete v tématu [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Kód je vynechají a zkompilovat do různých binárních souborů při [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je soubor tokenizovaného do formuláře BAML XAML. BAML formu soubory XAML, Image a dalších typů objektů spravovaných prostředků jsou vloženy do satelitní sestavení pro prostředek, který je možné lokalizovat do jiných jazyků, nebo hlavní sestavení při lokalizaci se nevyžaduje.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace podporují všechny [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] prostředky, včetně tabulek řetězců, obrázků a tak dále.  
  
<a name="building_localizable_apps"></a>   
### <a name="building-localizable-applications"></a>Vytváření možnosti lokalizace aplikací  
 Lokalizace znamená přizpůsobení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro různé jazykové verze. Chcete-li [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizovatelný, vývojáři potřebujete k vytvoření lokalizovatelný prostředky do prostředku sestavení aplikace. Sestavení prostředků je lokalizované do různých jazyků a Správa prostředků používá modelu code-behind [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] načíst. Jeden z soubory potřebné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace je soubor projektu (.proj). Všechny prostředky, které používáte ve vaší aplikaci by měl být obsažen v souboru projektu. Následující příklad ze souboru .csproj ukazuje, jak to udělat.  
  
```xml  
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>  
```  
  
 Použití prostředků ve vaší aplikaci doložit <xref:System.Resources.ResourceManager> a načtení prostředků, kterou chcete použít. Následující příklad demonstruje, jak to udělat.  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]  
  
<a name="using_clickonce"></a>   
## <a name="using-clickonce-with-localized-applications"></a>Pomocí lokalizované aplikace ClickOnce  
 ClickOnce je novou technologií nasazení Windows Forms dodávané s [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]. Umožňuje instalaci aplikací a upgrade webových aplikací. Když je aplikace, která byla nasazena s ClickOnce lokalizované lze zobrazit pouze na lokalizované jazykové verzi. Například pokud je na japonštinu lokalizované nasazené aplikace ji lze zobrazit pouze na japonštinu [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] není v angličtině [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]. To představuje problém, protože je běžný scénář japonské uživatelům používají anglickou verzi [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)].  
  
 Řešení tohoto problému je nastavení záložní atribut neutrální jazyk. Vývojář aplikací můžete volitelně odebrat prostředky z hlavní sestavení a určit, že prostředky naleznete v satelitních sestavení na konkrétní jazykovou verzi. K řízení použití tento proces <xref:System.Resources.NeutralResourcesLanguageAttribute>. Konstruktoru <xref:System.Resources.NeutralResourcesLanguageAttribute> třída má dva podpisy, ten, který přebírá <xref:System.Resources.UltimateResourceFallbackLocation> parametr k určení umístění, kde <xref:System.Resources.ResourceManager> by měl extrahovat nouzové prostředky: hlavní sestavení nebo satelitní sestavení. Následující příklad ukazuje, jak pomocí atributu. Pro konečné umístění zálohy kód způsobí, že <xref:System.Resources.ResourceManager> a hledat prostředky v podadresáři "de" adresáře aktuálně prováděné sestavení.  
  
```  
[assembly: NeutralResourcesLanguageAttribute(  
    "de" , UltimateResourceFallbackLocation.Satellite)]  
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled globalizace a lokalizace WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
