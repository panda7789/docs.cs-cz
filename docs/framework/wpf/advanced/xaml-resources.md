---
title: Zdroje XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1f9d0ff535d0784343b36d0b2df48b123ff3beef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-resources"></a>Zdroje XAML
Prostředek je objekt, který lze znovu použít na různých místech v aplikaci. Příklady prostředků: štětce a stylů. Tento přehled popisuje, jak používat prostředky v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Můžete také vytvořit a přístup k prostředkům pomocí kódu nebo zcela zaměnitelným významem mezi kódem a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Další informace najdete v tématu [prostředky a kód](../../../../docs/framework/wpf/advanced/resources-and-code.md).  
  
> [!NOTE]
>  Soubory prostředků, které jsou popsané v tomto tématu jsou jiné než soubory prostředků popsaných v [prostředek aplikace WPF, obsah a datové soubory](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md) a jiné než vložené nebo propojené prostředky, které jsou popsané v [ Správa prostředků aplikace (.NET)](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
  
<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Pomocí prostředků v jazyce XAML  
 V následujícím příkladu definuje <xref:System.Windows.Media.SolidColorBrush> jako prostředek v kořenovém elementu stránky. V příkladu se pak odkazuje na prostředek a používá pro nastavení vlastností několik podřízených elementů, včetně <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Controls.TextBlock>a <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FEResourceSH_snip#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Každý element úrovni rozhraní (<xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>) má <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost, která je vlastnost, která obsahuje prostředky (jako <xref:System.Windows.ResourceDictionary>) definující prostředku. Můžete definovat prostředků u libovolného elementu. Ale prostředky jsou nejčastěji definované v kořenovém elementu, který je <xref:System.Windows.Controls.Page> v příkladu.  
  
 Všechny prostředky v slovník prostředků, a musí mít jedinečný klíč. Když definujete prostředky v značek, přiřadíte jedinečný klíč prostřednictvím [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md). Klíč je obvykle řetězec; však můžete také nastavit ho na jiné typy objektů pomocí rozšíření odpovídající značek. Neřetězcový klíče pro prostředky používají určité oblasti funkcí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zejména pro styly, součástí zdroje a data stylů.  
  
 Po definování prostředek, můžete odkazovat prostředek, který se použije pro hodnotu vlastnosti pomocí syntaxe značek rozšíření prostředků, který určuje název klíče, například:  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 V předchozím příkladu při [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zavaděč zpracovává hodnota `{StaticResource MyBrush}` pro <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.Button>, logiku vyhledávání prostředků nejdřív zkontroluje slovník prostředků pro <xref:System.Windows.Controls.Button> element. Pokud <xref:System.Windows.Controls.Button> nemá definici klíč prostředku `MyBrush` (ne; jeho kolekce prostředků je prázdná), vyhledávací dále zkontroluje nadřazený element <xref:System.Windows.Controls.Button>, což je <xref:System.Windows.Controls.Page>. Proto když definujete prostředek na <xref:System.Windows.Controls.Page> kořenový element, všechny elementy ve logického stromu <xref:System.Windows.Controls.Page> k němu přístup, a pro nastavení hodnota libovolné vlastnosti, která přijímá můžete znovu použít stejný zdroj <xref:System.Type> který prostředku představuje. V předchozím příkladu, stejné `MyBrush` nastaví dvě různé vlastnosti prostředku: <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>a <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Statické a dynamické prostředky  
 Prostředek může být odkaz jako prostředek statické nebo dynamické prostředků. To se provádí pomocí buď [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) nebo [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Rozšíření kódu je funkce [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jímž odkaz na objekt můžete zadat tak, že rozšíření značek zpracovat řetězec atributu a vrátí objekt, který má [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zavaděč. Další informace o chování rozšíření značek najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Pokud použijete rozšíření značek, je obvykle zadat jeden nebo více parametrů v podobě řetězce, které jsou zpracovány v tomto rozšíření konkrétní značku, nikoli vyhodnocovaný v kontextu vlastnost je nastavena na možnost. [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) zpracovává klíč vyhledáním hodnota tohoto klíče ve slovnících všech dostupných prostředků. K tomu dojde během načítání, který je bod v čase, když je proces načítání potřebuje přiřadit hodnotu vlastnosti, která přebírá odkaz statické prostředků. [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) místo procesy klíč vytvořením výrazu a že výraz zůstane unevaluated dokud ve skutečnosti spuštěna aplikace, které během výraz vyhodnotí a poskytuje hodnotu.  
  
 Při odkazu na prostředek, můžete ovlivnit následující aspekty, zda použít odkaz na statické prostředků nebo odkaz na dynamické prostředků:  
  
-   Celkový návrh, jak vytvořit prostředky pro aplikaci (na stránce v aplikaci ve ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], v sestavení pouze prostředků).  
  
-   Funkčnost aplikace: aktualizuje prostředky v reálném čase součástí vaše požadavky aplikací?  
  
-   Chování příslušných vyhledávání odkaz na typ tohoto prostředku.  
  
-   Konkrétní vlastnost nebo typ prostředku a nativní chování těchto typů.  
  
### <a name="static-resources"></a>Statické prostředky  
 Statické prostředků odkazuje pracovní nejlépe za těchto okolností:  
  
-   Slovník soustřeďuje nejvíce všechny jeho prostředky do stránky nebo prostředků s úrovní aplikace návrhu aplikace. Odkazy statické prostředků nejsou již znovu podle chování modulu runtime, jako je například opětovné načtení stránky, a proto může být ke některé výhody výkonu zabraňující velké množství prostředků dynamické odkazy, při nejsou nutné na prostředek a návrh aplikace.  
  
-   Nastavíte hodnotu vlastnosti, která není na <xref:System.Windows.DependencyObject> nebo <xref:System.Windows.Freezable>.  
  
-   Vytváříte slovník prostředků, který se zkompiluje do knihovny DLL a zabalené jako součást aplikace nebo sdílené mezi aplikacemi.  
  
-   Vytváření motiv vlastního ovládacího prvku a se definice prostředků, které se používají v rámci motivy. Pro tento případ obvykle nechcete chování vyhledávání dynamické prostředků odkazu, odkaz chování statické prostředků chcete místo toho, aby vyhledávání předvídatelný a nezávislý na motiv. Dynamické prostředků odkaz, i odkaz v rámci motiv je ponechán unevaluated dokud runtime a může se stát, když motiv použité, některé místní element bude znovu definovat klíče, který motivu se pokouší odkazovat a místní prvek bude spadat předchozí pro motiv samotné při vyhledávání. Pokud k tomu dojde, nebude motivu chovat očekávaným způsobem.  
  
-   Prostředky používají k nastavení velké množství vlastností závislostí. Vlastnosti závislosti mít platnou hodnotu ukládání do mezipaměti jako povolené vlastnosti systému, takže pokud zadáte hodnotu pro vlastnost závislosti, které lze vyhodnotit na čas načítání, vlastnost závislosti nemá zkontrolujte výraz reevaluated a vrátit poslední platnou hodnotu. Tento postup může být výhody výkonu.  
  
-   Chcete změnit základní prostředků pro všichni příjemci, nebo chcete zachovat samostatné zapisovatelné instance pro každý příjemce pomocí [x: sdílené atribut](../../../../docs/framework/xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Chování vyhledávání statické prostředků  
  
1.  Proces vyhledávání zkontroluje požadovaný klíč ve slovníku prostředků definované elementu, který nastaví vlastnost.  
  
2.  Proces vyhledávání pak prochází logického stromu směrem nahoru, nadřazeného elementu a jeho slovník prostředků. Tento postup se opakuje, dokud nebude dosaženo kořenový element.  
  
3.  V dalším kroku se kontroluje prostředky aplikace. Prostředky aplikace jsou tyto prostředky v rámci slovníku prostředku, který je definován <xref:System.Windows.Application> objekt pro vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
 Statické prostředků odkazy z v rámci slovník prostředků, a musí odkazovat na prostředek, který již byl definován lexikálně před odkaz na prostředek. Předat dál odkazy se nedají vyřešit odkazem statické prostředků. Z tohoto důvodu Pokud používáte statické prostředků odkazy, je nutné vytvořit strukturu slovník prostředků tak, aby prostředky určený k použití podle prostředků jsou definovány v nebo na začátku každého slovník příslušných prostředků.  
  
 Statické prostředků vyhledávání můžete rozšířit do motivy nebo do systémových prostředků, ale to je podporováno, protože [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zavaděč odkládat údaje žádosti. Odložení je nutné, aby v době, kdy stránka načte motiv runtime správně platí pro aplikaci. Statické prostředků však odkazuje ke klíčům, které existují pouze v motivy nebo jako systém, které prostředky se nedoporučují. Je to proto, že tyto odkazy nejsou již znovu, pokud dojde ke změně motiv uživatelem v reálném čase. Odkaz na dynamické prostředků je spolehlivější při žádosti o motiv nebo dostatek systémových prostředků. Výjimkou je, když samotný prvek motiv požaduje jiný prostředek. Tyto odkazy musí být statické prostředků odkazy z důvodů uvedených výše.  
  
 Výjimka chování, pokud není nalezena odkaz statické prostředků se bude lišit. Pokud byla odložena prostředku, výjimka nastává za běhu. Pokud prostředek nebyl odložení, výjimka dojde v okamžiku načtení.  
  
### <a name="dynamic-resources"></a>Dynamické prostředky  
 Dynamické prostředky nejvhodnější pro v těchto případech:  
  
-   Hodnota prostředku závisí na podmínky, které nejsou známá, dokud modulu runtime. To zahrnuje systémové prostředky a prostředky, které jsou jinak uživatele nastavit. Například můžete vytvořit setter hodnoty, které odkazují na vlastnosti systému jako vystavené <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>, nebo <xref:System.Windows.SystemParameters>. Tyto hodnoty jsou skutečně dynamické, protože se nakonec z prostředí runtime uživatele a operačního systému. Také může mít motivů na úrovni aplikace, které můžete změnit, kde přístup k prostředkům úrovně stránky musí zachytit změny.  
  
-   Vytváříte nebo odkazy na styly motivů vlastního ovládacího prvku.  
  
-   Chcete-li upravit obsah <xref:System.Windows.ResourceDictionary> během životního cyklu aplikace.  
  
-   Máte složitý prostředků strukturu, která má vzájemné závislosti, kde může být nutný dopředného odkaz. Statické prostředků odkazy nepodporují dopředného odkazy, ale dynamické prostředků odkazy podporují, je vzhledem k tomu, že prostředek není potřeba vyhodnotí dokud runtime a předat dál odkazy nejsou proto relevantní koncept.  
  
-   Odkazují na prostředek, který je obzvláště velký z perspektivy kompilaci nebo pracovní sady a prostředek se možná nepoužívají při načtení stránky okamžitě. Statické prostředků odkazy vždy načíst z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] při načtení stránky; však není odkaz na dynamické prostředků zatížení, dokud se ve skutečnosti používá.  
  
-   Při vytváření stylu, které může metoda setter hodnoty pocházejí z jiné hodnoty, které jsou ovlivněné motivy nebo jiná nastavení uživatele.  
  
-   Prostředky jsou připojení k prvkům, které může během životního cyklu aplikace nadřazeny v logickém stromu. Změna nadřazené také potenciálně změní oboru vyhledávání prostředků, takže pokud chcete prostředek pro znovu vyhodnocena jako reparented element založené na nový obor, vždy použijte odkaz na dynamické prostředků.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Chování vyhledávání dynamické prostředků  
 Chování vyhledávání prostředků pro odkaz na dynamické prostředků je paralelní chování vyhledávání ve vašem kódu při volání <xref:System.Windows.FrameworkElement.FindResource%2A> nebo <xref:System.Windows.FrameworkElement.SetResourceReference%2A>.  
  
1.  Proces vyhledávání zkontroluje požadovaný klíč ve slovníku prostředků definované elementu, který nastaví vlastnost.  
  
    -   Pokud element definuje <xref:System.Windows.FrameworkElement.Style%2A> vlastnost, <xref:System.Windows.Style.Resources%2A> slovníku v rámci <xref:System.Windows.Style> je zaškrtnuté.  
  
    -   Pokud element definuje <xref:System.Windows.Controls.Control.Template%2A> vlastnost, <xref:System.Windows.FrameworkTemplate.Resources%2A> slovníku v rámci <xref:System.Windows.FrameworkTemplate> je zaškrtnuté.  
  
2.  Proces vyhledávání pak prochází logického stromu směrem nahoru, nadřazeného elementu a jeho slovník prostředků. Tento postup se opakuje, dokud nebude dosaženo kořenový element.  
  
3.  V dalším kroku se kontroluje prostředky aplikace. Prostředky aplikace jsou tyto prostředky v rámci slovníku prostředku, který je definován <xref:System.Windows.Application> objekt pro vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
4.  Motiv slovník prostředků, se kontroluje na aktuálně aktivní motivu. Pokud motiv změní za běhu, hodnota je již znovu.  
  
5.  Systémové prostředky jsou zaškrtnutá políčka.  
  
 Výjimka chování (pokud existuje) se liší:  
  
-   Pokud byl prostředek požadoval <xref:System.Windows.FrameworkElement.FindResource%2A> volání a nebyl nalezen, je vyvolána výjimka.  
  
-   Pokud byl prostředek požadoval <xref:System.Windows.FrameworkElement.TryFindResource%2A> volání a nebyl nalezen žádný došlo k výjimce, ale je vrácená hodnota `null`. Pokud se nastavuje vlastnost nepřijímá `null`, je stále možné, že, bude vyvolána výjimka hlubší (to závisí na jednotlivé vlastnosti nastaveno).  
  
-   Pokud byl prostředek požadoval odkaz dynamické prostředků v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]a nebyl nalezen, pak chování závisí na obecné vlastnosti systému, ale je obecné chování, jako kdyby žádná operace nastavení vlastností došlo k chybě na úrovni, kde existuje prostředek. Například pokud se pokusíte nastavit na pozadí na jednotlivé tlačítko elementu s použitím na prostředek, který nebylo možné vyhodnotit, pak nastavena žádná hodnota výsledků, ale efektivní hodnota stále mohou pocházet z ostatní účastníci prioritu systému a hodnotu vlastnosti. Hodnota pozadí pro instanci stále může pocházet z styl místně definované tlačítka nebo styl motivu. Pro vlastnosti, které nejsou definované styly motivů může efektivní hodnota po vyhodnocení prostředek, který selhal pocházet z výchozí hodnotu v metadata vlastnosti.  
  
#### <a name="restrictions"></a>Omezení  
 Dynamické prostředků odkazy mají některé významné omezení. Alespoň jeden z následujících musí být splněné:  
  
-   Vlastnost Probíhá nastavení musí být vlastnost na <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Vlastnost musí zajišťoval <xref:System.Windows.DependencyProperty>.  
  
-   Je odkaz na hodnotu v rámci <xref:System.Windows.Style> <xref:System.Windows.Setter>.  
  
-   Vlastnost Probíhá nastavení musí být vlastnost na <xref:System.Windows.Freezable> který je zadaný jako hodnota buď <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> vlastnost, nebo <xref:System.Windows.Setter> hodnotu.  
  
 Protože musí být vlastnost nastavena <xref:System.Windows.DependencyProperty> nebo <xref:System.Windows.Freezable> vlastnost většinu změn vlastnost se může rozšířit do uživatelského rozhraní protože potvrdí se systémem vlastnost změnu vlastnosti (hodnota změněné dynamické prostředků). Většina ovládací prvky zahrnují logiky, která vynutí jiné rozložení ovládacího prvku, pokud <xref:System.Windows.DependencyProperty> změny a že vlastnost může mít vliv na rozložení. Ale ne všechny vlastnosti jejichž [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) jako jejich hodnota je zaručeno, zadejte hodnotu tak, že aktualizace v reálném čase v uživatelském rozhraní. Tato funkcionalita přesto se mohou lišit v závislosti na vlastnosti, a také v závislosti na typu, který vlastní vlastnost nebo i logické struktury vaší aplikace.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Styly, DataTemplates a implicitní klíčů  
 Dříve, bylo uvedeno, že všechny položky v <xref:System.Windows.ResourceDictionary> musí mít klíč. Ale který neznamená, že všechny prostředky musí mít explicitního `x:Key`. Několik typů objektů podporovat klíčem implicitní, pokud je definována jako prostředek, kde je hodnota klíče vázaný na hodnotu jiné vlastnosti. To se označuje jako implicitní klíč, zatímco `x:Key` atribut je explicitní klíčem. Všechny implicitní klíč můžete přepsat zadáním explicitní klíč.  
  
 Jeden scénář velmi důležité pro prostředky je při definování <xref:System.Windows.Style>. Ve skutečnosti <xref:System.Windows.Style> téměř vždy definována jako položku do slovníku prostředků, protože styly jsou ze své podstaty určené pro opakované použití. Další informace o styly najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Styly pro ovládací prvky může být vytvořen s i odkazovaná adresou implicitní klíč. Styly motivů, které definují výchozí vzhledu ovládacího prvku spoléhají na tento implicitní klíč. Implicitní klíč z hlediska o to požádá je <xref:System.Type> samotného ovládacího prvku. Implicitní klíč z hlediska definice prostředku je <xref:System.Windows.Style.TargetType%2A> stylu. Proto pokud vytváříte motivy pro vlastní ovládací prvky, vytváření stylů, které pracují s existující styly motivů, není nutné zadat [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) pro tento <xref:System.Windows.Style>. A pokud chcete použít motivu stylů, není potřeba zadat libovolný styl vůbec. Například následující definici stylu funguje, i když <xref:System.Windows.Style> prostředků nezobrazí klíč:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Styl skutečně splnit klíč: implicitní klíč `typeof(` <xref:System.Windows.Controls.Button> `)`. V kódu, můžete zadat <xref:System.Windows.Style.TargetType%2A> přímo jako typ name (nebo můžete volitelně použít [{x: Type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md) Chcete-li se vrátit <xref:System.Type>.  
  
 Pomocí výchozí motiv styl mechanismů používaných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], stylem jako styl runtime <xref:System.Windows.Controls.Button> na stránce, i když <xref:System.Windows.Controls.Button> samotné nebude pokoušet o zadejte jeho <xref:System.Windows.FrameworkElement.Style%2A> vlastnost nebo konkrétní prostředek odkaz na styl. Vaše styl na stránce definován nachází v dřívější části pořadí vyhledávání starší než styl slovník motiv pomocí stejného klíče s styl slovník motivu. Můžete jenom zadat `<Button>Hello</Button>` kdekoli v stránky a styl definovaný s <xref:System.Windows.Style.TargetType%2A> z `Button` by použít na toto tlačítko. Pokud chcete, můžete stále explicitně klíče styl se stejnou hodnotou typu jako <xref:System.Windows.Style.TargetType%2A>, pro přehlednost ve vašem kódu, ale je volitelné.  
  
 Implicitní klíče pro styly se nevztahují na ovládací prvek, pokud <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> je `true` (Všimněte si také, že <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> může být nastaveno jako součást nativní chování pro třídu ovládacího prvku, nikoli explicitně na instanci ovládacího prvku). Také, aby bylo možné podporovat implicitní klíče pro scénáře odvozené třídy, musí přepsat ovládacího prvku <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (všechny stávající ovládací prvky, které jsou k dispozici jako součást [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tomu). Další informace o styly, motivů a ovládací prvek návrhu najdete v tématu [pokyny pro návrh Stylable ovládací prvky](../../../../docs/framework/wpf/controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate>také obsahuje implicitní klíče. Implicitní klíč pro <xref:System.Windows.DataTemplate> je <xref:System.Windows.DataTemplate.DataType%2A> hodnotu vlastnosti. <xref:System.Windows.DataTemplate.DataType%2A>dá se zadat taky jako název typu, nikoli explicitně pomocí [{x: Type...} ](../../../../docs/framework/xaml-services/x-type-markup-extension.md). Podrobnosti najdete v tématu [přehled Ukázka dat](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.ResourceDictionary>  
 [Prostředky aplikace](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Prostředky a kódu](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [Definování a odkazovat na prostředek](../../../../docs/framework/wpf/advanced/how-to-define-and-reference-a-resource.md)  
 [Přehled správy aplikací](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [x: Type – rozšíření značek](../../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [– Rozšíření značek StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [– Rozšíření značek DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
