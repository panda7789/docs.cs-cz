---
title: Přehled prvku TextPattern automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: e8358a4a4e0b4933670a2f01dfdf4dd9a7aa43cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409877"
---
# <a name="ui-automation-textpattern-overview"></a>Přehled prvku TextPattern automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled popisuje způsob použití [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vystavit textový obsah, včetně formátu a stylu atributy prvků textu v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-podporované platformy. Tyto ovládací prvky patří, ale nejsou omezeny na rozhraní Microsoft .NET Framework <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> a také jejich [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ekvivalenty.  
  
 Vystavení textový obsah ovládacího prvku se provádí prostřednictvím <xref:System.Windows.Automation.TextPattern> – vzor ovládacích prvků, která představuje obsah kontejneru text jako datový proud text. Pak <xref:System.Windows.Automation.TextPattern> vyžaduje podporu <xref:System.Windows.Automation.Text.TextPatternRange> třída vystavit formátu a stylu atributy. <xref:System.Windows.Automation.Text.TextPatternRange> podporuje <xref:System.Windows.Automation.TextPattern> podle představující souvislý nebo několika nesouvislé rozpětí textu v zásobníku textu s kolekcí <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> a <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncové body. <xref:System.Windows.Automation.Text.TextPatternRange> podporuje funkce, jako je výběr, porovnání, načítání a traversal.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern> Neposkytují znamená vložit nebo upravit text. Nicméně, v závislosti na ovládací prvek, to může udělat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> nebo prostřednictvím přímé klávesnice vstup. Najdete v článku [ukázkový Text vložte TextPattern](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16) příklad.  
  
 Funkce popsané v tomto přehledu je životně důležité technologie usnadnění dodavatele a své koncové uživatele. Technologie pro usnadnění můžete použít [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] shromažďovat informace o uživateli formátování textu, dokončení a poskytují programový navigaci a výběr textu pomocí <xref:System.Windows.Automation.Text.TextUnit> (znak, word, řádek nebo odstavce).  
  
