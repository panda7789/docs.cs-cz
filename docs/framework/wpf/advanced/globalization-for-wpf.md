---
title: Globalizace pro WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 4fc8c8e4d8c4cc2a53ed7e21ced9ab9c761e9d2b
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331538"
---
# <a name="globalization-for-wpf"></a>Globalizace pro WPF
V tomto tématu se seznámíte s problémy, které byste měli [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] znát při psaní aplikací pro globální trh. Programovací prvky globalizace jsou definovány v [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] v `System.Globalization`.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalizace XAML
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]je založená na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] a využívá podporu globalizace definovanou [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ve specifikaci. Následující části popisují některé [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] funkce, o kterých byste měli vědět.

<a name="char_reference"></a>
### <a name="character-references"></a>Odkazy na znaky
Odkaz na znak poskytuje UTF16 kódové jednotky konkrétního [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] znaku, který představuje, v desítkové nebo šestnáctkové soustavě. Následující příklad ukazuje desítkový znakový odkaz pro KOPTSKÉ velké písmeno "Ϩ":

```
&#1000;
```

Následující příklad ukazuje odkaz hexadecimálního znaku. Všimněte si, že má **x** před hexadecimálním číslem.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Kódování
 Kódování podporované nástrojem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je ASCII, [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 a UTF-8. Příkaz Encoding je na začátku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dokumentu. Pokud neexistuje žádný atribut kódování a neexistuje žádné pořadí bajtů, analyzátor se nastaví jako výchozí kódování UTF-8. Pro kódování jsou upřednostňovány znakové sady UTF-8 a UTF-16. Kódování UTF-7 není podporováno. Následující příklad ukazuje, jak zadat kódování UTF-8 v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru.

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Atribut Language
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]používá [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) pro reprezentaci atributu jazyka elementu.  Chcete-li využít výhod <xref:System.Globalization.CultureInfo> třídy, hodnota atributu Language musí být jeden z názvů jazykové verze <xref:System.Globalization.CultureInfo>předdefinované. [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) je dědičná ve stromové struktuře elementů (podle pravidel XML, ne nutně z důvodu dědičnosti vlastností závislosti) a její výchozí hodnota je prázdný řetězec, pokud není explicitně přiřazen.

 Atribut Language je velmi užitečný pro určení dialektů. Francouzština má například jinou kontrolu pravopisu, slovníku a výslovnost ve Francii, v Quebec, Belgii a Švýcarsku. Také čínština, japonština a korejština sdílí body kódu [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]v, ale grafické tvary se liší a používají zcela jiná písma.

 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad`fr-CA` používá atribut Language pro určení kanadské francouzštiny.

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Kódování Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]podporuje všechny [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] funkce včetně zástupných znaků. Pokud se dá znaková sada mapovat na [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], je podporovaná. Například GB18030 zavádí některé znaky namapované na rozšíření čínština, japonština a korejština (CFK) a a B a náhradní páry, proto je plně podporovaná. Aplikace může používat <xref:System.Globalization.StringInfo> k manipulaci s řetězci bez porozumění, zda mají náhradní páry nebo kombinování znaků. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Návrh mezinárodního uživatelského rozhraní pomocí jazyka XAML
 Tato část popisuje [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] funkce, které byste měli vzít v úvahu při psaní aplikace.

<a name="intl_text"></a>
### <a name="international-text"></a>Mezinárodní text
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zahrnuje integrované zpracování pro všechny .NET Framework podporované systémy pro psaní.

 V současné době jsou podporovány následující skripty:

- Arabština

- bengálština

- Koncový

- B

- Řečtina

- Gudžarátština

- Gurmukhi

- Hebrejština

- Grafické skripty

- Kannadština

- Lao

- Znak

- Malajálamština

- Mongolština

- Odia

- Slabika

- Tamilština

- Telugština

- Thána

- Thajštin

- Písmeno

 \* V této verzi se podporuje zobrazení a úpravy thajského textu. zalamování slov není.

 Následující skripty se momentálně nepodporují:

- Khmerština

- Korejština – staré hangul

- Le

- Sinhala

 Všechny systémové moduly pro psaní podporují [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]písma můžou zahrnovat [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tabulky rozložení, které umožňují tvůrcům písem navrhovat lepší mezinárodní a špičková typografická písma. Tabulky [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] rozložení písma obsahují informace o substitucích glyfů, umístění glyfů, zdůvodnění a umístění standardních hodnot a umožňují aplikacím pro zpracování textu zlepšit rozložení textu.

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]písma umožňují zpracování velkých sad glyfů pomocí [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] kódování. Takové kódování umožňuje širokou škálu mezinárodní podpory i pro typografické varianty glyfů.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vykreslování textu je poháněno [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] pomocí technologie s podobrazovou čárkou, která podporuje nezávislost rozlišení. To významně zlepšuje čitelnost a poskytuje možnost podporovat dokumenty ve stylu časopisu High Quality pro všechny skripty.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Mezinárodní rozložení
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje velmi pohodlný způsob, jak podporovat vodorovná, obousměrná a vertikální rozložení. V prezentačním prostředí <xref:System.Windows.FrameworkElement.FlowDirection%2A> lze vlastnost použít k definování rozložení. Vzorce směru toku jsou:

