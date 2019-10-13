---
title: Globalizace pro WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 32caf87435e23008f9f300d231c2705e7894280f
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291459"
---
# <a name="globalization-for-wpf"></a>Globalizace pro WPF
V tomto tématu se seznámíte s problémy, které byste měli znát při psaní aplikací [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pro globální trh. Programovací prvky globalizace jsou definovány v rozhraní .NET v oboru názvů <xref:System.Globalization>.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalizace XAML
 Jazyk Extensible Application Markup Language (XAML) (XAML) je založen na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] a využívá podporu globalizace definovanou ve specifikaci [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Následující části popisují některé funkce @no__t 0, o kterých byste měli vědět.

<a name="char_reference"></a>
### <a name="character-references"></a>Odkazy na znaky
Odkaz na znak poskytuje UTF16 kódové jednotky konkrétního znaku [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)], který představuje, v desítkovém nebo šestnáctkovém formátu. Následující příklad ukazuje desítkový znakový odkaz pro KOPTSKÉ velké písmeno "Ϩ":

```
&#1000;
```

Následující příklad ukazuje odkaz hexadecimálního znaku. Všimněte si, že má **x** před hexadecimálním číslem.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Encoding
 Kódování podporované [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou ASCII, [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 a UTF-8. Příkaz Encoding se nachází na začátku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dokumentu. Pokud neexistuje žádný atribut kódování a neexistuje žádné pořadí bajtů, analyzátor se nastaví jako výchozí kódování UTF-8. Pro kódování jsou upřednostňovány znakové sady UTF-8 a UTF-16. Kódování UTF-7 není podporováno. Následující příklad ukazuje, jak zadat kódování UTF-8 v souboru [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

```xaml
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Atribut Language
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používá jazyk [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) pro reprezentaci atributu Language elementu.  Chcete-li využít výhod třídy <xref:System.Globalization.CultureInfo>, hodnota atributu Language musí být jedním z názvů jazykové verze předdefinovaných <xref:System.Globalization.CultureInfo>. [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) je dědičná ve stromové struktuře elementů (podle pravidel XML, ne nutně z důvodu dědičnosti vlastností závislosti) a její výchozí hodnota je prázdný řetězec, pokud není explicitně přiřazen.

 Atribut Language je velmi užitečný pro určení dialektů. Francouzština má například jinou kontrolu pravopisu, slovníku a výslovnost ve Francii, v Quebec, Belgii a Švýcarsku. Také čínské, japonské a korejské body kódu pro sdílení v [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], ale grafické tvary se liší a používají úplně jiná písma.

 Následující příklad [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] používá pro určení kanadské francouzštiny atribut jazyka `fr-CA`.

```xaml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Sady
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] podporuje všechny funkce [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] včetně náhrad. Pokud znaková sada může být namapována na [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], je podporována. Například GB18030 zavádí některé znaky namapované na rozšíření čínština, japonština a korejština (CFK) a a B a náhradní páry, proto je plně podporovaná. Aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] může použít <xref:System.Globalization.StringInfo> k manipulaci s řetězci bez porozumění, zda mají náhradní páry nebo kombinování znaků.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Návrh mezinárodního uživatelského rozhraní pomocí jazyka XAML
 Tato část popisuje funkce [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], které byste měli zvážit při psaní aplikace.

<a name="intl_text"></a>
### <a name="international-text"></a>Mezinárodní text
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahrnuje integrované zpracování pro všechny systémy Microsoft .NET Framework podporovaného psaní.

 V současné době jsou podporovány následující skripty:

- arabština

- Bengálština

- Koncový

- B

- Řečtina

- Gudžarátština

- Západní

- Hebrejština

- Grafické skripty

- Kannadština

- Laoský

- Znak

- Malajalámština

- Mongolština

- Udijština

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

- Myanmar

- Sinhálské

 Všechny systémové moduly pro psaní podporují písma OpenType. Písma OpenType můžou zahrnovat tabulky rozložení OpenType, které umožňují tvůrcům písem navrhovat lepší mezinárodní a špičková typografická písma. Tabulky rozložení písma OpenType obsahují informace o substitucích glyfů, umístění glyfů, zdůvodnění a umístění standardních hodnot a umožňují aplikacím pro zpracování textu zlepšit rozložení textu.

 Písma OpenType umožňují zpracování rozsáhlých sad glyfů pomocí kódování [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]. Takové kódování umožňuje širokou škálu mezinárodní podpory i pro typografické varianty glyfů.

 vykreslování textu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá technologii Microsoft ClearType sub pixelů, která podporuje nezávislost rozlišení. To významně zlepšuje čitelnost a poskytuje možnost podporovat dokumenty ve stylu časopisu High Quality pro všechny skripty.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Mezinárodní rozložení
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje velmi pohodlný způsob, jak podporovat vodorovná, obousměrná a vertikální rozložení. V prezentačním prostředí lze pomocí vlastnosti <xref:System.Windows.FrameworkElement.FlowDirection%2A> definovat rozložení. Vzorce směru toku jsou:

- *LeftToRight* – horizontální rozložení pro latinkou, východní Asie a tak dále.

- *RightToLeft* – obousměrný pro arabštinu, hebrejštinu a tak dále.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Vývoj lokalizovatelných aplikací
 Při psaní aplikace pro globální spotřebu byste měli mít na paměti, že aplikace musí být lokalizovatelné. Následující témata ukazují, co je potřeba vzít v úvahu.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Vícejazyčné uživatelské rozhraní
 Vícejazyčná uživatelská rozhraní (MUI) je podpora Microsoftu pro přepínání uživatelská rozhraní z jednoho jazyka na jiný. Aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá model sestavení pro podporu rozhraní MUI. Jedna aplikace obsahuje jazykově neutrální sestavení i jazyková sestavení satelitních prostředků závislá na jazyce. Vstupním bodem je spravovaný. EXE v hlavním sestavení.  zavaděč prostředků [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] využívá správce prostředků [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] k podpoře vyhledávání prostředků a záložního použití. Více jazykových satelitních sestavení funguje se stejným hlavním sestavením. Načtené sestavení prostředků závisí na <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> aktuálního vlákna.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Lokalizovatelné uživatelské rozhraní
 aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používají [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] k definování [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] umožňuje vývojářům určit hierarchii objektů se sadou vlastností a logiky. Primární použití [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] slouží k vývoji aplikací [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ale lze je použít k určení hierarchie všech objektů modulu CLR (Common Language Runtime). Většina vývojářů používá [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] k určení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikace a použití programovacího jazyka, jako je C# například reakce na interakci s uživatelem.

 Z pohledu prostředků je soubor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] navržený tak, aby popsal @no__t závislý na jazyku – 1 je element prostředku. proto musí být jeho konečný distribuční formát Lokalizovatelný, aby podporoval mezinárodní jazyky. Protože [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemůže zpracovávat události, mnoho aplikací [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahuje bloky kódu k tomu. Další informace naleznete v tématu [Přehled XAML (WPF)](xaml-overview-wpf.md). Kód se odeberou a zkompiluje do různých binárních souborů, když se soubor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] přihlásí do formátu BAML jazyka XAML. Formulář BAML souborů XAML, obrázků a dalších typů spravovaných objektů prostředků jsou vloženy do satelitního sestavení prostředků, které lze lokalizovat do jiných jazyků, nebo do hlavního sestavení, pokud není nutná lokalizace.

> [!NOTE]
> aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporují všechny prostředky @no__t 1CLR, včetně tabulek řetězců, obrázků a tak dále.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Vytváření lokalizovatelných aplikací
 Lokalizace znamená, že je možné přizpůsobit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jiným kulturám. Aby bylo možné aplikaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizovat, vývojáři potřebují sestavit všechny lokalizovatelné prostředky do sestavení prostředků. Sestavení prostředků je lokalizováno do různých jazyků a kód na pozadí používá rozhraní API pro správu prostředků k načtení. Jeden ze souborů vyžadovaných pro aplikaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je soubor projektu (. proj). Všechny prostředky, které ve vaší aplikaci používáte, by měly být zahrnuté do souboru projektu. Následující příklad ze souboru. csproj ukazuje, jak to provést.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Chcete-li použít prostředek ve vaší aplikaci, vytvořte instanci <xref:System.Resources.ResourceManager> a načtěte prostředek, který chcete použít. Následující příklad ukazuje, jak to provést.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Použití ClickOnce s lokalizovanými aplikacemi
 ClickOnce je nová technologie nasazení model Windows Forms, která bude dodávána se sadou Visual Studio 2005. Umožňuje instalaci aplikace a upgrade webových aplikací. Je-li aplikace nasazená s ClickOnce lokalizována, lze ji zobrazit pouze v lokalizované jazykové verzi. Například pokud je nasazená aplikace lokalizována do japonštiny, lze ji zobrazit pouze v japonštině [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)], ne v anglické verzi Windows. To představuje problém, protože se jedná o běžný scénář pro použití anglické verze systému Windows pro japonské uživatele.

 Řešením tohoto problému je nastavení atributu pro záložní použití neutrálního jazyka. Vývojář aplikace může volitelně odebrat prostředky z hlavního sestavení a určit, že prostředky lze nalézt v satelitním sestavení odpovídajícím konkrétní jazykové verzi. Pro řízení tohoto procesu použijte <xref:System.Resources.NeutralResourcesLanguageAttribute>. Konstruktor třídy <xref:System.Resources.NeutralResourcesLanguageAttribute> má dva signatury, jeden, který přebírá parametr <xref:System.Resources.UltimateResourceFallbackLocation> pro určení umístění, kde by <xref:System.Resources.ResourceManager> mělo extrahovat záložní prostředky: hlavní sestavení nebo satelitní sestavení. Následující příklad ukazuje, jak použít atribut. V případě konečného záložního umístění kód způsobí, <xref:System.Resources.ResourceManager> vyhledat prostředky v podadresáři "de" adresáře aktuálně spuštěného sestavení.

```csharp
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Další informace najdete v tématech

- [Přehled globalizace a lokalizace WPF](wpf-globalization-and-localization-overview.md)
