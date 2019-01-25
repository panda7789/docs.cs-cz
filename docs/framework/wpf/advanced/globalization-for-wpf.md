---
title: Globalizace pro WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: d7b544fcb308960ff86b83655d60cb1453b6571a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543812"
---
# <a name="globalization-for-wpf"></a>Globalizace pro WPF
Toto téma popisuje problémy, které byste měli vědět při zápisu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací na globálním trhu. Globalizace programovací prvky, které jsou definovány v [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] v `System.Globalization`.



<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalizace XAML
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] je založen na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] a využívá výhod podpory globalizace definované v [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] specifikace. Následující části popisují některé [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] funkce, které byste měli vědět.

<a name="char_reference"></a>
### <a name="character-references"></a>Znak odkazy
Poskytuje odkazy na znak jednotky kódu UTF16 konkrétní [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] znak to představuje v desítkové nebo šestnáctkové. Následující příklad ukazuje odkaz desítkové kódy znaků pro HORI KOPTŠTINA velké písmeno, nebo "Ϩ":

```
&#1000;
```

Následující příklad ukazuje odkaz šestnáctkové kódy znaků. Všimněte si, že má **x** před šestnáctkové číslo.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Kódování
 Kódování nepodporuje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 a UTF-8. Kódování prohlášení je na začátku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dokumentu. Pokud neexistuje žádný atribut kódování a neexistuje žádné pořadí bajtů, analyzátor výchozí hodnota je UTF-8. UTF-8 a UTF-16 jsou upřednostňované kódování. Kódování UTF-7 se nepodporuje. Následující příklad ukazuje, jak určit kódování UTF-8 v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru.

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Atribut Language
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používá [XML: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) představující atributu language elementu.  Abyste mohli využívat <xref:System.Globalization.CultureInfo> třídy, hodnota atributu language musí být jeden z názvů jazykovou verzi předdefinovaná v nástroji <xref:System.Globalization.CultureInfo>. [XML: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) je odvoditelný v stromem prvků (podle pravidel XML, ne tedy nutně kvůli dědičnosti vlastností závislostí) a jeho výchozí hodnota je prázdný řetězec, pokud není explicitně přiřazeny.

 Atribut language je velmi užitečné pro určení dialekty. Francouzština má například pravopisu, slovník a výslovnost ve Francii, Quebec, Belgie a Švýcarska. Také čínštiny, japonštiny a korejštiny sdílet body kódu v [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], ale znakový obrazce se liší a používají něco úplně jiného písma.

 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad používá `fr-CA` atribut language k určení francouzština (Kanada).

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Kódování Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] podporuje všechny [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] funkce včetně zástupnými typy. Za předpokladu, znakové sady je možné mapovat na [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], se podporuje. Například GB18030 zavádí některé znaky, které jsou mapované na rozšíření čínština, japonština nebo korejština (CFK) A a B a náhradní páry, proto je plně podporovaná. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace můžete použít <xref:System.Globalization.StringInfo> k manipulaci s řetězci bez porozumění, zda mají náhradní páry a kombinace znaků.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Navrhování mezinárodní uživatelské rozhraní s XAML
 Tato část popisuje [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] funkce, které byste měli zvážit při psaní aplikací.

<a name="intl_text"></a>
### <a name="international-text"></a>Mezinárodní Text
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahrnuje integrované zpracování pro všechny podporované rozhraní Microsoft .NET Framework písmové systémy.

 Následující skripty jsou aktuálně podporovány:

-   Arabština

-   bengálština

-   Devanágarí

-   Cyrilice

-   Řečtina

-   Gudžarátština

-   Gurmukhi

-   Hebrejština

-   Znakový skriptů

-   Kannadština

-   Lao

-   Latinská

-   Malajálamština

-   Mongolština

-   Odia

-   Syrská

-   Tamilština

-   Telugština

-   Thaana

-   Thajština *

-   Tibetské

 * V této verzi zobrazení a úpravy thajský textu je podporovány. dělení slov není.

 Následující skripty se momentálně nepodporují:

-   Khmer

-   Korejské staré písmo

-   Myanmar

-   Sinhala

 Všechny písmo strojů podporu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] můžete zahrnout písma [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tabulky rozložení, které umožňují písma creators Navrhnout lepší mezinárodní a vyšší kategorie typografickém písma. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Písma rozložení tabulky obsahují informace o piktogram náhrady, umístění glyfů, zarovnání a standardních hodnot umístění, povolení aplikací pro zpracování textu pro zlepšení rozložení textu.

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] písma povolit zpracování velkých piktogram nastaví pomocí [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] kódování. Takové kódování umožňuje širokou mezinárodní podpora stejně jako u varianty typografickém glyfů.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování textu využívá k tomu [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] dílčí pixel technologie, která podporuje nezávislost řešení. To výrazně zlepšuje čitelnost a umožňuje vysoce kvalitní magazine styl dokumentů o podpoře pro všechny skripty.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Mezinárodní rozložení
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje velmi pohodlný způsob, jak podporovat vodorovné, obousměrné a svislé rozložení. V jednoduchá prezentační architektura <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost lze použít k definování rozložení. Tyto vzory se dají směr toku jsou:

