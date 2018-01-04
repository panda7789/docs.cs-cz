---
title: "Stromy v subsystému WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73c34f8edfa735e361bf294f08cefd285be3e898
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="trees-in-wpf"></a>Stromy v subsystému WPF
V mnoha technologií prvky a součásti jsou uspořádány do stromové struktury, kde vývojáři přímo upravit objekt uzly ve stromu ovlivnit vykreslování nebo chování aplikace. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]definování vztahů mezi elementy program také používá několik metaphors struktura stromu. Ve většině případů WPF vývojáři můžete vytvořit aplikaci v kódu nebo definovat části aplikace v jazyce XAML při koncepčně zamyšlení jedná stromu objektu, ale bude volání rozhraní API konkrétní nebo pomocí konkrétní značek udělat tak místo některé obecné objekt stromu manipulaci API například můžete použít v modelu DOM. XML WPF zpřístupní dva pomocných tříd, které poskytují jedná je stromové zobrazení <xref:System.Windows.LogicalTreeHelper> a <xref:System.Windows.Media.VisualTreeHelper>. Vizuálním stromu podmínky a logickém stromu používají také v dokumentaci k WPF vzhledem k tomu, že tyto stejné struktury jsou užitečné pro seznámení s chováním některých klíčových funkcí WPF. Toto téma definuje, co představují vizuální strojové struktuře a logickém stromu, popisuje, jak takový stromy vztahují k celkové stromu koncepce objektu a zavádí <xref:System.Windows.LogicalTreeHelper> a <xref:System.Windows.Media.VisualTreeHelper>s.  
  

  
<a name="element_tree"></a>   
## <a name="trees-in-wpf"></a>Stromy v subsystému WPF  
 Nejúplnější stromové struktury v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je stromu objektů. Pokud definujete stránku aplikace v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a pak můžete načíst [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], stromová struktura je založeno na vnoření relaci elementů do kódu. Pokud definujete aplikace nebo je vytvořena část v kódu aplikace, pak se stromovou strukturu založená na tom, jak přiřadit hodnoty vlastností pro vlastnosti, které implementují modelu obsahu pro daný objekt. V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], existují dva způsoby, které stromu kompletní objekt je conceptualized a mohou být oznámeny jeho veřejné rozhraní API: jako logického stromu a jako vizuálním stromu. Rozdíly mezi logického stromu a vizuálním stromu vždy nejsou nezbytně důležité, ale někdy se může způsobit problémy s určité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] subsystémy a vliv možností, které provedete v kód.  
  
 I když není vždy pracovat s logického stromu nebo vizuálním stromu přímo, seznámení s koncepty interakci stromy je užitečné pro pochopení WPF technologií. Myslíme WPF jako strom jedná určitého druhu je také velmi důležitý k pochopení, jak se dědičnost vlastnosti a události směrování fungují v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
> [!NOTE]
>  Strom objektů je více koncept než skutečná rozhraní API, a proto je jiný způsob, jak si můžete představit koncept jako grafu objektu. V praxi existují vztahy mezi objekty v době běhu, kde bude rozdělíme jedná stromu. Zejména pomocí uživatelského rozhraní definované XAML, je nicméně dostatečně relevantní, že většina dokumentace WPF použije stromu objektů termín při odkazování na tento koncept obecné jedná stromu.  
  
