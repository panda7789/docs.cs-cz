---
title: Stromy
ms.date: 03/30/2017
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
ms.openlocfilehash: aed4350f1a7084b7894a70ac9d6d00cf25b39e34
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646202"
---
# <a name="trees-in-wpf"></a>Stromy v subsystému WPF
V mnoha technologiích jsou prvky a součásti uspořádány do stromové struktury, kde vývojáři přímo manipulují s uzly objektů ve stromu, aby ovlivnili vykreslování nebo chování aplikace. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]používá také několik metafor stromové struktury k definování vztahů mezi prvky programu. Z větší části WPF vývojáři můžete vytvořit aplikaci v kódu nebo definovat části aplikace v XAML při přemýšlení koncepčně o metaforu stromu objektů, ale bude volat konkrétní rozhraní API nebo pomocí konkrétní značky, aby tak učinily, spíše než některé obecné objektstrom manipulace rozhraní API, jako je například můžete použít v XML DOM. WPF zpřístupňuje dvě pomocné třídy, <xref:System.Windows.LogicalTreeHelper> <xref:System.Windows.Media.VisualTreeHelper>které poskytují strom metaforické zobrazení a . Termíny vizuální strom a logický strom se také používají v dokumentaci WPF, protože tyto stejné stromy jsou užitečné pro pochopení chování některých klíčových funkcí WPF. Toto téma definuje, co vizuální strom a logický strom představují, popisuje, jak tyto <xref:System.Windows.LogicalTreeHelper> <xref:System.Windows.Media.VisualTreeHelper>stromy souvisejí s celkovým konceptem stromu objektů, a zavádí a s.  

<a name="element_tree"></a>
## <a name="trees-in-wpf"></a>Stromy v subsystému WPF  
 Nejúplnější stromová [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] struktura v je strom objektu. Pokud definujete stránku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikace a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]pak načtete stromovou strukturu na základě vztahů vnoření prvků ve značkách. Pokud definujete aplikaci nebo část aplikace v kódu, vytvoří se stromová struktura na základě způsobu přiřazení hodnot vlastností pro vlastnosti, které implementují model obsahu pro daný objekt. V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]aplikaci existují dva způsoby, jak je celý strom objektů konceptualizován a může být vykázán do jeho veřejného rozhraní API: jako logický strom a jako vizuální strom. Rozdíly mezi logickým stromem a vizuálním stromem nejsou vždy nutně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] důležité, ale mohou občas způsobit problémy s určitými subsystémy a ovlivnit volby, které provedete ve značkách nebo kódu.  
  
 I když ne vždy manipulovat buď logický strom nebo vizuální strom přímo, pochopení pojmy, jak se stromy vzájemně ovlivňují, je užitečné pro pochopení WPF jako technologie. Myšlení WPF jako strom metafora nějakého druhu je také důležité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pochopit, jak dědičnost vlastností a směrování událostí práce v .  
  
> [!NOTE]
> Vzhledem k tomu, že strom objektů je spíše koncept než skutečné rozhraní API, jiný způsob, jak si tento koncept myslet, je jako objektový graf. V praxi existují vztahy mezi objekty v době běhu, kdy se metafora stromu rozpadne. Nicméně, zejména s XAML definované uživatelské ho, metafora stromu je natolik relevantní, že většina WPF dokumentace bude používat termín stromu objektů při odkazování na tento obecný koncept.  
  