- *LeftToRight* – horizontální rozložení pro latinkou, východní Asie a tak dále.

- *RightToLeft* – obousměrný pro arabštinu, hebrejštinu a tak dále.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Vývoj lokalizovatelných aplikací
 Při psaní aplikace pro globální spotřebu byste měli mít na paměti, že aplikace musí být lokalizovatelné. Následující témata ukazují, co je potřeba vzít v úvahu.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Vícejazyčné uživatelské rozhraní
 Vícejazyčná uživatelská rozhraní (MUI) je [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] podpora pro přepínání [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] z jednoho jazyka na jiný. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aplikace používá model sestavení pro podporu MUI. Jedna aplikace obsahuje jazykově neutrální sestavení i jazyková sestavení satelitních prostředků závislá na jazyce. Vstupním bodem je spravovaný. EXE v hlavním sestavení.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zavaděč prostředků využívá [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]správce prostředků k podpoře vyhledávání a záložních prostředků. Více jazykových satelitních sestavení funguje se stejným hlavním sestavením. Načtené sestavení prostředků závisí na <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> aktuálním vlákně.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Lokalizovatelné uživatelské rozhraní
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikace používají [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] k definování jejich [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]umožňuje vývojářům určit hierarchii objektů se sadou vlastností a logiky. Primárním použitím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nástroje je vývoj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, ale lze jej použít k určení hierarchie všech [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objektů. Většina vývojářů [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používá k určení jejich [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikace a používání programovacího jazyka, jako C# je například reakce na interakci s uživatelem.

 Z pohledu prostředku je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor navržený tak, aby popisoval závislé [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] na jazyku, který je prvkem prostředku, a proto je nutné lokalizovat jeho konečný formát distribuce, aby podporoval mezinárodní jazyky. Protože [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemůže zpracovat události, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mnoho aplikací obsahuje bloky kódu k tomu. Další informace naleznete v tématu [Přehled XAML (WPF)](xaml-overview-wpf.md). Kód je odstraněn a zkompilován do různých binárních souborů v případě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , že je soubor přidaný do formuláře BAML typu XAML. Formulář BAML souborů XAML, obrázků a dalších typů spravovaných objektů prostředků jsou vloženy do satelitního sestavení prostředků, které lze lokalizovat do jiných jazyků, nebo do hlavního sestavení, pokud není nutná lokalizace.

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikace podporují všechny [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] prostředky, včetně tabulek řetězců, obrázků a tak dále.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Vytváření lokalizovatelných aplikací
 Lokalizace znamená pro přizpůsobení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] k různým kulturám. Aby bylo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] možné aplikaci lokalizovat, vývojáři potřebují sestavit všechny lokalizovatelné prostředky do sestavení prostředků. Sestavení prostředků je lokalizováno do různých jazyků a kód na pozadí používá rozhraní API pro správu prostředků k načtení. Jeden ze souborů vyžadovaných pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci je soubor projektu (. proj). Všechny prostředky, které ve vaší aplikaci používáte, by měly být zahrnuté do souboru projektu. Následující příklad ze souboru. csproj ukazuje, jak to provést.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Chcete-li použít prostředek ve vaší aplikaci <xref:System.Resources.ResourceManager> , vytvořte instanci a a načtěte prostředek, který chcete použít. Následující příklad demonstruje, jak to udělat.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Použití ClickOnce s lokalizovanými aplikacemi
 ClickOnce je nová technologie nasazení model Windows Forms, která bude dodávána se sadou Visual Studio 2005. Umožňuje instalaci aplikace a upgrade webových aplikací. Je-li aplikace nasazená s ClickOnce lokalizována, lze ji zobrazit pouze v lokalizované jazykové verzi. Například pokud je nasazená aplikace lokalizována do japonštiny, lze ji zobrazit pouze v [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] anglické verzi systému Windows. To představuje problém, protože se jedná o běžný scénář pro použití anglické verze systému Windows pro japonské uživatele.

 Řešením tohoto problému je nastavení atributu pro záložní použití neutrálního jazyka. Vývojář aplikace může volitelně odebrat prostředky z hlavního sestavení a určit, že prostředky lze nalézt v satelitním sestavení odpovídajícím konkrétní jazykové verzi. Chcete-li řídit tento proces <xref:System.Resources.NeutralResourcesLanguageAttribute>, použijte. Konstruktor <xref:System.Resources.NeutralResourcesLanguageAttribute> třídy má dva signatury, jeden, který <xref:System.Resources.UltimateResourceFallbackLocation> přebírá parametr pro <xref:System.Resources.ResourceManager> určení umístění, kde by měl extrahovat záložní prostředky: hlavní sestavení nebo satelitní sestavení. Následující příklad ukazuje, jak použít atribut. V případě konečného záložního umístění kód způsobí <xref:System.Resources.ResourceManager> hledání prostředků v podadresáři "de" adresáře aktuálně spuštěného sestavení.

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Viz také:

- [Přehled globalizace a lokalizace WPF](wpf-globalization-and-localization-overview.md)