<a name="UI_Automation_TextPattern_vs__Cicero"></a>   
## <a name="ui-automation-textpattern-vs-text-services-framework"></a>TextPattern automatizace uživatelského rozhraní vs. Text Services Framework  
 [!INCLUDE[TLA#tla_tsf](../../../includes/tlasharptla-tsf-md.md)] je jednoduchý a škálovatelné systému rozhraní, které umožňuje službám přirozeného jazyka a pokročilé textový vstup na ploše a v aplikacích. Kromě rozhraní pro aplikace ke zveřejnění jejich úložiště text také podporuje metadata pro toto úložiště text.  
  
 Ale [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] byl navržený pro aplikace, které je třeba vložit vstup do kontextově scénáře, zatímco <xref:System.Windows.Automation.TextPattern> je jen pro čtení řešení (s omezenou řešení uvedených výše) určená k poskytování optimalizované přístupu k úložišti text pro čtečky obrazovky a Braillovo písmo zařízení.  
  
 Stručně řečeno, můžete použít přístupné technologie, které vyžadují přístup jen pro čtení k úložišti text <xref:System.Windows.Automation.TextPattern>, ale budou potřebovat složitější funkce [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] pro kontextově vstup.  
  
<a name="Control_Types"></a>   
## <a name="control-types"></a>Typy ovládacích prvků  
  
#### <a name="text"></a>Text  
 Ovládací prvek Text je základní prvek představující část textu na obrazovce.  
  
 Ovládací prvek text samostatné slouží jako popisek nebo statický text ve formuláři. Ovládací prvky text může být také obsažený v rámci strukturu <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> nebo <xref:System.Windows.Automation.ControlType.DataItem>.  
  
> [!NOTE]
>  Ovládacích prvků textu, se nemusí zobrazit v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu (viz [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)). To je proto ovládacích prvků textu se často zobrazují prostřednictvím vlastnost název jiného ovládacího prvku. Text, který slouží k označení ovládací prvek upravit pro instanci, jsou dostupné prostřednictvím vlastnost názvu ovládacích prvků pro úpravy. Vzhledem k tomu, že je ovládací prvek upravit v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, není nutné pro text elementu samotného v tomto zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. Pouze text, který se zobrazí v zobrazení obsahu je text, který není redundantní informace. To umožňuje rychle filtrovat pouze na řadu informací, které uživatelé potřebují všechny využívajících technologie usnadnění.  
  
#### <a name="edit"></a>Upravit  
 Upravte ovládací prvky povolit uživatelům zobrazení a úpravy na jednom řádku textu.  
  
> [!NOTE]
>  V některých scénářích rozložení může obtékat jednoho řádku textu.  
  
#### <a name="document"></a>Dokument  
 Ovládací prvky dokument může uživatel přejděte a získat informace z více stránek textu.  
  
<a name="TextPattern_Client_API_s"></a>   
## <a name="textpattern-client-apis"></a>TextPattern klientské rozhraní API  
  
|||  
|-|-|  
|`System.Windows.Automation.TextPattern Class`|Vstupní bod pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] text modelu.<br /><br /> Tato třída také obsahuje dva <xref:System.Windows.Automation.TextPattern> naslouchacích procesů událostí, <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> a <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|  
|`System.Windows.Automation.Text.TextPatternRange Class`|Reprezentace rozpětí textu v rámci kontejner text, který podporuje <xref:System.Windows.Automation.TextPattern>.<br /><br /> Klienti automatizace uživatelského rozhraní měli být opatrní aktuální platnosti rozsahu text vytvořený <xref:System.Windows.Automation.Text.TextPatternRange>. Pokud původní text v ovládacím prvku text nahrazuje zcela nový text, stává neplatným aktuálním rozsahu textu. Ale rozsah text může ještě některé životnost pokud jenom součástí původní text se změní a spravuje textu jeho základní ovládací prvek text "ukazatel" s kotvy (nebo koncových bodů) a nikoli s umístěním absolutní znak.<br /><br /> Klienti mohou naslouchat <xref:System.Windows.Automation.TextPattern.TextChangedEvent> pro oznámení o všech změnách textový obsah pracují s.|  
|`System.Windows.Automation.AutomationTextAttribute Class`|Použít k identifikaci atributy formátování textu rozsahu.|  
  
<a name="TextPattern_Provider_API_s"></a>   
## <a name="textpattern-provider-apis"></a>TextPattern poskytovatele rozhraní API  
 Prvky uživatelského rozhraní nebo ovládací prvky, které podporují <xref:System.Windows.Automation.TextPattern> implementací <xref:System.Windows.Automation.Provider.ITextProvider> a <xref:System.Windows.Automation.Provider.ITextRangeProvider> rozhraní, buď nativně nebo pomocí [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] proxy servery, podporují vystavení atribut podrobné informace pro jakýkoli text obsahují v Přidání poskytovat robustní navigační možnosti.  
  
 A <xref:System.Windows.Automation.TextPattern> zprostředkovatele nemusí podporovat všechny atributy textu, pokud chybí podpora pro všechny konkrétní atributy ovládacího prvku.  
  
 A <xref:System.Windows.Automation.TextPattern> musí podporovat zprostředkovatele <xref:System.Windows.Automation.TextPattern.GetSelection%2A> a <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> funguje v případě, že ovládací prvek podporuje výběr textu nebo umístění kurzoru text (nebo systémový znak) v části textu. Pokud ovládací prvek nepodporuje tuto funkci pak nemusí podporovat některé z těchto metod. Ovládací prvek však musí vystavit typ podporuje implementací výběr textu <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> vlastnost.  
  
 A <xref:System.Windows.Automation.TextPattern> zprostředkovatele musí podporovat vždy <xref:System.Windows.Automation.Text.TextUnit> konstanty <xref:System.Windows.Automation.Text.TextUnit.Character> a <xref:System.Windows.Automation.Text.TextUnit.Document> a také všechny další <xref:System.Windows.Automation.Text.TextUnit> konstanty je schopný zajistit podporu.  
  
> [!NOTE]
>  Zprostředkovatel může přeskočit podporu pro konkrétní <xref:System.Windows.Automation.Text.TextUnit> rozlišením na další největší <xref:System.Windows.Automation.Text.TextUnit> podporované v následujícím pořadí: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page>, a <xref:System.Windows.Automation.Text.TextUnit.Document> .  
  
|||  
|-|-|  
|`ITextProvider Interface`|Poskytuje metody, vlastnosti a atributů, které podporují <xref:System.Windows.Automation.TextPattern> v klientských aplikacích (viz <xref:System.Windows.Automation.Provider.ITextProvider>).|  
|`ITextRangeProvider Interface`|Reprezentuje rozpětí textu v textu zprostředkovatele (viz <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|  
|`System.Windows.Automation.TextPatternIdentifiers Class`|Obsahuje hodnoty, které jsou použity jako identifikátory pro zprostředkovatele text (viz <xref:System.Windows.Automation.TextPatternIdentifiers>).|  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpečení  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Architektura byl navržen s důrazem na bezpečnost (viz [Přehled zabezpečení automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-security-overview.md)). TextPattern třídy popsané v tomto přehledu ale vyžadovat některé specifické aspekty zabezpečení.  
  
-   [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] poskytovatelé text zadat jen pro čtení rozhraní a neposkytuje možnost měnit existující text v ovládacím prvku.  
  
-   Klienti automatizace uživatelského rozhraní lze použít pouze [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Pokud jsou plně "důvěryhodné". Příkladem tohoto může být chráněný plochy přihlášení, kde můžete spustit pouze známé a důvěryhodné aplikace.  
  
-   Vývojáři zprostředkovatelů automatizace uživatelského rozhraní měli vědět, že všechny informace se rozhodnete vystavit v jejich ovládacích prvcích prostřednictvím [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] je v podstatě veřejné a plně přístupné jiným kódem. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] nesnaží určit že důvěryhodnost libovolného automatizace uživatelského rozhraní klienta a proto zprostředkovatele automatizace uživatelského rozhraní by neměli zveřejňovat chráněného obsahu nebo citlivé textové informace (například pole heslo).  
  
-   Jednou z nejvýznamnějších změn v zabezpečení pro [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] je široce označovány jako "Zabezpečení vstup" což zahrnuje technologie jako nejméně privilegovaným (nebo omezené) uživatelské účty (LUA) a uživatelského rozhraní oprávnění úroveň izolace (UIPI).  
  
    -   UIPI zabraňuje jeden program z řízení nebo monitorování jiné další "privilegované" programu, prevence útoků zpráva okno mezi procesy, které zfalšovat vstup uživatele.  
  
    -   LUA nastaví omezení oprávnění aplikací spuštěn pomocí uživatele ve skupině Administrators. Aplikace nemusí mít oprávnění správce, ale místo toho se spustí s nejnižšími oprávněními, které jsou nezbytné. V důsledku toho může být určitá omezení vynucení LUA scénáře. Zejména řetězec zkrácení (včetně TextPattern řetězce), kde může být nezbytné k omezení velikosti řetězce načítány z úrovni správce aplikací, nejsou vynucené přidělit paměť do bodu zakázání aplikace.  
  
<a name="Performance"></a>   
## <a name="performance"></a>Výkon  
 Protože TextPattern závisí na volání mezi procesy pro většinu ze svých funkcí, neposkytuje mechanismus ukládání do mezipaměti ke zlepšení výkonu při zpracování obsahu. Jde na rozdíl od jiných vzorů ovládacích prvků v [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] který lze přistupovat pomocí <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> metody.  
  
 Jeden cílem pro zlepšení výkonu je tím, že zajistí klienti automatizace uživatelského rozhraní se pokusí získat středně velkých bloky text použití <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Například GetText(1) volání je zpoplatněná přístupů mezi procesy pro každý znak, že jedno volání GetText(-1) zpoplatněná vstupů do jednoho mezi procesy, ale může mít vysokou latencí, v závislosti na velikosti text zprostředkovatele.  
  
<a name="Glossary"></a>   
## <a name="textpattern-terminology"></a>TextPattern terminologie  
 **Atribut**  
 Formátování vlastnosti rozsahu text (například <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> nebo <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).  
  
 **Rozsah degenerovanou**  
 Degenerovanou rozsah je prázdné nebo nulové znak textu. Pro účely vzor TextPattern ovládacích prvků textového kurzoru (nebo systémový znak) považuje za degenerovanou rozsahu. Pokud není vybraný žádný text, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> by vrátit na degenerovanou rozsah bod pro vložení textu a <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> by vrátit degenerovanou rozsah jako svůj výchozí koncový bod. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> a <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> může vracet degenerovanou rozsahy zprostředkovatele textu nelze najít žádné textové rozsahy, které splňují danou podmínku. Tento rozsah degenerovanou slouží jako výchozí koncový bod v rámci zprostředkovatele text. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A> a <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> vrátit odkaz s hodnotou null (`Nothing` v aplikaci Microsoft Visual Basic .NET) k zamezení nejasnostem s rozsahem zjištěných versus degenerovanou rozsahu.  
  
 **Vložený objekt**  
 Existují dva typy vložené objekty v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text modelu. Skládají se z založený na textu obsahu prvky, jako jsou například hypertextových odkazů nebo tabulky a ovládací prvky, jako jsou bitové kopie a tlačítka. Podrobnější informace najdete v části [přístup vložené objekty pomocí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md).  
  
 **Endpoint**  
 Absolutní <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> nebo <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> bodu rozsahu textu v rámci kontejneru text.  
  
 ![Výčty TextPatternRangeEndpoint &#40;začínat a končit&#41;. ] (../../../docs/framework/ui-automation/media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")  
Následující znázorňuje sadu počáteční a koncový bod.  
  
 **TextRange**  
 Reprezentace rozpětí textu, počáteční a koncový bod, v textu kontejneru, včetně všech přidružených atributů a funkce.  
  
 <xref:System.Windows.Automation.Text.TextUnit>  
 Předem definované jednotka text (znak, word, řádek nebo odstavce) použitý pro procházení segmenty logickou rozsahu text.  
  
## <a name="see-also"></a>Viz také  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Text Services Framework](http://msdn.microsoft.com/library/default.asp?url=/library/tsf/tsf/text_services_framework.asp)