-   *LeftToRight* – vodorovné rozložení pro latinka, východní Asie a tak dále.

-   *RightToLeft* – obousměrné arabština, hebrejština a tak dále.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Vývoj lokalizovatelných aplikacích
 Při psaní aplikace pro globální spotřeby měli mít na paměti, že aplikace musí být lokalizovatelný. V následujících tématech upozorňují na věci k uvážení.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Vícejazyčné uživatelské rozhraní
 (Multi-Language User rozhraní) je [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] podporu pro přepínání [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] z jednoho jazyka do druhého. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace používá model sestavení pro podporu MUI. Jedna aplikace obsahuje jazykově neutrální sestavení, jakož i závislá na jazyku satelitní sestavení prostředků. Vstupní bod je spravovaná. Soubor EXE v hlavním sestavení.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zavaděč prostředku využívá [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]na resource Manageru pro podporu vyhledávání prostředků a nouzového řešení ověření. Více satelitní sestavení jazyka pracovat se stejnou hlavní sestavení. Závislá sestavení prostředků, který je načten <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> aktuálního vlákna.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Lokalizovatelné uživatelského rozhraní
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace používají [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] definovat jejich [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] umožňuje vývojářům zadat sadu vlastností a logika hierarchii objektů. Primární použití [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je vývoj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, ale slouží k určení hierarchie žádné [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty. Většina vývojářů používá [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a zadat jejich aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a reagovat na interakci uživatele pomocí programovacího jazyka, jako je C#.

 Z prostředků hlediska [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru určená k popisu závislá na jazyku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] je element prostředku a proto jeho poslední distribuce musí být ve formátu lokalizovatelné pro podporu mezinárodní jazyky. Protože [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemůže zpracovávat události, mnoho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikace obsahují bloky kódu k tomu. Další informace najdete v tématu [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Kód je vynechají a zkompilovány do různých binární soubory při [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je soubor tokenizovaného do formuláře BAML z XAML. Formulář BAML souborů XAML, obrázky a další typy objektů spravovaných prostředků jsou vloženy do satelitní sestavení prostředků, které může být lokalizována do jiných jazyků, nebo hlavní sestavení při lokalizaci se nevyžaduje.

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace podporují všechny [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] prostředky, včetně tabulek řetězců, obrázků a tak dále.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Vytváření lokalizovatelných aplikacích
 Lokalizace znamená přizpůsobení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro různé jazykové verze. Chcete-li [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizovatelný vývojáři potřebují k vývoji všechny lokalizovatelné prostředky do sestavení prostředků aplikace. Sestavení prostředků je lokalizován do různých jazycích a modelu code-behind používá správu prostředků [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] načíst. Jeden ze souborů požadovaných pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace je soubor projektu (souborů .proj). Všechny prostředky, které používáte ve vaší aplikaci by měla být zahrnuty v souboru projektu. Ze souboru .csproj následující příklad ukazuje, jak to provést.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Můžete vytvořit instanci prostředků ve vaší aplikaci <xref:System.Resources.ResourceManager> a načtěte prostředek, který chcete použít. Následující příklad demonstruje, jak to udělat.

 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Pomocí lokalizovaných aplikací ClickOnce
 ClickOnce je nová technologie nasazení Windows Forms, který bude dodáváno spolu s Visual Studio 2005. Umožňuje instalaci aplikací a inovací webových aplikací. Pokud lokalizované aplikace, která byla nasazena s ClickOnce lze zobrazit pouze na lokalizovanou jazykovou verzi. Například pokud je lokalizován nasazenou aplikaci na japonštinu ji lze zobrazit pouze na Japonština [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] není v angličtině Windows. To představuje problém, protože je běžný scénář pro japonské uživatelům spouštět anglickou verzi Windows.

 Řešení tohoto problému je nastavení záložní atribut neutrální jazyk. Vývojáři aplikací můžete volitelně odebrat prostředky z hlavního sestavení a určit, že prostředky nacházely v satelitní sestavení odpovídající konkrétní jazykovou verzi. K řízení používání tohoto procesu <xref:System.Resources.NeutralResourcesLanguageAttribute>. Konstruktor třídy <xref:System.Resources.NeutralResourcesLanguageAttribute> třída má dvě podpisy, ten, který přebírá <xref:System.Resources.UltimateResourceFallbackLocation> parametr k určení umístění, kde <xref:System.Resources.ResourceManager> by měl extrahovat záložní prostředky: hlavního sestavení nebo satelitního sestavení. Následující příklad ukazuje způsob použití atributu. Pro použití náhradní lokality konečné umístění, kód způsobí, že <xref:System.Resources.ResourceManager> hledat prostředky v podadresáři "de" adresáře právě spuštěné sestavení.

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Viz také:
- [Přehled globalizace a lokalizace WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