<a name="logical_tree"></a>   
## <a name="the-logical-tree"></a>Logickém stromu.  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], přidejte obsah k elementům uživatelského rozhraní nastavením vlastnosti objektů, které zálohují těchto elementů. Například můžete přidat položky do <xref:System.Windows.Controls.ListBox> řízení manipulací s jeho <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastnost. Díky tomu jsou umístění položky do <xref:System.Windows.Controls.ItemCollection> to znamená <xref:System.Windows.Controls.ItemsControl.Items%2A> hodnotu vlastnosti. Podobně, chcete-li přidat objekty do <xref:System.Windows.Controls.DockPanel>, pracovat s jeho <xref:System.Windows.Controls.Panel.Children%2A> hodnotu vlastnosti. Zde jsou přidávání objektů do <xref:System.Windows.Controls.UIElementCollection>. Příklad kódu, najdete v části [k elementu dynamicky přidat](http://msdn.microsoft.com/en-us/d00f258a-7973-4de7-bc54-a3fc1f638419).  
  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], při umístění položky v seznamu <xref:System.Windows.Controls.ListBox> nebo ovládací prvky nebo jiných prvků uživatelského rozhraní <xref:System.Windows.Controls.DockPanel>, můžete také použít <xref:System.Windows.Controls.ItemsControl.Items%2A> a <xref:System.Windows.Controls.Panel.Children%2A> vlastnosti, explicitně nebo implicitně, jako v následujícím příkladu.  
  
 [!code-xaml[TreeOvwsSupport#AllCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 Pokud jste při zpracování této XAML ve formátu XML v rámci modelu objektu dokumentu, a pokud měl zahrnuté značky komentář out jako implicitní (který by byl právní), pak by mohl obsahovat výsledný strom CODEDOM XML prvky pro `<ListBox.Items>` a další implicitní položky. Ale XAML nezpracovává tímto způsobem, pokud je kód pro čtení a zápis objektů, výsledný objekt grafu neobsahuje oznámena `ListBox.Items`. Ale mít <xref:System.Windows.Controls.ListBox> vlastnost s názvem `Items` obsahující <xref:System.Windows.Controls.ItemCollection>a že <xref:System.Windows.Controls.ItemCollection> je inicializován, ale prázdný, když <xref:System.Windows.Controls.ListBox> zpracování XAML. Potom každý podřízený objekt element, který existuje jako obsah pro <xref:System.Windows.Controls.ListBox> je přidán do <xref:System.Windows.Controls.ItemCollection> voláním analyzátor `ItemCollection.Add`. Tady je příklad zpracování XAML do stromu k objektu je dosavadní zdánlivě příklad kde stromu vytvořený objekt je v podstatě logickém stromu.  
  
 Logického stromu však není grafu celý objekt, který pro aplikace, které se promítnou uživatelského rozhraní v době běhu, i s položkami implicitní syntaxe XAML se existuje. Hlavním důvodem je vizuály a šablony. Představte si třeba <xref:System.Windows.Controls.Button>. Logickém stromu sestavy <xref:System.Windows.Controls.Button> objekt a taky její řetězec `Content`. Ale existuje další na toto tlačítko ve stromové struktuře běhového objektu. Konkrétně na tlačítko se zobrazí pouze na obrazovce způsobem používaným protože konkrétní <xref:System.Windows.Controls.Button> byla použita šablona ovládacího prvku. Vizuální prvky, které pocházejí z použité šablony (například definované šablony <xref:System.Windows.Controls.Border> tmavý šedé kolem visual tlačítka) nejsou hlášené v logickém stromu, i když hledáte v logickém stromu. při běhu (například zpracovává vstupní událost z viditelné uživatelského rozhraní a pak se čte logického stromu). Najít vizuální prvky šablony, místo toho potřebovali byste prozkoumat vizuálním stromu.  
  
 Další informace o tom, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe mapuje vytvořený objekt grafu a implicitní syntaxe v jazyce XAML, najdete v části [XAML syntaxe v podrobností](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) nebo [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="tree_property_inheritance_event_routing"></a>   
### <a name="the-purpose-of-the-logical-tree"></a>Účelem logickém stromu.  
 Logického stromu existuje, tak, aby obsahu modely můžete snadno iterace v jejich možné podřízené objekty a tak, aby modely obsahu může být extensible. Navíc logickém stromu. poskytuje rozhraní pro určité oznámení, například když jsou načteny všechny objekty v logickém stromu. V podstatě logického stromu je sblížení graf běhu objekt na úrovni framework, který vyloučí vizuální prvky, ale je dostačující pro mnoho dotazování operace proti složení vlastní běhu aplikace.  
  
 Kromě toho se vyřeší hledání směrem nahoru v logickém stromu pro oba odkazy statické a dynamické prostředků <xref:System.Windows.FrameworkElement.Resources%2A> kolekce na počáteční žádajícího objektu a poté pokračovat nahoru k logické a zkontrolujete jednotlivé <xref:System.Windows.FrameworkElement> (nebo <xref:System.Windows.FrameworkContentElement>) pro jinou `Resources` hodnotu, která obsahuje <xref:System.Windows.ResourceDictionary>, případně obsahující klíči. Logickém stromu. slouží k vyhledávání prostředků, pokud existuje logického stromu a vizuálním stromu. Další informace o slovnících prostředků a vyhledávání naleznete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
<a name="composition"></a>   
### <a name="composition-of-the-logical-tree"></a>Složení logickém stromu.  
 Logickém stromu. je definovaný na WPF framework úrovni, což znamená, že WPF základní elementu, který je nejdůležitější pro operace logickém stromu. je buď <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Ale, jako je uvidí Pokud skutečně používáte <xref:System.Windows.LogicalTreeHelper> rozhraní API, logickém stromu. někdy obsahuje uzly, které nejsou buď <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Pro instanci logického stromu sestavy <xref:System.Windows.Controls.TextBlock.Text%2A> hodnotu <xref:System.Windows.Controls.TextBlock>, což je řetězec.  
  
<a name="override_logical_tree"></a>   
### <a name="overriding-the-logical-tree"></a>Přepsání logickém stromu.  
 Řízení rozšířené autorům můžete přepsat logického stromu pomocí přepsání několik [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] které definují, jak obecné objekt nebo model obsahu přidá nebo odebere objekty v logickém stromu. Příklad postupu přepsání logického stromu, naleznete v části [přepsat logického stromu](../../../../docs/framework/wpf/advanced/how-to-override-the-logical-tree.md).  
  
<a name="pvi"></a>   
### <a name="property-value-inheritance"></a>Dědičnost hodnoty vlastnosti  
 Dědičnost vlastnosti hodnotu funguje prostřednictvím hybridní stromu. Skutečné metadata, která obsahuje <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> vlastnost, která umožňuje dědičnost vlastnosti je WPF úrovni rozhraní <xref:System.Windows.FrameworkPropertyMetadata> třídy. Proto nadřazeného objektu, který obsahuje původní hodnotu a podřízený objekt, který dědí tato hodnota musí být <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, a musí oba být součástí některých logickém stromu. Pro existující grafického subsystému WPF vlastnosti, které podporují dědičnost vlastnosti, je však možné perpetuate prostřednictvím použité objekt, který není v logickém stromu dědičnosti hodnotu vlastnosti. Hlavně to je důležité pro s prvky šablonu použít libovolné hodnoty zděděnou vlastnost, nastavte buď u instance, který je podle šablony, nebo na úrovni stránky složení stále vyšší úrovně a proto vyšší v logickém stromu. Aby dědičnost hodnotu vlastnosti konzistentně fungovat na všech těchto hranici vlastnost dědičných musí být registrován jako přidružená vlastnost a tento vzor byste měli postupovat, pokud chcete definovat vlastní závislosti vlastnost s vlastností dědičnost chování. Přesný stromu používá pro dědičnost vlastnosti nemůže být očekává zcela metody nástrojů pomocná třída, i v době běhu. Další informace najdete v tématu [dědičnost hodnotu vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
<a name="two_trees"></a>   
## <a name="the-visual-tree"></a>Vizuálním stromu  
 Kromě konceptu logického stromu, k dispozici je také koncepci visual tree v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Vizuální strojové struktuře popisuje strukturu vizuální objekty reprezentovaná <xref:System.Windows.Media.Visual> základní třídy. Když píšete šablonu pro ovládací prvek, je definování nebo opětovná definice visual stromové struktury, která platí pro ovládací prvek. Vizuální strojové struktuře je také zajímat vývojáře, kteří mají nižší úrovně kontrolu nad kreslení z důvodů výkonu a optimalizace. Jeden úniku vizuálním stromu jako součást konvenční [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování aplikací je, že událost trasy pro směrované události nejčastěji cestují podél vizuálním stromu, není logickém stromu. Tento subtlety chování směrované události nemusí být hned zjevné, pokud si nejste autora ovládacího prvku. Ovládací prvky, které implementují složení visual úrovni zpracování událostí nebo vytvořit událost setter směrování události prostřednictvím vizuální strojové struktuře umožní.  
  
<a name="trees_content"></a>   
## <a name="trees-content-elements-and-content-hosts"></a>Stromy, prvků obsahu a obsahu hostitele  
 Obsahu elementy (třídy, které jsou odvozeny od <xref:System.Windows.ContentElement>) nejsou součástí vizuálním stromu; nedědí z <xref:System.Windows.Media.Visual> a nemají vizuální reprezentace. Chcete-li zobrazit v uživatelském rozhraní na všech <xref:System.Windows.ContentElement> musí být hostované v hostiteli obsahu, který je i <xref:System.Windows.Media.Visual> a účastník logickém stromu. Obvykle je takového objektu <xref:System.Windows.FrameworkElement>. Můžete conceptualize, že hostitel obsahu je něco jako "prohlížeče" pro obsah a vybere způsob zobrazení tohoto obsahu v rámci oblasti obrazovky, který řídí hostitele. Pokud je zároveň hostitelem obsahu, můžete obsah se účastnit některé stromu procesy, které obvykle souvisejí s vizuálním stromu. Obecně platí <xref:System.Windows.FrameworkElement> třída hostitele zahrnuje implementace kód, který přidá všechny hostované <xref:System.Windows.ContentElement> trasu událostí prostřednictvím podřízených uzlů obsahu logického stromu, i když hostované obsah není součástí true vizuálním stromu. To je nezbytné, aby <xref:System.Windows.ContentElement> zdrojem může být směrované události, který směruje na libovolný element, než na sebe.  
  
<a name="tree_traversal"></a>   
## <a name="tree-traversal"></a>Traversal stromu  
 <xref:System.Windows.LogicalTreeHelper> Třída poskytuje <xref:System.Windows.LogicalTreeHelper.GetChildren%2A>, <xref:System.Windows.LogicalTreeHelper.GetParent%2A>, a <xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A> metody pro traversal logickém stromu. Ve většině případů by neměl máte procházení logického stromu existujících ovládacích prvků, protože tyto ovládací prvky téměř vždy vystavit jejich logické podřízených elementů v vlastnosti vyhrazené kolekce, která podporuje přístup kolekce, jako `Add`, indexeru, a tak dále. Především scénáře, který se používá autory řízení, kteří se rozhodnou není odvozena od vzory určený ovládacích prvků, jako je stromu traversal <xref:System.Windows.Controls.ItemsControl> nebo <xref:System.Windows.Controls.Panel> kde jsou již definováni vlastnosti kolekce a který chcete zadat své vlastní kolekce Podpora vlastnost.  
  
 Vizuální strojové struktuře také podporuje pomocná třída pro vizuálním stromu traversal <xref:System.Windows.Media.VisualTreeHelper>. Vizuální strojové struktuře nebude vystavena, jako pohodlně prostřednictvím vlastnosti specifické pro ovládací prvek, proto <xref:System.Windows.Media.VisualTreeHelper> třída je doporučeným způsobem, jak je v případě potřeby pro váš scénář programovací procházení vizuálním stromu. Další informace najdete v tématu [vykreslování přehled grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
> [!NOTE]
>  V některých případech je potřeba zkontrolovat vizuálním stromu použité šablony. Byste měli být opatrní při použití této techniky. I když jsou procházení vizuálním stromu ovládacího prvku, kde můžete definovat šablony, příjemci ovládacího prvku můžete kdykoli změnit šablonu nastavením <xref:System.Windows.Controls.Control.Template%2A> vlastnost instancí a i koncoví uživatelé mohou mít vliv na šabloně použité změnou motiv systému.  
  
<a name="routes"></a>   
## <a name="routes-for-routed-events-as-a-tree"></a>Trasy pro směrované události jako "Stromu"  
 Jak je uvedeno nahoře, trasa jakékoli dané směrované události přenáší podél jedné a předem určený cesty stromu, který je hybridní reprezentace visual a logické stromu. Událost trasy, která mohou projít buď v nahoru nebo dolů pokynů v rámci stromu v závislosti na tom, jestli je tunelové propojení nebo jejich směrované události. Koncept trasy událostí nemá přímo podpůrné pomocná třída, která by bylo možné "vás" události trasy nezávisle na vyvolá událost, která ve skutečnosti tras. Je třída, která představuje trasy, <xref:System.Windows.EventRoute>, ale metody této třídy jsou obecně jen pro interní použití.  
  
<a name="resourcesandtrees"></a>   
## <a name="resource-dictionaries-and-trees"></a>Slovnících prostředků a stromů  
 Vyhledávání prostředků slovník pro všechny `Resources` definované na stránce prochází v podstatě logickém stromu. Objekty, které nejsou v logickém stromu může odkazovat na prostředky s klíčem, ale pořadí vyhledávání prostředků začíná v okamžiku, kterých je tento objekt připojený k logickém stromu. V grafickém subsystému WPF, může mít pouze uzly logického stromu `Resources` vlastnost, která obsahuje <xref:System.Windows.ResourceDictionary>, proto nepřináší žádný užitek ve vizuálním stromu hledá s klíčem prostředky z procházení <xref:System.Windows.ResourceDictionary>.  
  
 Vyhledávání prostředků můžete také rozšířit nad rámec okamžitou logickém stromu. Pro kód aplikace vyhledávání prostředků můžete pokračujte dále slovnících prostředků na úrovni aplikace a klikněte na motiv podporu a systému hodnoty, které je odkazováno jako statické vlastnosti nebo klíče. Motivy, sami můžete také odkazu hodnoty systému mimo logického stromu motiv, pokud odkazy prostředků musí být dynamické. Další informace o slovnících prostředků a logiku vyhledávání, najdete v části [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Inicializace elementů objektu, které nejsou ve stromu objektů](../../../../docs/framework/wpf/advanced/initialization-for-object-elements-not-in-an-object-tree.md)  
 [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
