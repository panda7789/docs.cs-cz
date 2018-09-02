---
title: Přehled řízeného vytváření
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
ms.openlocfilehash: ca11a5787dfd3e5f3089d44689d96ec64c75e4f3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394065"
---
# <a name="control-authoring-overview"></a>Přehled řízeného vytváření
Rozšiřitelnost [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] model řízení výrazně snižuje potřebu vytvářet nový ovládací prvek. Ale v některých případech budete stále muset vytvořit vlastní ovládací prvek. Toto téma popisuje funkce, které minimalizují potřeba k vytvoření vlastního ovládacího prvku a jiného ovládacího prvku pro vytváření modelů v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Toto téma ukazuje, jak vytvořit nový ovládací prvek.  
  
 
  
<a name="when_to_write_a_new_control"></a>   
## <a name="alternatives-to-writing-a-new-control"></a>Alternativy k zápisu nového ovládacího prvku  
 V minulosti Pokud chcete získat vlastní zkušenosti z existujícího ovládacího prvku, jste byli omezeni na měnící se standardní vlastnosti ovládacího prvku, jako je například velikost písma, barvu pozadí a šířku ohraničení. Pokud jste si přáli rozšířit vzhled a chování ovládacího prvku nad rámec těchto předdefinovaných parametrů, musíte vytvořit nový ovládací prvek, obvykle dědění z existujícího ovládacího prvku a přepsání metody, které jsou zodpovědné za vykreslování ovládacího prvku.  I když se pořád možnost, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vám umožňuje přizpůsobit existující ovládací prvky s využitím bohaté obsahu modelu, styly, šablony a aktivačních událostí. Následující seznam obsahuje příklady, jak tyto funkce lze vytvořit vlastní a konzistentní prostředí bez nutnosti vytvářet nový ovládací prvek.  
  