<a name="logical_tree"></a>
## <a name="the-logical-tree"></a>Logický strom  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikace můžete přidat obsah do prvků uživatelského rozhraní nastavením vlastností objektů, které tyto prvky zpět. Například přidáte položky <xref:System.Windows.Controls.ListBox> do ovládacího <xref:System.Windows.Controls.ItemsControl.Items%2A> prvku manipulací s jeho vlastností. Tímto způsobem umisťujete položky do hodnoty, <xref:System.Windows.Controls.ItemCollection> která je vlastnost. <xref:System.Windows.Controls.ItemsControl.Items%2A> Podobně chcete-li přidat <xref:System.Windows.Controls.DockPanel>objekty do <xref:System.Windows.Controls.Panel.Children%2A> , manipulovat s jeho hodnotu vlastnosti. Zde přidáváte objekty <xref:System.Windows.Controls.UIElementCollection>do . Příklad kódu najdete v [tématu Jak: Dynamicky přidat element](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms752374(v=vs.100)).  
  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], když umístíte <xref:System.Windows.Controls.ListBox> položky seznamu v nebo <xref:System.Windows.Controls.DockPanel>ovládací prvky <xref:System.Windows.Controls.ItemsControl.Items%2A> nebo <xref:System.Windows.Controls.Panel.Children%2A> jiné prvky uživatelského rozhraní v , můžete také použít vlastnosti a, explicitně nebo implicitně, jako v následujícím příkladu.  
  
 [!code-xaml[TreeOvwsSupport#AllCode](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 Pokud byste měli zpracovat tento XAML jako XML v rámci objektového modelu dokumentu a pokud jste zahrnuli značky komentované jako implicitní (což by bylo legální), pak by výsledný strom XML DOM zahrnoval prvky pro `<ListBox.Items>` a další implicitní položky. Ale XAML nezpracovává tímto způsobem při čtení značek a zápisu do objektů, `ListBox.Items`výsledný objekt graf neobsahuje doslova . Má však <xref:System.Windows.Controls.ListBox> vlastnost `Items` s názvem <xref:System.Windows.Controls.ItemCollection>, <xref:System.Windows.Controls.ItemCollection> která obsahuje , a <xref:System.Windows.Controls.ListBox> která je inicializována, ale prázdná při zpracování XAML. Potom každý podřízený prvek objektu, <xref:System.Windows.Controls.ListBox> který existuje <xref:System.Windows.Controls.ItemCollection> jako obsah pro `ItemCollection.Add`je přidán do podle analyzátoru volání . Tento příklad zpracování XAML do stromu objektů je zatím zdánlivě příklad, kde je strom vytvořených objektů v podstatě logický strom.  
  
 Logický strom však není celý objekt grafu, který existuje pro uživatelské rozhraní aplikace za běhu, a to i s xAML implicitní syntaktické položky započítány. Hlavním důvodem jsou vizuály a šablony. Zvažte například <xref:System.Windows.Controls.Button>. Logický strom hlásí <xref:System.Windows.Controls.Button> objekt a `Content`také jeho řetězec . Ale je více k tomuto tlačítku ve stromu objektů run-time. Zejména tlačítko se zobrazí pouze na obrazovce tak, <xref:System.Windows.Controls.Button> jak to dělá, protože byla použita určitá šablona ovládacího prvku. Vizuály, které pocházejí z použité šablony <xref:System.Windows.Controls.Border> (například šablona definované tmavě šedé kolem vizuální tlačítko) nejsou hlášeny v logickém stromu, i když se díváte na logický strom za běhu (například zpracování vstupní události z viditelného uživatelského zařízení a potom čtení logického stromu). Chcete-li najít vizuály šablony, budete místo toho muset prozkoumat vizuální strom.  
  
 Další informace o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tom, jak syntaxe mapuje na vytvořený objektový graf a implicitní syntaxi v XAML, naleznete [v tématu Syntaxe XAML podrobně](xaml-syntax-in-detail.md) nebo [Přehled XAML (WPF).](../../../desktop-wpf/fundamentals/xaml.md)  
  
<a name="tree_property_inheritance_event_routing"></a>
### <a name="the-purpose-of-the-logical-tree"></a>Účel logického stromu  
 Logický strom existuje tak, aby modely obsahu můžete snadno iterate přes jejich možné podřízené objekty a tak, aby modely obsahu může být rozšiřitelné. Logický strom také poskytuje rámec pro určitá oznámení, například při načítání všech objektů v logickém stromu. V podstatě logický strom je aproximace grafu objektu za běhu na úrovni rozhraní, která vylučuje vizuály, ale je vhodná pro mnoho dotazovacích operací proti složení vlastní aplikace běhu.  
  
 Kromě toho statické a dynamické odkazy na prostředky jsou vyřešeny <xref:System.Windows.FrameworkElement.Resources%2A> pohledem nahoru prostřednictvím logického stromu pro kolekce na počáteční <xref:System.Windows.FrameworkElement> žádající objekt a potom pokračuje do logického stromu a kontrolu každý (nebo <xref:System.Windows.FrameworkContentElement>) pro jinou `Resources` <xref:System.Windows.ResourceDictionary>hodnotu, která obsahuje , případně obsahující tento klíč. Logický strom se používá pro vyhledávání prostředků, pokud jsou k dispozici logický strom i vizuální strom. Další informace o slovníky prostředků a vyhledávání naleznete v tématu [XAML resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
<a name="composition"></a>
### <a name="composition-of-the-logical-tree"></a>Složení logického stromu  
 Logický strom je definován na úrovni rámce WPF, což znamená, že základní prvek WPF, který je nejdůležitější pro operace logického stromu, je buď <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Však jak můžete zjistit, pokud <xref:System.Windows.LogicalTreeHelper> skutečně použít rozhraní API, logický strom <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>někdy obsahuje uzly, které nejsou buď nebo . Například logický strom hlásí <xref:System.Windows.Controls.TextBlock.Text%2A> hodnotu <xref:System.Windows.Controls.TextBlock>, což je řetězec.  
  
<a name="override_logical_tree"></a>
### <a name="overriding-the-logical-tree"></a>Přepsání logického stromu  
 Pokročilí autoři ovládacího prvku mohou přepsat logický strom přepsáním několika api, která definují, jak obecný model objektu nebo obsahu přidává nebo odebere objekty v logickém stromu. Příklad, jak přepsat logický strom, naleznete [v tématu Přepsat logický strom](how-to-override-the-logical-tree.md).  
  
<a name="pvi"></a>
### <a name="property-value-inheritance"></a>Dědičnost hodnoty vlastnosti  
 Dědičnost hodnoty vlastnosti pracuje prostřednictvím hybridního stromu. Skutečná metadata, která <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> obsahuje vlastnost, která umožňuje dědičnost <xref:System.Windows.FrameworkPropertyMetadata> vlastností, je třída wpf na úrovni architektury. Proto nadřazený objekt, který obsahuje původní hodnotu, a <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>podřízený objekt, který tuto hodnotu dědí, musí být nebo , a musí být oba součástí některého logického stromu. Však pro existující WPF vlastnosti, které podporují dědičnost vlastností, dědičnost hodnoty vlastnosti je schopen udržovat prostřednictvím zasahující objekt, který není v logickém stromu. Hlavně je to důležité pro to, aby prvky šablony používaly všechny zděděné hodnoty vlastností nastavené buď v instanci, která je šablonována, nebo na ještě vyšších úrovních složení na úrovni stránky a proto vyšší v logickém stromu. Aby dědičnost hodnoty vlastnosti fungovala konzistentně přes takovou hranici, musí být děťující vlastnost registrována jako připojená vlastnost a tento vzor byste měli dodržovat, pokud máte v úmyslu definovat vlastní vlastnost závislosti s chováním dědičnosti vlastností. Přesný strom používaný pro dědičnost vlastností nelze zcela předvídat pomocí metody pomocné třídy, a to ani za běhu. Další informace naleznete v [tématu Dědičnost hodnoty nemovitosti](property-value-inheritance.md).  
  
<a name="two_trees"></a>
## <a name="the-visual-tree"></a>Vizuální strom  
 Kromě konceptu logického stromu je zde také koncept vizuálního stromu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Vizuální strom popisuje strukturu vizuálních objektů, jak <xref:System.Windows.Media.Visual> je znázorněno základní třídou. Při psaní šablony pro ovládací prvek definujete nebo předefinujete vizuální strom, který platí pro tento ovládací prvek. Vizuální strom je také zajímavý pro vývojáře, kteří chtějí nižší úroveň kontroly nad kreslením z důvodů výkonu a optimalizace. Jedna expozice vizuálního stromu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako součást konvenčního aplikačního programování je, že trasy událostí pro směrovanou událost většinou cestují podél vizuálního stromu, nikoli logického stromu. Tato jemnost směrované události chování nemusí být okamžitě zřejmé, pokud jste autor ovládacího prvku. Směrování událostí prostřednictvím vizuálního stromu umožňuje ovládací prvky, které implementují složení na vizuální úrovni pro zpracování událostí nebo vytváření setterů událostí.  
  
<a name="trees_content"></a>
## <a name="trees-content-elements-and-content-hosts"></a>Stromy, prvky obsahu a hostitelé obsahu  
 Elementy obsahu (třídy, které jsou odvozeny z <xref:System.Windows.ContentElement>) nejsou součástí vizuálního stromu; nedědí a <xref:System.Windows.Media.Visual> nemají vizuální reprezentaci. Aby se mohl zobrazit v unovém <xref:System.Windows.ContentElement> unovém umíte vůbec, <xref:System.Windows.Media.Visual> musí být hostován v hostiteli obsahu, který je účastníkem logického stromu. Obvykle takový objekt <xref:System.Windows.FrameworkElement>je . Můžete konceptualizovat, že hostitel obsahu je poněkud jako "prohlížeč" pro obsah a zvolí způsob zobrazení tohoto obsahu v oblasti obrazovky, kterou hostitel ovládá. Když je obsah hostován, obsah může být účastníkem určitých procesů stromu, které jsou obvykle přidruženy k vizuálnímu stromu. Obecně <xref:System.Windows.FrameworkElement> hostitelská třída obsahuje kód implementace, <xref:System.Windows.ContentElement> který přidá všechny hostované do trasy události prostřednictvím poduzlů logického stromu obsahu, i když hostovaný obsah není součástí skutečného vizuálního stromu. To je nezbytné, <xref:System.Windows.ContentElement> aby může zdroj směrované události, která směruje na jakýkoli prvek než sám.  
  
<a name="tree_traversal"></a>
## <a name="tree-traversal"></a>Stromový průchod  
 Třída <xref:System.Windows.LogicalTreeHelper> poskytuje <xref:System.Windows.LogicalTreeHelper.GetChildren%2A>, <xref:System.Windows.LogicalTreeHelper.GetParent%2A>a <xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A> metody pro průchod logického stromu. Ve většině případů byste neměli procházet logický strom existujících ovládacích prvků, protože tyto ovládací prvky téměř vždy `Add`zveřejňují jejich logické podřízené prvky jako vyhrazenou vlastnost kolekce, která podporuje přístup ke kolekci, jako je indexer a tak dále. Strom průchodje je hlavně scénář, který se používá autoři ovládacího prvku, <xref:System.Windows.Controls.ItemsControl> kteří <xref:System.Windows.Controls.Panel> se rozhodnou neodvodit z zamýšlené ho řízení vzory, jako jsou nebo kde vlastnosti kolekce jsou již definovány a kteří mají v úmyslu poskytnout vlastní podporu vlastností kolekce.  
  
 Vizuální strom také podporuje pomocnou třídu pro <xref:System.Windows.Media.VisualTreeHelper>průchozí vizuální strom . Vizuální strom není vystavena jako pohodlně prostřednictvím vlastnosti specifické pro ovládací prvek, takže <xref:System.Windows.Media.VisualTreeHelper> třída je doporučený způsob, jak procházet vizuální strom, pokud je to nezbytné pro váš scénář programování. Další informace naleznete v [tématu Přehled vykreslení grafiky WPF](../graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
> [!NOTE]
> Někdy je nutné prozkoumat vizuální strom aplikované šablony. Při použití této techniky byste měli být opatrní. I v případě, že procházíte vizuálním stromem pro ovládací prvek, kde definujete <xref:System.Windows.Controls.Control.Template%2A> šablonu, mohou spotřebitelé ovládacího prvku vždy změnit šablonu nastavením vlastnosti na instance a dokonce i koncový uživatel může ovlivnit použitou šablonu změnou motivu systému.  
  
<a name="routes"></a>
## <a name="routes-for-routed-events-as-a-tree"></a>Trasy pro směrované události jako "strom"  
 Jak již bylo zmíněno dříve, trasa dané směrované události cestuje po jedné a předem určené cestě stromu, který je hybridem reprezentací vizuálního a logického stromu. Trasa události může cestovat ve směru nahoru nebo dolů ve stromu v závislosti na tom, zda se jedná o trasování tunelového propojení nebo probublávání směrované události. Koncept trasy události nemá přímou podpůrnou pomocnou třídu, která by mohla být použita k "procházce" trasy události nezávisle na vyvolání události, která se skutečně směruje. Je třída, která představuje <xref:System.Windows.EventRoute>trasu , ale metody této třídy jsou obecně pouze pro interní použití.  
  
<a name="resourcesandtrees"></a>
## <a name="resource-dictionaries-and-trees"></a>Slovníky zdrojů a stromy  
 Vyhledávání slovníku prostředků `Resources` pro všechny definované na stránce prochází v podstatě logický strom. Objekty, které nejsou v logickém stromu, mohou odkazovat na klíčové prostředky, ale pořadí vyhledávání prostředků začíná v místě, kde je tento objekt připojen k logickému stromu. V WPF pouze logické uzly `Resources` stromu <xref:System.Windows.ResourceDictionary>může mít vlastnost, která obsahuje , proto není žádný <xref:System.Windows.ResourceDictionary>přínos při procházení vizuální strom hledá keyed prostředky z .  
  
 Vyhledávání prostředků však může také přesahovat okamžité logické ho stromu. Pro značky aplikace může vyhledávání prostředků pokračovat dále do slovníků prostředků na úrovni aplikace a potom na podporu motivu a systémové hodnoty, které jsou odkazovány jako statické vlastnosti nebo klíče. Motivy samy o sobě mohou také odkazovat na systémové hodnoty mimo logický strom motivu, pokud jsou odkazy na prostředky dynamické. Další informace o slovníky prostředků a logiku vyhledávání naleznete v tématu [XAML resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled vstupu](input-overview.md)
- [Přehled vykreslování grafiky WPF](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Inicializace elementů objektu, které nejsou obsaženy ve stromu objektů](initialization-for-object-elements-not-in-an-object-tree.md)
- [Architektura WPF](wpf-architecture.md)
