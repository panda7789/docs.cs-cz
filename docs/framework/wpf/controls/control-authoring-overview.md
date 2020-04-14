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
ms.openlocfilehash: 2326520039085beb5f5294e23db67b67f9d7d7da
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243268"
---
# <a name="control-authoring-overview"></a>Přehled vytváření ovládacích prvku

Rozšiřitelnost modelu ovládacího [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prvku výrazně snižuje potřebu vytvořit nový ovládací prvek. V některých případech však může být stále nutné vytvořit vlastní ovládací prvek. Toto téma popisuje funkce, které minimalizují potřebu vytvořit vlastní ovládací [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]prvek a různé modely vytváření ovládacích prvků v aplikaci . Toto téma také ukazuje, jak vytvořit nový ovládací prvek.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Alternativy k zápisu nového ovládacího prvku

Historicky pokud jste chtěli získat přizpůsobené prostředí z existujícího ovládacího prvku, byli jste omezeni na změnu standardních vlastností ovládacího prvku, jako je barva pozadí, šířka ohraničení a velikost písma. Pokud jste chtěli rozšířit vzhled nebo chování ovládacího prvku nad rámec těchto předdefinovaných parametrů, budete muset vytvořit nový ovládací prvek, obvykle děděním z existujícího ovládacího prvku a přepsáním metody odpovědné za kreslení ovládacího prvku.  I když je to [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stále možnost, umožňuje přizpůsobit existující ovládací prvky pomocí modelu bohatého obsahu, stylů, šablon a aktivačních událostí. Následující seznam uvádí příklady, jak lze tyto funkce použít k vytvoření vlastních a konzistentních prostředí bez nutnosti vytvářet nový ovládací prvek.

- **Bohatý obsah.** Mnoho standardních [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků podporuje bohatý obsah. Například vlastnost content <xref:System.Windows.Controls.Button> a je <xref:System.Object>typu , takže teoreticky lze <xref:System.Windows.Controls.Button>zobrazit cokoli v .  Chcete-li, aby tlačítko zobrazilo obrázek <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.StackPanel> text, <xref:System.Windows.Controls.StackPanel> můžete <xref:System.Windows.Controls.ContentControl.Content%2A> k vlastnosti přidat obrázek a a přiřadit k němu. Vzhledem k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tomu, že ovládací prvky mohou zobrazovat vizuální prvky a libovolná data, je méně potřeba vytvořit nový ovládací prvek nebo upravit existující ovládací prvek pro podporu složité vizualizace. Další informace o modelu <xref:System.Windows.Controls.Button> obsahu pro a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]další modely obsahu v [tématu WPF Content Model](wpf-content-model.md).

- **Styly.** A <xref:System.Windows.Style> je kolekce hodnot, které představují vlastnosti ovládacího prvku. Pomocí stylů můžete vytvořit opakovaně použitelnou reprezentaci požadovaného vzhledu ovládacího prvku a chování bez psaní nového ovládacího prvku. Předpokládejme například, že chcete, aby všechny ovládací <xref:System.Windows.Controls.TextBlock> prvky měly červenou barvu Písmo Arial s velikostí písma 14. Můžete vytvořit styl jako prostředek a odpovídajícím způsobem nastavit příslušné vlastnosti. Pak <xref:System.Windows.Controls.TextBlock> každý, který přidáte do aplikace bude mít stejný vzhled.

- **Šablony dat.** A <xref:System.Windows.DataTemplate> umožňuje přizpůsobit způsob zobrazení dat v ovládacím prvku. Lze například <xref:System.Windows.DataTemplate> použít k určení způsobu zobrazení dat <xref:System.Windows.Controls.ListBox>v .  Příklad najdete v tématu [Přehled šablon ování dat](../data/data-templating-overview.md).  Kromě přizpůsobení vzhledu dat může <xref:System.Windows.DataTemplate> a obsahovat prvky uživatelského rozhraní, což poskytuje velkou flexibilitu ve vlastních uživatelskéch rozhraních.  Například pomocí <xref:System.Windows.DataTemplate>aplikace můžete vytvořit <xref:System.Windows.Controls.ComboBox> zaškrtávací políčko , ve kterém každá položka obsahuje.

- **Šablony ovládacího prvku.** Mnoho ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použití a <xref:System.Windows.Controls.ControlTemplate> definovat strukturu a vzhled ovládacího prvku, který odděluje vzhled ovládacího prvku z funkce ovládacího prvku. Můžete výrazně změnit vzhled ovládacího prvku předefinováním jeho <xref:System.Windows.Controls.ControlTemplate>.  Předpokládejme například, že chcete ovládací prvek, který vypadá jako semafor. Tento ovládací prvek má jednoduché uživatelské rozhraní a funkce.  Ovládací prvek je tři kruhy, z nichž pouze jeden může být rozsvícen najednou. Po nějakém odrazu si <xref:System.Windows.Controls.RadioButton> možná uvědomíte, že funkce pouze jednoho je vybrána <xref:System.Windows.Controls.RadioButton> najednou, ale výchozí vzhled vypadá vůbec jako světla na semaforu.  Vzhledem <xref:System.Windows.Controls.RadioButton> k tomu, že šablona ovládacího prvku <xref:System.Windows.Controls.ControlTemplate> používá k definování vzhledu ovládací prvek, je snadné předefinovat tak, aby odpovídalpožadavkům ovládacího prvku, a pomocí přepínačů vytvořte semafor.

  > [!NOTE]
  > I <xref:System.Windows.Controls.RadioButton> když lze <xref:System.Windows.DataTemplate>použít <xref:System.Windows.DataTemplate> , a není dostatečná v tomto příkladu.  Definuje <xref:System.Windows.DataTemplate> vzhled obsahu ovládacího prvku. V případě <xref:System.Windows.Controls.RadioButton>a je obsah, který se zobrazí vpravo od <xref:System.Windows.Controls.RadioButton> kruhu, který označuje, zda je vybrán.  V příkladu semaforu musí být přepínací tlačítko jen kruhem, který se může "rozsvítit". Vzhledem k tomu, že požadavek na vzhled <xref:System.Windows.Controls.RadioButton>semaforu se <xref:System.Windows.Controls.ControlTemplate>tak liší od výchozího vzhledu aplikace , je nutné předefinovat .  Obecně a <xref:System.Windows.DataTemplate> se používá pro definování obsahu (nebo data) <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku a a se používá pro definování struktury ovládacího prvku.

- **Aktivační události.** A <xref:System.Windows.Trigger> umožňuje dynamicky měnit vzhled a chování ovládacího prvku bez vytvoření nového ovládacího prvku. Předpokládejme například, <xref:System.Windows.Controls.ListBox> že máte v aplikaci více <xref:System.Windows.Controls.ListBox> ovládacích prvků a chcete, aby položky v každé z nich byly tučné a červené, když jsou vybrány. Prvním instinktem může být vytvoření třídy, která dědí z <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> metody a přepíše ji za účelem změny vzhledu <xref:System.Windows.Controls.ListBoxItem> vybrané položky, ale lepším přístupem je přidání aktivační události ke stylu a, který mění vzhled vybrané položky. Aktivační událost umožňuje změnit hodnoty vlastností nebo provést akce na základě hodnoty vlastnosti. A <xref:System.Windows.EventTrigger> umožňuje provést akce, když dojde k události.

Další informace o stylech, šablonách a aktivačních událostech naleznete [v tématu Stylování a šablonování](styling-and-templating.md).

Obecně platí, že pokud ovládací prvek zrcadlí funkce existujícího ovládacího prvku, ale chcete, aby ovládací prvek vypadat jinak, měli byste nejprve zvážit, zda můžete použít některou z metod popsaných v této části změnit existující ovládací prvek vzhled.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Modely pro vytváření ovládacích prvku

Model bohatého obsahu, styly, šablony a aktivační události minimalizují potřebu vytvořit nový ovládací prvek. Pokud však potřebujete vytvořit nový ovládací prvek, je důležité porozumět různým [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]modelům vytváření ovládacího prvku v . [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje tři obecné modely pro vytvoření ovládacího prvku, z nichž každý poskytuje jinou sadu funkcí a úroveň flexibility. Základní třídy pro tři <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Control>modely <xref:System.Windows.FrameworkElement>jsou , , a .

### <a name="deriving-from-usercontrol"></a>Odvození z usercontrolu

Nejjednodušší způsob, jak vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek <xref:System.Windows.Controls.UserControl>v je odvodit z . Při vytváření ovládacího prvku, <xref:System.Windows.Controls.UserControl>který dědí z <xref:System.Windows.Controls.UserControl>, přidáte existující součásti do , [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]pojmenujte součásti a referenční obslužné rutiny událostí v aplikaci . Potom můžete odkazovat na pojmenované prvky a definovat obslužné rutiny událostí v kódu. Tento vývojový model je velmi podobný modelu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]používanému pro vývoj aplikací v aplikaci .

Pokud je sestaven <xref:System.Windows.Controls.UserControl> správně, může a využít výhod bohatého obsahu, stylů a aktivačních událostí. Pokud však váš ovládací <xref:System.Windows.Controls.UserControl>prvek dědí od , uživatelé, <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ControlTemplate> kteří používají ovládací prvek, nebudou moci použít nebo přizpůsobit jeho vzhled.  Je nutné odvodit z <xref:System.Windows.Controls.Control> třídy nebo jedné <xref:System.Windows.Controls.UserControl>z jejích odvozených tříd (jiné než) k vytvoření vlastního ovládacího prvku, který podporuje šablony.

#### <a name="benefits-of-deriving-from-usercontrol"></a>Výhody odvození od UserControl

Zvažte odvození <xref:System.Windows.Controls.UserControl> od, pokud platí všechny tyto platí:

- Chcete vytvořit ovládací prvek podobně jako sestavení aplikace.

- Ovládací prvek se skládá pouze z existujících součástí.

- Nemusíte podporovat složité přizpůsobení.

### <a name="deriving-from-control"></a>Odvození z řízení

Odvození z <xref:System.Windows.Controls.Control> třídy je model používaný většinou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existujících ovládacích prvků. Když vytvoříte ovládací prvek, <xref:System.Windows.Controls.Control> který dědí z třídy, definujete jeho vzhled pomocí šablon. Tímto způsobem oddělíte provozní logiku od vizuální reprezentace. Můžete také zajistit oddělení uživatelského rozhraní a logiky pomocí příkazů a vazeb namísto událostí <xref:System.Windows.Controls.ControlTemplate> a vyhnout se odkazování na prvky v kdykoli je to možné.  Pokud uživatelské rozhraní a logika ovládacího prvku jsou správně odděleny, uživatel ovládacího prvku můžete předefinovat ovládacího prvku <xref:System.Windows.Controls.ControlTemplate> přizpůsobit jeho vzhled. I když <xref:System.Windows.Controls.Control> vytváření vlastní není tak <xref:System.Windows.Controls.UserControl>jednoduché <xref:System.Windows.Controls.Control> jako budování , vlastní poskytuje největší flexibilitu.

#### <a name="benefits-of-deriving-from-control"></a>Výhody deriving z kontroly

Zvažte odvození <xref:System.Windows.Controls.Control> od místo <xref:System.Windows.Controls.UserControl> použití třídy, pokud platí některou z následujících platí:

- Chcete, aby vzhled ovládacího prvku bylo možné <xref:System.Windows.Controls.ControlTemplate>přizpůsobit pomocí .

- Chcete, aby vaše ovládací prvek podporoval různé motivy.

### <a name="deriving-from-frameworkelement"></a>Odvození z FrameworkElement

Ovládací prvky, které jsou odvozeny z <xref:System.Windows.Controls.UserControl> nebo <xref:System.Windows.Controls.Control> spoléhají na vytváření existujících prvků. Pro mnoho scénářů je to přijatelné řešení, protože <xref:System.Windows.FrameworkElement> jakýkoli objekt, <xref:System.Windows.Controls.ControlTemplate>který dědí z může být v . Existují však časy, kdy vzhled ovládacího prvku vyžaduje více než funkce složení jednoduchého prvku. Pro tyto scénáře je založenna součást <xref:System.Windows.FrameworkElement> je správná volba.

Existují dvě standardní metody <xref:System.Windows.FrameworkElement>pro vytváření komponent založených na: přímé vykreslování a vlastní kompozice prvků. Přímé vykreslování zahrnuje přepsání <xref:System.Windows.UIElement.OnRender%2A> <xref:System.Windows.FrameworkElement> metody a poskytování <xref:System.Windows.Media.DrawingContext> operací, které explicitně definují vizuály komponenty. Jedná se o <xref:System.Windows.Controls.Image> metodu používanou a . <xref:System.Windows.Controls.Border> Vlastní kompozice prvku zahrnuje <xref:System.Windows.Media.Visual> použití objektů typu k vytvoření vzhledu komponenty. Příklad naleznete v tématu [Použití kresleníVizuální objekty](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track>je příkladem ovládacího [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvku, který používá vlastní složení prvků. Je také možné kombinovat přímé vykreslování a vlastní kompozici prvků ve stejném ovládacím prvku.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>Výhody odvození od FrameworkElement

Zvažte odvození <xref:System.Windows.FrameworkElement> od některý z následujících platí:

- Chcete mít přesnou kontrolu nad vzhled vaší kontroly nad rámec toho, co je poskytováno jednoduché složení prvku.

- Chcete definovat vzhled ovládacího prvku definováním vlastní logiky vykreslení.

- Chcete vytvořit existující prvky novými způsoby, které <xref:System.Windows.Controls.UserControl> přesahují to, co je možné s a <xref:System.Windows.Controls.Control>.

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>Základy vytváření ovládacích prvku

Jak již bylo popsáno dříve, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jedním z nejvýkonnějších funkcí je schopnost jít nad rámec nastavení základních vlastností ovládacího prvku změnit jeho vzhled a chování, ale stále není nutné vytvořit vlastní ovládací prvek. Styl, datová vazba a funkce aktivační [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události jsou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožněny systémem vlastností a systémem událostí. Následující části popisují některé postupy, které byste měli dodržovat, bez ohledu na model, který používáte k vytvoření vlastního ovládacího prvku, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aby uživatelé vlastního ovládacího prvku mohli používat tyto funkce stejně jako pro ovládací prvek, který je součástí aplikace .

### <a name="use-dependency-properties"></a>Použít vlastnosti závislosti

Pokud je vlastnost vlastností závislosti, je možné provést následující kroky:

- Nastavte vlastnost ve stylu.

- Spojte vlastnost se zdrojem dat.

- Jako hodnotu vlastnosti použijte dynamický prostředek.

- Animovat vlastnost.

Pokud chcete vlastnost ovládacího prvku pro podporu některé z těchto funkcí, měli byste implementovat jako vlastnost závislosti. Následující příklad definuje vlastnost závislosti `Value` pojmenovanou následujícím způsobem:

- Definujte <xref:System.Windows.DependencyProperty> identifikátor `ValueProperty` pojmenovaný `public` `static` `readonly` jako pole.

- Zaregistrujte název vlastnosti v systému vlastností voláním <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>, chcete-li zadat následující:

  - Název vlastnosti

  - Typ proměnné

  - Typ, který vlastní vlastnost.

  - Metadata pro vlastnost. Metadata obsahují výchozí hodnotu vlastnosti, <xref:System.Windows.CoerceValueCallback> <xref:System.Windows.PropertyChangedCallback>a a .

- Definujte vlastnost obálky `Value`CLR s názvem , což je stejný název, který se používá `get` `set` k registraci vlastnosti závislosti implementací vlastnosti a přistupujících objektů. Všimněte `get` si, že `set` a <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> přístupové akce pouze volání a příslušně. Doporučuje se, aby přístupové objekty vlastností závislostí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neobsahovaly další logiku, <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> protože klienti a mohou obejít přístupové objekty a volat a přímo. Například když je vlastnost vázána na zdroj dat, `set` přistupující objekt vlastnosti není volána.  Namísto přidání další logiku získat a nastavit <xref:System.Windows.ValidateValueCallback>přístupové skupiny, použijte , <xref:System.Windows.CoerceValueCallback>a <xref:System.Windows.PropertyChangedCallback> delegáti reagovat nebo zkontrolovat hodnotu při změně.  Další informace o těchto zpětná volání naleznete [v tématu závislost vlastnost i zpětná ověření](../advanced/dependency-property-callbacks-and-validation.md).

- Definujte metodu <xref:System.Windows.CoerceValueCallback> `CoerceValue`pro pojmenované . `CoerceValue`zajišťuje, `Value` že je větší `MinValue` nebo rovna `MaxValue`a menší než nebo rovna .

- Definujte metodu <xref:System.Windows.PropertyChangedCallback>pro `OnValueChanged`, s názvem . `OnValueChanged`vytvoří <xref:System.Windows.RoutedPropertyChangedEventArgs%601> objekt a připraví se `ValueChanged` na zvýšení směrované události. Směrované události jsou popsány v další části.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Další informace naleznete [v tématu Vlastní vlastnosti závislostí](../advanced/custom-dependency-properties.md).

### <a name="use-routed-events"></a>Použít směrované události

Stejně jako vlastnosti závislostí rozšířit pojem CLR vlastnosti s další funkce, směrované události rozšířit pojem standardní clr události. Při vytváření nového ovládacího [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvku je také vhodné implementovat událost jako směrovou událost, protože směrovaná událost podporuje následující chování:

- Události mohou být zpracovány na nadřazené více ovládacích prvků. Pokud událost je probublávání událost, jeden nadřazený ve stromu elementu můžete přihlásit k odběru události. Autoři aplikace pak mohou použít jednu obslužnou rutinu k reakci na událost více ovládacích prvků. Například pokud je ovládací prvek součástí každé <xref:System.Windows.Controls.ListBox> položky v (protože je součástí <xref:System.Windows.DataTemplate>) vývojář aplikace můžete definovat obslužnou rutinu události pro událost ovládacího prvku na . <xref:System.Windows.Controls.ListBox> Vždy, když dojde k události na některý z ovládacích prvků, je volána obslužná rutina události.

- Směrované události lze použít <xref:System.Windows.EventSetter>v aplikaci , která vývojářům aplikací umožňuje určit obslužnou rutinu události ve stylu.

- Směrované události lze použít <xref:System.Windows.EventTrigger>v aplikaci , což je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]užitečné pro animaci vlastností pomocí . Další informace naleznete v [tématu Přehled animace](../graphics-multimedia/animation-overview.md).

Následující příklad definuje směrovou událost následujícím způsobem:

- Definujte <xref:System.Windows.RoutedEvent> identifikátor `ValueChangedEvent` pojmenovaný `public` `static` `readonly` jako pole.

- Zaregistrujte směrovou <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> událost voláním metody. Příklad určuje následující informace při <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>volání :

  - Název události je `ValueChanged`.

  - Strategie směrování <xref:System.Windows.RoutingStrategy.Bubble>je , což znamená, že obslužná rutina události ve zdroji (objekt, který vyvolává událost) je volána jako první a obslužná rutina událostí na nadřazených prvcích zdroje jsou volána postupně, počínaje obslužnou rutinou události na nejbližším nadřazeném prvku.

  - Typ obslužné <xref:System.Windows.RoutedPropertyChangedEventHandler%601>rutiny události <xref:System.Decimal> je vytvořen s typem.

  - Vlastnící typ události je `NumericUpDown`.

- Deklarujte `ValueChanged` veřejnou událost s názvem a zahrnuje deklarace přístupového přístupu k událostem. Příklad volá <xref:System.Windows.UIElement.AddHandler%2A> v `add` deklaraci <xref:System.Windows.UIElement.RemoveHandler%2A> přistupujícího serveru a v deklaraci přistupujícího `remove` serveru pro použití služby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události.

- Vytvořte chráněnou virtuální `OnValueChanged` metodu `ValueChanged` s názvem, která vyvolá událost.

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Další informace naleznete v tématech [Přehled směrovaných událostí](../advanced/routed-events-overview.md) a [Vytvoření vlastní směrované události](../advanced/how-to-create-a-custom-routed-event.md).

### <a name="use-binding"></a>Použít vazbu

Chcete-li oddělit ui ovládacího prvku z jeho logiky, zvažte použití datové vazby. To je obzvláště důležité, pokud definujete vzhled <xref:System.Windows.Controls.ControlTemplate>ovládacího prvku pomocí . Při použití datové vazby, můžete být schopni eliminovat potřebu odkazovat na určité části uj.s z kódu. Je vhodné, aby se zabránilo odkazování na <xref:System.Windows.Controls.ControlTemplate> prvky, které jsou v, <xref:System.Windows.Controls.ControlTemplate> protože <xref:System.Windows.Controls.ControlTemplate> když kód odkazuje na prvky, které <xref:System.Windows.Controls.ControlTemplate>jsou v a je změněn, odkazovaný prvek musí být zahrnuty do nového .

Následující příklad aktualizuje <xref:System.Windows.Controls.TextBlock> `NumericUpDown` ovládací prvek, přiřazuje mu název a odkazuje na textové pole podle názvu v kódu.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

Následující příklad používá vazbu k dosažení stejné věci.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Další informace o datové vazbě naleznete v [tématu Přehled datové vazby](../../../desktop-wpf/data/data-binding-overview.md).

### <a name="design-for-designers"></a>Design pro designéry

Chcete-li získat podporu pro vlastní ovládací prvky WPF v NávrhářwPF pro Visual Studio (například úpravy vlastností s okno Vlastnosti), postupujte podle těchto pokynů.  Další informace o vývoji pro WPF Designer, naleznete v [tématu Návrh XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

#### <a name="dependency-properties"></a>Vlastnosti závislosti

Nezapomeňte implementovat `get` CLR `set` a přistupující objekty, jak je popsáno výše, v "Použití vlastností závislostí." Návrháři mohou použít obálku ke zjištění přítomnosti vlastnosti závislosti, ale oni, stejně jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a klienti ovládacího prvku, nejsou povinni volat přistupující objekty při získávání nebo nastavování vlastnosti.

#### <a name="attached-properties"></a>Přidružené vlastnosti

Měli byste implementovat připojené vlastnosti na vlastní ovládací prvky pomocí následujících pokynů:

- `public` `Property` <xref:System.Windows.DependencyProperty.RegisterAttached%2A> Mít formulář *PropertyName,* který byl vytváření pomocí metody. `static` `readonly` <xref:System.Windows.DependencyProperty> Název vlastnosti, který <xref:System.Windows.DependencyProperty.RegisterAttached%2A> je předán, musí odpovídat *PropertyName*.

- Implementujte `public` `static` dvojici metod `Set`CLR s názvem *PropertyName* a `Get` *PropertyName*. Obě metody by měly <xref:System.Windows.DependencyProperty> přijmout třídu odvozenou z jako jejich první argument. `Set` *PropertyName* Metoda také přijímá argument, jehož typ odpovídá registrovaný datový typ pro vlastnost. `Get` *PropertyName* Metoda by měla vrátit hodnotu stejného typu. `Set`Pokud *PropertyName* metoda chybí, vlastnost je označenjen pro čtení.

- `Set`*PropertyName* `Get`a *PropertyName* musí <xref:System.Windows.DependencyObject.GetValue%2A> směrovat <xref:System.Windows.DependencyObject.SetValue%2A> přímo na a metody na objektu cílové závislosti, v uvedeném pořadí. Návrháři mohou přistupovat k připojené vlastnosti voláním prostřednictvím obálky metody nebo přímým voláním objektu cílové závislosti.

Další informace o připojených vlastnostech naleznete v tématu [Přehled připojených vlastností](../advanced/attached-properties-overview.md).

### <a name="define-and-use-shared-resources"></a>Definování a použití sdílených prostředků

Můžete zahrnout ovládací prvek ve stejném sestavení jako vaše aplikace, nebo můžete zabalit ovládací prvek v samostatném sestavení, které lze použít ve více aplikacích. Informace popsané v tomto tématu se většinou použijí bez ohledu na metodu, kterou používáte.  Existuje však jeden rozdíl, který stojí za zmínku.  Když vložíte ovládací prvek do stejného sestavení jako aplikace, můžete přidat globální prostředky do souboru App.xaml. Ale sestavení, které obsahuje pouze <xref:System.Windows.Application> ovládací prvky nemá objekt s ním spojené, takže soubor App.xaml není k dispozici.

Když aplikace hledá prostředek, vypadá na třech úrovních v následujícím pořadí:

1. Úroveň prvku.

   Systém začíná s elementem, který odkazuje na prostředek a potom prohledává prostředky logické nadřazené a tak dále, dokud není dosaženo kořenového prvku.

2. Úroveň aplikace.

   Prostředky definované <xref:System.Windows.Application> objektem.

3. Úroveň motivu.

   Slovníky na úrovni motivu jsou uloženy v podsložce s názvem Motivy.  Soubory ve složce Motivy odpovídají motivům.  Můžete mít například Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml a tak dále.  Můžete také mít soubor s názvem generic.xaml.  Když systém hledá prostředek na úrovni motivů, nejprve ho vyhledá v souboru specifickém pro motiv a pak ho vyhledá v souboru generic.xaml.

Pokud je ovládací prvek v sestavení, které je oddělené od aplikace, je nutné umístit globální prostředky na úrovni prvku nebo na úrovni motivu. Obě metody mají své výhody.

#### <a name="defining-resources-at-the-element-level"></a>Definování zdrojů na úrovni prvku

Sdílené prostředky můžete definovat na úrovni prvku vytvořením vlastního slovníku prostředků a jeho sloučením se slovníkem prostředků ovládacího prvku.  Při použití této metody můžete pojmenovat soubor prostředků, co chcete, a může být ve stejné složce jako ovládací prvky. Prostředky na úrovni prvku můžete také použít jednoduché řetězce jako klíče. Následující příklad vytvoří <xref:System.Windows.Media.LinearGradientBrush> soubor prostředků s názvem Dictionary1.xaml.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Po definování slovníku je třeba jej sloučit se slovníkem prostředků ovládacího prvku.  Můžete to provést [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocí nebo kód.

Následující příklad sloučí slovník prostředků [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]pomocí .

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

Nevýhodou tohoto přístupu <xref:System.Windows.ResourceDictionary> je, že objekt je vytvořen pokaždé, když na něj odkazujete.  Máte-li například v knihovně 10 vlastních ovládacích prvků a sloučíte slovníky sdílených prostředků pro každý ovládací prvek pomocí jazyka XAML, vytvoříte 10 identických <xref:System.Windows.ResourceDictionary> objektů.  Tomu se můžete vyhnout vytvořením statické třídy, která slučuje prostředky v kódu a vrací výsledné <xref:System.Windows.ResourceDictionary>.

Následující příklad vytvoří třídu, <xref:System.Windows.ResourceDictionary>která vrací sdílené .

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

Následující příklad sloučí sdílený prostředek se prostředky vlastního ovládacího prvku v `InitializeComponent`konstruktoru ovládacího prvku před voláním .  Vzhledem `SharedDictionaryManager.SharedDictionary` k tomu, <xref:System.Windows.ResourceDictionary> že je statická vlastnost, je vytvořen pouze jednou. Vzhledem k tomu, `InitializeComponent` že slovník prostředků byl sloučen dříve, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] než byl volán, prostředky jsou k dispozici pro ovládací prvek v jeho souboru.

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Definování zdrojů na úrovni motivu

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umožňuje vytvářet prostředky pro různé motivy systému Windows.  Jako autor ovládacího prvku můžete definovat prostředek pro konkrétní motiv a změnit vzhled ovládacího prvku v závislosti na tom, jaký motiv se používá. Například vzhled motivu <xref:System.Windows.Controls.Button> A v klasickém systému Windows (výchozí motiv pro systém <xref:System.Windows.Controls.Button> Windows 2000) se liší od vzhledu motivu Windows Luna (výchozí motiv pro systém Windows XP), protože <xref:System.Windows.Controls.Button> pro každý motiv používá jiný. <xref:System.Windows.Controls.ControlTemplate>

Prostředky, které jsou specifické pro motiv, jsou uloženy ve slovníku prostředků s určitým názvem souboru. Tyto soubory musí být `Themes` ve složce s názvem, která je podsložkou složky, která obsahuje ovládací prvek. V následující tabulce jsou uvedeny soubory slovníku prostředků a motiv, který je přidružen ke každému souboru:

|Název souboru slovníku prostředků|Motiv pro Windows|
|-----------------------------------|-------------------|
|`Classic.xaml`|Klasický vzhled systému Windows 9x/2000 v systému Windows XP|
|`Luna.NormalColor.xaml`|Výchozí modrý motiv v systému Windows XP|
|`Luna.Homestead.xaml`|Motiv Oliva v systému Windows XP|
|`Luna.Metallic.xaml`|Stříbrný motiv v systému Windows XP|
|`Royale.NormalColor.xaml`|Výchozí motiv v systému Windows XP Media Center Edition|
|`Aero.NormalColor.xaml`|Výchozí motiv v systému Windows Vista|

Není nutné definovat zdroj pro každý motiv. Pokud zdroj není definován pro konkrétní motiv, pak `Classic.xaml` ovládací prvek zkontroluje pro zdroj. Pokud prostředek není definován v souboru, který odpovídá aktuálnímu motivu nebo v `Classic.xaml`, ovládací prvek používá `generic.xaml`obecný prostředek, který je v souboru slovníku prostředků s názvem .  Soubor `generic.xaml` je umístěn ve stejné složce jako soubory slovníku prostředků specifické pro motivy. Přestože `generic.xaml` neodpovídá určitému motivu systému Windows, stále se jedná o slovník na úrovni motivu.

C# nebo [Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) NumericUpDown vlastní ovládací prvek s motiva a ui automatizace podporu vzorku obsahuje dva slovníky prostředků pro `NumericUpDown` ovládací prvek: jeden je v generic.xaml a druhý je v Luna.NormalColor.xaml. [C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)

Pokud vložíte <xref:System.Windows.Controls.ControlTemplate> některý ze souborů slovníku prostředků specifických pro motiv, musíte vytvořit statický <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> konstruktor <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>pro ovládací prvek a volat metodu na , jak je znázorněno v následujícím příkladu.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Definování a odkazování na klíče pro prostředky motivu

Když definujete prostředek na úrovni prvku, můžete přiřadit řetězec jako jeho klíč a získat přístup k prostředku prostřednictvím řetězce. Když definujete prostředek na úrovni motivu, <xref:System.Windows.ComponentResourceKey> musíte použít klíč.  Následující příklad definuje prostředek v souboru generic.xaml.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

Následující příklad odkazuje na prostředek zadáním <xref:System.Windows.ComponentResourceKey> jako klíč.

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Určení umístění prostředků motivu

Chcete-li najít prostředky pro ovládací prvek, hostitelské aplikace potřebuje vědět, že sestavení obsahuje prostředky specifické pro ovládací prvek. Můžete dosáhnout přidáním <xref:System.Windows.ThemeInfoAttribute> sestavení, které obsahuje ovládací prvek. Má <xref:System.Windows.ThemeInfoAttribute> <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> vlastnost, která určuje umístění obecných prostředků <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> a vlastnost, která určuje umístění prostředků specifických pro motiv.

Následující příklad nastaví vlastnosti <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> a <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> na <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>, chcete-li určit, že obecné prostředky a prostředky specifické pro motiv jsou ve stejném sestavení jako ovládací prvek.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Viz také

- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Sbalení URI v technologii WPF](../app-development/pack-uris-in-wpf.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