-   **Formátovaný obsah.** Mnoho standardních [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky podporují formátovaný obsah. Například vlastnost content <xref:System.Windows.Controls.Button> je typu <xref:System.Object>, takže teoreticky cokoliv mohou být zobrazeny na <xref:System.Windows.Controls.Button>.  Pokud chcete, aby tlačítko Zobrazit image a text, můžete přidat bitovou kopii a <xref:System.Windows.Controls.TextBlock> k <xref:System.Windows.Controls.StackPanel> a přiřadit <xref:System.Windows.Controls.StackPanel> k <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost. Protože ovládacích prvků můžete zobrazit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vizuálních prvků a libovolná data, méně nutné k vytvoření nového ovládacího prvku nebo pro úpravu existujícího ovládacího prvku pro podporu složité vizualizace. Další informace o obsahu modelu pro <xref:System.Windows.Controls.Button> a další obsah modely v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], naleznete v tématu [Model obsahu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
-   **Styly.** A <xref:System.Windows.Style> je kolekce hodnot, které představují vlastnosti ovládacího prvku. Pomocí stylů můžete vytvořit opakovaně použitelné reprezentace požadovaný vzhled a chování aniž byste museli napsat nový ovládací prvek. Předpokládejme například, že chcete všechny vaše <xref:System.Windows.Controls.TextBlock> ovládacích prvků na červený, Arial písmo s velikostí písma 14. Můžete vytvořit styl jako prostředek a odpovídajícím způsobem nastavit příslušné vlastnosti. Pak každý <xref:System.Windows.Controls.TextBlock> přidat do vaší aplikace bude mít stejný vzhled.  
  
-   **Datové šablony.** A <xref:System.Windows.DataTemplate> umožňuje přizpůsobit způsob zobrazení dat v ovládacím prvku. Například <xref:System.Windows.DataTemplate> lze určit způsob zobrazení dat <xref:System.Windows.Controls.ListBox>.  Příkladem, naleznete v tématu [přehled datových šablon](../../../../docs/framework/wpf/data/data-templating-overview.md).  Kromě přizpůsobení vzhledu dat, <xref:System.Windows.DataTemplate> může obsahovat prvky uživatelského rozhraní, které vám přináší značnou flexibilitu ve vlastní uživatelská rozhraní.  Například pomocí <xref:System.Windows.DataTemplate>, můžete vytvořit <xref:System.Windows.Controls.ComboBox> v kterou každá položka obsahuje zaškrtávací políčko.  
  
-   **Šablony ovládacích prvků.** Mnoho ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použít <xref:System.Windows.Controls.ControlTemplate> definovat strukturu a vzhled, který odděluje vzhledu ovládacího prvku z funkce ovládací prvek ovládacího prvku. Vzhled ovládacího prvku může výrazně změnit předefinováním jeho <xref:System.Windows.Controls.ControlTemplate>.  Předpokládejme například, že chcete ovládací prvek, který bude vypadat jako semafor. Tento ovládací prvek má jednoduché uživatelské rozhraní a funkce.  Ovládací prvek je tři kruhy pouze jeden z nich můžete lit po jednom. Po nějaké reflexe mohou Pamatujte, že <xref:System.Windows.Controls.RadioButton> nabízí funkce pouze jednoho výběru v době, ale výchozí vzhled <xref:System.Windows.Controls.RadioButton> nic vypadá světla na semafor.  Protože <xref:System.Windows.Controls.RadioButton> používá šablonu ovládacího prvku k definování jeho vzhled, snadno znovu definovat <xref:System.Windows.Controls.ControlTemplate> odpovídal požadavkům ovládacího prvku a používejte přepínačů, aby vaše semafor.  
  
    > [!NOTE]
    >  I když <xref:System.Windows.Controls.RadioButton> můžete použít <xref:System.Windows.DataTemplate>, <xref:System.Windows.DataTemplate> nestačí v tomto příkladu.  <xref:System.Windows.DataTemplate> Definuje vzhled elementů obsahu ovládacího prvku. V případě třídy <xref:System.Windows.Controls.RadioButton>, obsah je cokoli, co se zobrazí napravo od kruhu, která určuje, zda <xref:System.Windows.Controls.RadioButton> je vybrána.  V tomto příkladu semafor přepínač musí být pouze kruh, který může "rozsvítit." Protože vzhled požadavek semafor se tak liší od výchozí vzhled <xref:System.Windows.Controls.RadioButton>, je nezbytné k předefinování <xref:System.Windows.Controls.ControlTemplate>.  Obecně platí <xref:System.Windows.DataTemplate> slouží k definování obsah (nebo dat) z ovládacího prvku a s <xref:System.Windows.Controls.ControlTemplate> slouží k definování struktury ovládacího prvku.  
  
-   **Aktivační události.** A <xref:System.Windows.Trigger> vám umožní dynamicky změnit vzhled a chování ovládacího prvku bez vytvoření nového ovládacího prvku. Předpokládejme například, že máte více <xref:System.Windows.Controls.ListBox> ovládacích prvků ve vaší aplikaci a chcete položky v každém <xref:System.Windows.Controls.ListBox> být tučné a červenou, když je tato možnost vybrána. Může být první instinct vytvořit třídu, která dědí z <xref:System.Windows.Controls.ListBox> a přepsat <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> metodou Změna vzhledu vybrané položky, ale lepším řešením je přidání triggeru pro styl <xref:System.Windows.Controls.ListBoxItem> , který změní vzhled vybrané položky. Aktivační událost můžete změnit hodnoty vlastností nebo provádět akce na základě hodnoty vlastnosti. <xref:System.Windows.EventTrigger> Umožňuje provádět akce, když dojde k události.  
  
 Další informace o styly, šablony a aktivačních událostech najdete v tématu [styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Obecně platí Pokud váš ovládací prvek zrcadlí funkce existujícího ovládacího prvku, ale chcete ovládací prvek vypadat jinak, byste měli nejprve zvážit, jestli můžete některou z metod popsaných v této části můžete změnit pomocí existujícího ovládacího prvku vzhled.  
  
<a name="models_for_control_authoring"></a>   
## <a name="models-for-control-authoring"></a>Modely pro vytváření ovládacího prvku  
 Bohaté obsahu modelu, styly, šablony a aktivační události minimalizovat potřebu vytvářet nový ovládací prvek. Ale pokud potřebujete vytvořit nový ovládací prvek, je důležité pochopit, jiný ovládací prvek pro vytváření modelů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí tři hlavní modely pro vytvoření ovládacího prvku, z nichž každý obsahuje odlišnou sadu funkcí a úroveň flexibility. Základní třídy pro všechny tři modely jsou <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control>, a <xref:System.Windows.FrameworkElement>.  
  
### <a name="deriving-from-usercontrol"></a>Odvozování z uživatelský ovládací prvek  
 Nejjednodušší způsob, jak vytvořit ovládací prvek v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je odvozena z <xref:System.Windows.Controls.UserControl>. Při vytváření ovládacího prvku, který dědí z <xref:System.Windows.Controls.UserControl>, přidat existující součásti <xref:System.Windows.Controls.UserControl>, název komponenty a odkazovat na obslužné rutiny událostí v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Potom můžete odkazovat na pojmenované elementy a definování obslužných rutin událostí v kódu. Tento model vývoje je velmi podobný modelu používá při vývoji aplikací v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Pokud vytvořen správně, <xref:System.Windows.Controls.UserControl> můžete využít výhod formátovaného obsahu, styly a aktivačních událostí. Ale pokud váš ovládací prvek dědí z <xref:System.Windows.Controls.UserControl>, uživatelé, kteří používají ovládací prvek nebude možné použít <xref:System.Windows.DataTemplate> nebo <xref:System.Windows.Controls.ControlTemplate> přizpůsobit její vzhled.  Je nutné odvozovat <xref:System.Windows.Controls.Control> třídy nebo některé z odvozených tříd (jiné než <xref:System.Windows.Controls.UserControl>) Chcete-li vytvořit vlastní ovládací prvek, který podporuje šablony.  
  
#### <a name="benefits-of-deriving-from-usercontrol"></a>Výhody odvozený od uživatelský ovládací prvek  
 Vezměte v úvahu odvozený od <xref:System.Windows.Controls.UserControl> Pokud všechny z následujících akcí:  
  
-   Chcete sestavit ovládacího prvku podobně jako na tom, jak sestavit aplikaci.  
  
-   Ovládací prvek se skládá pouze z existující komponenty.  
  
-   Není nutné pro podporu komplexních přizpůsobení.  
  
### <a name="deriving-from-control"></a>Odvozování z ovládacího prvku  
 Odvozování z <xref:System.Windows.Controls.Control> třídy je model využívá většina existující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků. Při vytváření ovládacího prvku, který dědí z <xref:System.Windows.Controls.Control> třída, definují jeho vzhled pomocí šablon. Díky tomu můžete oddělit provozní logiky od bude obsahovat vizuální reprezentaci. Můžete také zajistit oddělení uživatelského rozhraní a logiky pomocí příkazů a vazby místo události a nejkonkrétnější – vyhněte odkazující prvky v <xref:System.Windows.Controls.ControlTemplate> kdykoli je to možné.  Pokud jsou správně oddělení uživatelského rozhraní a logiky ovládacího prvku, uživatelského ovládacího prvku lze znovu definovat ovládacího prvku <xref:System.Windows.Controls.ControlTemplate> přizpůsobit její vzhled. I když sestavování vlastních <xref:System.Windows.Controls.Control> není snadné – stačí vytváření <xref:System.Windows.Controls.UserControl>, vlastní <xref:System.Windows.Controls.Control> nabízí největší flexibilitu.  
  
#### <a name="benefits-of-deriving-from-control"></a>Výhody systému vyplývajících z ovládacího prvku  
 Vezměte v úvahu odvozený od <xref:System.Windows.Controls.Control> namísto použití <xref:System.Windows.Controls.UserControl> třídy, pokud je libovolná z následujících podmínek:  
  
-   Chcete vzhled ovládacího prvku, lze přizpůsobit prostřednictvím <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Chcete ovládací prvek podporovat různé motivy.  
  
### <a name="deriving-from-frameworkelement"></a>Odvozený od prvku FrameworkElement  
 Ovládací prvky, které jsou odvozeny z <xref:System.Windows.Controls.UserControl> nebo <xref:System.Windows.Controls.Control> spoléhat na vytváření stávající elementy. Pro většinu scénářů, toto je přijatelného řešení, protože libovolný objekt, který dědí z <xref:System.Windows.FrameworkElement> může být v <xref:System.Windows.Controls.ControlTemplate>. Existují však situace při vzhled ovládacího prvku vyžaduje více než funkce jednoduchý prvek složení. Pro tyto scénáře založenou na komponentu <xref:System.Windows.FrameworkElement> je tou správnou volbou.  
  
 Existují dvě standardní metody pro vytváření <xref:System.Windows.FrameworkElement>– na základě komponenty: přímé vykreslení a vlastní složení elementu. Přímé vykreslování zahrnuje přepsání <xref:System.Windows.UIElement.OnRender%2A> metoda <xref:System.Windows.FrameworkElement> a poskytování <xref:System.Windows.Media.DrawingContext> operace, které explicitně definovat součást vizuály. Toto je metoda, kterou používá <xref:System.Windows.Controls.Image> a <xref:System.Windows.Controls.Border>. Vlastní element složení zahrnuje použití objektů typu <xref:System.Windows.Media.Visual> sestavit vzhledu komponenty. Příklad najdete v tématu [použití objektů DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track> je příkladem ovládacího prvku v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , která používá vlastní element složení. Je také možné kombinovat s přímým přístupem vykreslování a vlastní element složení ve stejný ovládací prvek.  
  
#### <a name="benefits-of-deriving-from-frameworkelement"></a>Výhody odvozený od prvku FrameworkElement  
 Vezměte v úvahu odvozený od <xref:System.Windows.FrameworkElement> Pokud některý z následujících podmínek:  
  
-   Chcete mít přesnou kontrolu nad vzhled ovládacího prvku nad rámec poskytuje jednoduchý prvek složení.  
  
-   Můžete definovat vzhled ovládacího prvku tak, že definujete vlastní logiku pro vykreslení.  
  
-   Chcete sestavit nové způsoby, který jde nad rámec toho, jaké jsou možnosti s existující prvky <xref:System.Windows.Controls.UserControl> a <xref:System.Windows.Controls.Control>.  
  
<a name="control_authoring_basics"></a>   
## <a name="control-authoring-basics"></a>Základy vytváření ovládacího prvku  
 Jak je uvedeno výše, jednou z nejúčinnějších funkcí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je schopnost se dostat nad rámec nastavení základní vlastnosti chcete změnit její vzhled a chování ovládacího prvku, ale stále není by bylo potřeba vytvořit vlastní ovládací prvek. Styly, datové vazby a aktivační události funkcí je možné podle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém událostí. Následující části popisují některé postupy, které byste měli postupovat, bez ohledu na to, model použijete k vytvoření vlastního ovládacího prvku tak, aby uživatelé vlastního ovládacího prvku mohou používat tyto funkce stejně, jako kdyby je sdíleli pro ovládací prvek, který je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="use-dependency-properties"></a>Pomocí vlastnosti závislosti  
 Pokud vlastnost vlastnost závislosti, je možné provést následující kroky:  
  
-   Nastavte vlastnost ve stylu.  
  
-   Ke zdroji dat vytvořit vazbu vlastnost.  
  
-   Dynamický prostředek použijte jako hodnotu vlastnosti.  
  
-   Animujte vlastnost.  
  
 Pokud chcete vlastnost ovládacího prvku k podpoře jakýchkoli tuto funkci, je nutné jej implementovat jako vlastnost závislosti. Následující příklad definuje vlastnost závislosti s názvem `Value` následujícím způsobem:  
  
-   Definování <xref:System.Windows.DependencyProperty> identifikátor s názvem `ValueProperty` jako `public` `static` `readonly` pole.  
  
-   Zaregistrovat název vlastnosti v systému vlastností voláním <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>, zadat následující:  
  
    -   Název vlastnosti  
  
    -   Typ vlastnosti.  
  
    -   Typ, který vlastní vlastnost.  
  
    -   Metadata pro vlastnost. Výchozí hodnota vlastnosti, obsahuje metadata <xref:System.Windows.CoerceValueCallback> a <xref:System.Windows.PropertyChangedCallback>.  
  
-   Definování [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obálky vlastnost s názvem `Value`, což je stejný název, který se použije k registraci vlastnost závislosti implementací vlastnosti `get` a `set` přistupující objekty. Všimněte si, že `get` a `set` přistupující objekty volat pouze <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> v uvedeném pořadí. Doporučuje se, že přistupující objekty vlastnosti závislosti není obsahovat další logiku, protože klienti a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] může obejít přístupové objekty a volání <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> přímo. Například pokud je vlastnost navázána na datový zdroj, vlastnosti `set` přistupujícího objektu není volána.  Nepřidávat další logiku na GET a přístupové objekty set, použijte <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.CoerceValueCallback>, a <xref:System.Windows.PropertyChangedCallback> delegáty odpovídají nebo zkontrolujte hodnotu při změně.  Další informace o tato zpětná volání, naleznete v tématu [vlastnost závislosti zpětné volání a ověření](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
-   Definujte metodu <xref:System.Windows.CoerceValueCallback> s názvem `CoerceValue`. `CoerceValue` zajišťuje, že `Value` je větší nebo rovna hodnotě `MinValue` a menší než nebo rovno `MaxValue`.  
  
-   Definujte metodu <xref:System.Windows.PropertyChangedCallback>s názvem `OnValueChanged`. `OnValueChanged` vytvoří <xref:System.Windows.RoutedPropertyChangedEventArgs%601> objektu a připraví pro vyvolání `ValueChanged` směrované události. Směrované události jsou popsány v následující části.  
  
 [!code-csharp[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
 [!code-vb[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]  
  
 Další informace najdete v tématu [vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
### <a name="use-routed-events"></a>Použití směrovaných událostí  
 Stejně jako závislost vlastnosti rozšíření pojem [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnosti s dalšími funkcemi směrovaných událostí rozšířit pojem standard [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události. Když vytvoříte nový [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku, je také vhodné implementovat vaše událostí jako směrovaných událostí, protože směrované události podporuje následující chování:  
  
-   Události mohou být zpracovávány u nadřazené položky více ovládacích prvků. Pokud je událost šíření událostí, jedné nadřazené ve stromu elementů může přihlásit k odběru události. Autoři aplikace pak můžete použít jednu obslužnou rutinu reagovat na událost několik ovládacích prvků. Například, pokud váš ovládací prvek je součástí každé položky v <xref:System.Windows.Controls.ListBox> (protože je součástí <xref:System.Windows.DataTemplate>), vývojář aplikace definovat obslužnou rutinu události pro událost ovládacího prvku na <xref:System.Windows.Controls.ListBox>. Pokaždé, když dojde k události na žádném z ovládacích prvků, je volána obslužnou rutinu události.  
  
-   Směrované události lze použít v <xref:System.Windows.EventSetter>, která vývojářům aplikací umožňuje určit obslužné rutiny události v rámci style.  
  
-   Směrované události lze použít v <xref:System.Windows.EventTrigger>, což je užitečné pro animace vlastnosti pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Další informace najdete v tématu [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Následující příklad definuje směrované události následujícím způsobem:  
  
-   Definování <xref:System.Windows.RoutedEvent> identifikátor s názvem `ValueChangedEvent` jako `public` `static` `readonly` pole.  
  
-   Zaregistrujte směrované události ve volání <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> metody. Příklad určuje následující informace, když volá <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:  
  
    -   Je název události `ValueChanged`.  
  
    -   Strategie směrování je <xref:System.Windows.RoutingStrategy.Bubble>, což znamená, že je nejdříve volána obslužnou rutinu události ve zdroji (objekt, který vyvolává událost) a potom jsou volány obslužné rutiny události na zdroje na nadřazené elementy v daný okamžik, počínaje obslužné rutiny události na nejbližšímu Nadřazený element.  
  
    -   Typ obslužné rutiny události je <xref:System.Windows.RoutedPropertyChangedEventHandler%601>, vytvořený s <xref:System.Decimal> typu.  
  
    -   Vlastnící typ události je `NumericUpDown`.  
  
-   Veřejná událost s názvem deklarovat `ValueChanged` a obsahuje deklarace přístupového objektu události. Příklad volá <xref:System.Windows.UIElement.AddHandler%2A> v `add` deklarace přistupujícího objektu a <xref:System.Windows.UIElement.RemoveHandler%2A> v `remove` deklarace přistupujícího objektu používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostí služby.  
  
-   Vytvořit chráněný, virtuální metodu s názvem `OnValueChanged` , která vyvolává `ValueChanged` událostí.  
  
 [!code-csharp[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
 [!code-vb[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]  
  
 Další informace najdete v tématu [směrovat Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md) a [vytvoření vlastní události směrovat](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md).  
  
### <a name="use-binding"></a>Použít vazbu  
 Oddělit uživatelského ovládacího prvku z svou logikou, zvažte použití datových vazeb. To je zvlášť důležité, pokud definujete vzhled ovládacího prvku pomocí <xref:System.Windows.Controls.ControlTemplate>. Při použití datových vazeb, bude pravděpodobně možné eliminovat nutnost odkazovat na konkrétní části uživatelského rozhraní z kódu. Je vhodné-li zabránit odkazování prvky, které jsou v <xref:System.Windows.Controls.ControlTemplate> vzhledem k tomu, když kód odkazuje na prvky, které jsou v <xref:System.Windows.Controls.ControlTemplate> a <xref:System.Windows.Controls.ControlTemplate> se změní požadavky odkazovaný element mají být zahrnuty v novém <xref:System.Windows.Controls.ControlTemplate>.  
  
 Následující příklad aktualizací <xref:System.Windows.Controls.TextBlock> z `NumericUpDown` ovládacího prvku, přiřadí název a odkazování na textové pole podle názvu v kódu.  
  
 [!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]  
  
 [!code-csharp[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
 [!code-vb[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]  
  
 Vazby do provést totéž v následujícím příkladu.  
  
 [!code-xaml[UserControlNumericUpDown#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]  
  
 Další informace o datové vazbě naleznete v tématu [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
### <a name="design-for-designers"></a>Návrh pro profesionální návrháře využívající  
 Získat podporu pro vlastní ovládací prvky WPF v [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] (například v okně Vlastnosti pro úpravy vlastností), postupujte podle následujících pokynů.  Další informace o vývoji pro [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)], naleznete v tématu [návrh XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).  
  
#### <a name="dependency-properties"></a>Vlastnosti závislosti  
 Je potřeba implementovat [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] `get` a `set` přistupující objekty jak bylo popsáno dříve, v "Vlastnosti závislosti použití." Návrháři k detekci přítomnosti vlastnost závislosti, ale jejich, jako je třeba použít obálku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a klienti v ovládacím prvku není nutné volat přistupující objekty při načtení nebo nastavení vlastnosti.  
  
#### <a name="attached-properties"></a>Přidružené vlastnosti  
 Měli byste implementovat připojené vlastnosti ve vlastních ovládacích prvků pomocí následujících pokynů:  
  
-   Mít `public` `static` `readonly` <xref:System.Windows.DependencyProperty> formuláře *PropertyName* `Property` , který se vytváří pomocí <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody. Název vlastnosti, který je předán <xref:System.Windows.DependencyProperty.RegisterAttached%2A> musí odpovídat *PropertyName*.  
  
-   Implementovat pár `public` `static` CLR metody s názvem `Set` *PropertyName* a `Get` *PropertyName*. Obě metody by měla přijímat třídy odvozené od <xref:System.Windows.DependencyProperty> jako jejich první argument. `Set` *PropertyName* metoda také přijímá argument, jehož typ odpovídá typu registrované datové vlastnosti. `Get` *PropertyName* metoda by měla vracet hodnotu stejného typu. Pokud `Set` *PropertyName* chybí metoda, vlastnost je označena jako jen pro čtení.  
  
-   `Set` *Vlastnost PropertyName* a `Get` *PropertyName* musí směrovat přímo <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> metody na závislost cílové objektů. Návrháři může přístup k připojené vlastnosti volání prostřednictvím metody obálky nebo přímé volání cílový objekt závislosti.  
  
 Další informace o přidružené vlastnosti najdete v tématu [přehled připojených vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
### <a name="define-and-use-shared-resources"></a>Definice a používání sdílených prostředků  
 Může obsahovat ovládací prvek ve stejném sestavení, jako vaši aplikaci, nebo můžete zabalit ovládacího prvku v samostatných sestavení, které můžete použít ve více aplikacích. Ve většině případů informace popsané v tomto tématu platí bez ohledu na metodu, kterou používáte.  Ale jedním z rozdílů za zmínku, neexistuje.  Pokud vložíte ovládací prvek ve stejném sestavení jako aplikace, můžete libovolně udělovat globální prostředky přidat do souboru App.xaml. Ale nemá žádné sestavení, které obsahuje pouze ovládací prvky <xref:System.Windows.Application> objekt přidružený, takže není k dispozici soubor App.xaml.  
  
 Jakmile aplikace vypadá pro určitý prostředek, bude vypadat na třech úrovních v následujícím pořadí:  
  
1.  Element úroveň.  
  
     Systém začíná u prvku, který odkazuje na prostředek a a tak dále vyhledává prostředky logické nadřazené, dokud nebude dosaženo kořenový element.  
  
2.  Na úrovni aplikace.  
  
     Prostředky, které jsou definované <xref:System.Windows.Application> objektu.  
  
3.  Úroveň motiv.  
  
     Slovníky motiv úrovni jsou uloženy v podsložce s názvem motivů.  Soubory ve složce motivů odpovídají motivů.  Například může mít Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml a tak dále.  Můžete také mít soubor generic.xaml.  Když systém hledá prostředek na úrovni motivy, nejprve vyhledá ho v souboru konkrétní motivu a pak hledá ho v generic.xaml.  
  
 Pokud je váš ovládací prvek v sestavení, která je oddělená od aplikace, je nutné umístit globální prostředky na úrovni prvku nebo na úrovni motiv. Obě metody mají své výhody.  
  
#### <a name="defining-resources-at-the-element-level"></a>Definování prostředků na úrovni – Element  
 Sdílené prostředky na úrovni prvku můžete definovat vytvořením vlastních prostředků slovníku a ho sloučit s slovník prostředků ovládacího prvku.  Při použití této metody můžete pojmenovat soubor prostředků všechno, co chcete a to může být ve stejné složce jako své ovládací prvky. Jednoduché řetězce prostředku na úrovni element můžete také použít jako klíče. Následující příklad vytvoří <xref:System.Windows.Media.LinearGradientBrush> soubor prostředků s názvem Dictionary1.xaml.  
  
 [!code-xaml[SharedResources#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]  
  
 Po definování slovníku, musíte ho sloučit s slovník prostředků ovládacího prvku.  Můžete to provést pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kódu.  
  
 Následující příklad sloučí slovník prostředků s použitím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[SharedResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]  
  
 Nevýhody tohoto přístupu je, že <xref:System.Windows.ResourceDictionary> je vytvořen objekt pokaždé, když na něj odkazovat.  Například pokud máte 10 vlastních ovládacích prvků v knihovně a sloučení slovníky sdíleného prostředku pro každý ovládací prvek pomocí XAML, vytvoříte 10 identické <xref:System.Windows.ResourceDictionary> objekty.  Tím můžete vyhnout tak, že vytvoříte statické třídy, která sloučí prostředky v kódu a vrátí výsledný <xref:System.Windows.ResourceDictionary>.  
  
 Následující příklad vytvoří třídu, která vrátí hodnotu sdíleného <xref:System.Windows.ResourceDictionary>.  
  
 [!code-csharp[SharedResources#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]  
  
 Následující příklad sloučí sdílený prostředek s prostředky vlastního ovládacího prvku v konstruktoru ovládacího prvku před voláním `InitializeComponent`.  Protože `SharedDictionaryManager.SharedDictionary` je statická vlastnost <xref:System.Windows.ResourceDictionary> je vytvořen pouze jednou. Protože slovník prostředků se nesloučila před `InitializeComponent` byla volána, prostředky jsou k dispozici pro ovládací prvek v jeho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru.  
  
 [!code-csharp[SharedResources#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]  
  
#### <a name="defining-resources-at-the-theme-level"></a>Definování prostředků na úrovni motiv  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje vytvářet prostředky pro různé motivy Windows.  Jako autor ovládacího prvku můžete definovat prostředek pro konkrétní motivu pro změnu vzhledu ovládacího prvku v závislosti na tom, jaký motiv se používá. Například vzhled <xref:System.Windows.Controls.Button> v klasické Windows motivu (výchozí motiv pro Windows 2000) se liší od <xref:System.Windows.Controls.Button> v motivu Windows Luna (výchozí motiv pro systém Windows XP) protože <xref:System.Windows.Controls.Button> používá jiný <xref:System.Windows.Controls.ControlTemplate> pro každý motiv.  
  
 Prostředky, které jsou specifické pro motiv jsou uloženy ve slovníku prostředků s určitým názvem souboru. Tyto soubory musí být ve složce s názvem `Themes` , který je podsložkou složky, která obsahuje ovládací prvek. Následující tabulka uvádí soubory slovníku prostředků a motiv, který je přidružený k každého souboru:  
  
|Název souboru slovníku prostředků|Motiv Windows|  
|-----------------------------------|-------------------|  
|`Classic.xaml`|Klasické Windows 9 x / 2000 podívejte se na Windows XP|  
|`Luna.NormalColor.xaml`|Modrý motiv Windows XP|  
|`Luna.Homestead.xaml`|Olivově motiv Windows XP|  
|`Luna.Metallic.xaml`|Stříbrným motiv Windows XP|  
|`Royale.NormalColor.xaml`|Výchozí motiv na systém Windows Media Center|  
|`Aero.NormalColor.xaml`|Výchozí motiv v systému Windows Vista|  
  
 Nemusíte definovat prostředek pro každý motiv. Pokud prostředek není definován pro konkrétní motivu, ovládací prvek zkontroluje `Classic.xaml` pro prostředek. Pokud prostředek není definovaný v souboru, který odpovídá aktuální motiv nebo v `Classic.xaml`, ovládací prvek používá obecný prostředek, který se nachází v souboru slovníku prostředků s názvem `generic.xaml`.  `generic.xaml` Soubor se nachází ve stejné složce jako soubory slovníku prostředků specifických pro motiv. I když `generic.xaml` neodpovídá pro konkrétní motivu Windows, je stále slovník úrovni motiv.  
  
 [Ovládací prvek NumericUpDown vlastní motiv a ukázka podpora automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=160025) obsahuje dvě slovníky prostředků neobsahují `NumericUpDown` ovládacího prvku: jeden je v generic.xaml a jeden je v Luna.NormalColor.xaml.  Můžete spustit aplikaci a přepínat mezi stříbrné motiv Windows XP a jiný motiv zobrazíte rozdíl mezi dvěma řídicími šablony. (Pokud používáte systém Windows Vista, můžete přejmenovat Luna.NormalColor.xaml Aero.NormalColor.xaml a přepínání mezi dva motivy, jako jsou klasické Windows a výchozí motiv pro Windows Vista.)  
  
 Při vložení <xref:System.Windows.Controls.ControlTemplate> v některém z soubory slovníku prostředků konkrétní motivu, musíte vytvořit statický konstruktor pro ovládací prvek a volání <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> metodu <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
 [!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]  
  
##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Definování a odkazování na klíče pro prostředky motiv  
 Když definujete prostředek na úrovni prvku, můžete přiřadit řetězec jako svůj klíč a přístup k prostředku přes řetězec. Když definujete prostředek na úrovni motivu, je nutné použít <xref:System.Windows.ComponentResourceKey> jako klíč.  Následující příklad definuje prostředek v generic.xaml.  
  
 [!code-xaml[ThemeResourcesControlLibrary#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]  
  
 Následující příklad odkazuje na prostředek tak, že zadáte <xref:System.Windows.ComponentResourceKey> jako klíč.  
  
 [!code-xaml[ThemeResourcesControlLibrary#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]  
  
##### <a name="specifying-the-location-of-theme-resources"></a>Určení umístění motivu prostředky  
 Najít prostředky pro ovládací prvek, hostitelské aplikace potřebuje vědět, že sestavení obsahuje prostředky specifické pro ovládací prvek. Můžete to udělat tak, že přidáte <xref:System.Windows.ThemeInfoAttribute> na sestavení, která obsahuje ovládací prvek. <xref:System.Windows.ThemeInfoAttribute> Má <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> vlastnost, která určuje umístění obecné prostředky, a <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> vlastnost, která určuje umístění prostředky specifické pro motiv.  
  
 Následující příklad nastaví <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> a <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> vlastností <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>, chcete-li určit, že obecný a specifické pro konkrétní motivu jsou prostředky ve stejném sestavení jako ovládací prvek.  
  
 [!code-csharp[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
 [!code-vb[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]  
  
## <a name="see-also"></a>Viz také  
 [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [Sbalení URI v technologii WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)
