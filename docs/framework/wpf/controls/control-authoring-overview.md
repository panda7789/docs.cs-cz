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
ms.openlocfilehash: 1ac8964f915206205d5c9e6ab782fcaa59bf2a99
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975719"
---
# <a name="control-authoring-overview"></a>Přehled řízeného vytváření

Rozšiřitelnost modelu ovládacího prvku [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] významně omezuje nutnost vytvoření nového ovládacího prvku. V některých případech však můžete stále potřebovat vytvořit vlastní ovládací prvek. Toto téma popisuje funkce, které minimalizují nutnost vytvořit vlastní ovládací prvek a různé modely vytváření ovládacích prvků v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Toto téma také ukazuje, jak vytvořit nový ovládací prvek.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Alternativy k psaní nového ovládacího prvku

Pokud jste si chtěli přizpůsobené prostředí získat z existujícího ovládacího prvku, bylo omezeno na změnu standardních vlastností ovládacího prvku, jako je barva pozadí, Šířka ohraničení a velikost písma. Pokud jste chtěli zvětšit vzhled nebo chování ovládacího prvku nad rámec těchto předdefinovaných parametrů, je nutné vytvořit nový ovládací prvek, obvykle děděním z existujícího ovládacího prvku a přepsáním metody zodpovědné za vykreslení ovládacího prvku.  I když je to stále možnost, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vám umožní přizpůsobit existující ovládací prvky pomocí jejího bohatýho modelu obsahu, stylů, šablon a triggerů. Následující seznam obsahuje příklady, jak lze tyto funkce použít k vytvoření vlastních a konzistentních prostředí, aniž byste museli vytvořit nový ovládací prvek.

- **Bohatě bohatý obsah.** Mnohé ze standardních [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků podporují bohatou obsah. Například vlastnost content <xref:System.Windows.Controls.Button> je typu <xref:System.Object>, takže teoreticky lze zobrazit na <xref:System.Windows.Controls.Button>.  Chcete-li mít tlačítko Zobrazit obrázek a text, můžete do <xref:System.Windows.Controls.StackPanel> přidat obrázek a <xref:System.Windows.Controls.TextBlock> a přiřadit <xref:System.Windows.Controls.StackPanel> k vlastnosti <xref:System.Windows.Controls.ContentControl.Content%2A>. Vzhledem k tomu, že ovládací prvky mohou zobrazit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vizuální prvky a libovolná data, je méně nutné vytvořit nový ovládací prvek nebo upravit existující ovládací prvek pro podporu komplexní vizualizace. Další informace o modelu obsahu pro <xref:System.Windows.Controls.Button> a dalších modelech obsahu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]najdete v tématu [model obsahu WPF](wpf-content-model.md).

- **Nadpis.** <xref:System.Windows.Style> je kolekce hodnot, které reprezentují vlastnosti ovládacího prvku. Pomocí stylů lze vytvořit opakovaně použitelná reprezentace požadovaného vzhledu a chování ovládacího prvku bez psaní nového ovládacího prvku. Předpokládejme například, že chcete, aby všechny ovládací prvky <xref:System.Windows.Controls.TextBlock> měly červené písmo Arial Font s velikostí písma 14. Můžete vytvořit styl jako prostředek a odpovídajícím způsobem nastavit odpovídající vlastnosti. Pak všechny <xref:System.Windows.Controls.TextBlock>, které přidáte do vaší aplikace, budou mít stejný vzhled.

- **Datové šablony.** <xref:System.Windows.DataTemplate> umožňuje přizpůsobit způsob zobrazení dat na ovládacím prvku. Například <xref:System.Windows.DataTemplate> lze použít k určení způsobu zobrazení dat v <xref:System.Windows.Controls.ListBox>.  Příklad najdete v tématu [Přehled šablonování dat](../data/data-templating-overview.md).  Kromě přizpůsobení vzhledu dat může <xref:System.Windows.DataTemplate> obsahovat prvky uživatelského rozhraní, které vám poskytnou značnou flexibilitu ve vlastních uživatelská rozhraní.  Například pomocí <xref:System.Windows.DataTemplate>můžete vytvořit <xref:System.Windows.Controls.ComboBox>, ve kterém každá položka obsahuje zaškrtávací políčko.

- **Šablony ovládacích prvků.** Mnoho ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá <xref:System.Windows.Controls.ControlTemplate> k definování struktury a vzhledu ovládacího prvku, který odděluje vzhled ovládacího prvku od funkce ovládacího prvku. Vzhled ovládacího prvku můžete významně změnit předefinováním jeho <xref:System.Windows.Controls.ControlTemplate>.  Předpokládejme například, že chcete ovládací prvek, který vypadá jako semafor. Tento ovládací prvek má jednoduché uživatelské rozhraní a funkce.  Ovládací prvek je tři kroužky, pouze jeden z nich lze rozsvítit současně. Po určité reflexi si můžete všimnout, že <xref:System.Windows.Controls.RadioButton> nabízí možnost výběru pouze jednoho výběru, ale výchozí vzhled <xref:System.Windows.Controls.RadioButton> v semaforu nevypadá jako světla.  Vzhledem k tomu, že <xref:System.Windows.Controls.RadioButton> používá šablonu ovládacího prvku k definování jejího vzhledu, je snadné předefinovat <xref:System.Windows.Controls.ControlTemplate> tak, aby vyhovovala požadavkům ovládacího prvku, a pomocí přepínačů vytvořit svůj semafor.

  > [!NOTE]
  > I když <xref:System.Windows.Controls.RadioButton> může použít <xref:System.Windows.DataTemplate>, <xref:System.Windows.DataTemplate> není v tomto příkladu dostačující.  <xref:System.Windows.DataTemplate> definuje vzhled obsahu ovládacího prvku. V případě <xref:System.Windows.Controls.RadioButton>se obsah zobrazuje napravo od kruhu, který označuje, jestli je vybraná <xref:System.Windows.Controls.RadioButton>.  Přepínač v příkladu semaforu potřebuje jenom kruh, který může "světlo". Vzhledem k tomu, že je požadavek na zobrazení semaforu jiný než výchozí vzhled <xref:System.Windows.Controls.RadioButton>, je nutné předefinovat <xref:System.Windows.Controls.ControlTemplate>.  Obecně <xref:System.Windows.DataTemplate> slouží k definování obsahu (nebo dat) ovládacího prvku a k definování způsobu strukturování ovládacího prvku se používá <xref:System.Windows.Controls.ControlTemplate>.

- **Zpráv.** <xref:System.Windows.Trigger> umožňuje dynamicky měnit vzhled a chování ovládacího prvku bez vytvoření nového ovládacího prvku. Předpokládejme například, že máte v aplikaci více <xref:System.Windows.Controls.ListBox> ovládacích prvků a chcete, aby byly položky v každém <xref:System.Windows.Controls.ListBox> v případě výběru tučné a červené. První Instinct může být vytvořit třídu, která dědí z <xref:System.Windows.Controls.ListBox> a přepsat metodu <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A>, aby změnila vzhled vybrané položky, ale lepším přístupem je přidat Trigger do stylu <xref:System.Windows.Controls.ListBoxItem>, který změní vzhled vybrané položky. Aktivační událost umožňuje změnit hodnoty vlastností nebo provést akce na základě hodnoty vlastnosti. <xref:System.Windows.EventTrigger> umožňuje provádět akce, když dojde k události.

Další informace o stylech, šablonách a triggerech naleznete v tématu [stylování and šablonování](styling-and-templating.md).

Obecně platí, že pokud váš ovládací prvek zrcadlí funkčnost stávajícího ovládacího prvku, ale chcete, aby ovládací prvek vypadal jinak, měli byste nejprve zvážit, zda můžete použít kteroukoli z metod popsaných v této části, chcete-li změnit vzhled stávajícího ovládacího prvku.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Modely pro vytváření ovládacích prvků

Bohatě vytvořený model obsahu, styly, šablony a triggery minimalizují nutnost vytvoření nového ovládacího prvku. Pokud však potřebujete vytvořit nový ovládací prvek, je důležité pochopit různé modely vytváření ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje tři obecné modely pro vytvoření ovládacího prvku, z nichž každý nabízí různé sady funkcí a úrovně flexibility. Základní třídy pro tři modely jsou <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control>a <xref:System.Windows.FrameworkElement>.

### <a name="deriving-from-usercontrol"></a>Odvození od prvku UserControl

Nejjednodušší způsob, jak vytvořit ovládací prvek v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], je odvozovat z <xref:System.Windows.Controls.UserControl>. Při sestavování ovládacího prvku, který dědí z <xref:System.Windows.Controls.UserControl>, přidáte existující součásti do <xref:System.Windows.Controls.UserControl>, pojmenujte komponenty a referenční obslužné rutiny událostí v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Pak můžete odkazovat na pojmenované elementy a definovat obslužné rutiny událostí v kódu. Tento model vývoje se velmi podobá modelu používanému pro vývoj aplikací v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Pokud je tato <xref:System.Windows.Controls.UserControl> sestavená správně, může využít výhod mnoha druhů obsahu, stylů a triggerů. Nicméně pokud váš ovládací prvek dědí z <xref:System.Windows.Controls.UserControl>, uživatelé, kteří používají ovládací prvek, nebudou moci použít <xref:System.Windows.DataTemplate> nebo <xref:System.Windows.Controls.ControlTemplate> k přizpůsobení jeho vzhledu.  Aby bylo možné vytvořit vlastní ovládací prvek, který podporuje šablony, je nutné odvozovat z <xref:System.Windows.Controls.Control> třídy nebo jedné z jeho odvozených tříd (kromě <xref:System.Windows.Controls.UserControl>).

#### <a name="benefits-of-deriving-from-usercontrol"></a>Výhody vyplývající z prvku UserControl

Zvažte odvození z <xref:System.Windows.Controls.UserControl>, pokud platí následující:

- Chcete sestavit svůj ovládací prvek podobně jako při sestavování aplikace.

- Váš ovládací prvek se skládá pouze ze stávajících součástí.

- Nemusíte podporovat složité přizpůsobení.

### <a name="deriving-from-control"></a>Odvození od ovládacího prvku

Odvození z třídy <xref:System.Windows.Controls.Control> je model používaný většinou existujících ovládacích prvků [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Když vytvoříte ovládací prvek, který dědí z třídy <xref:System.Windows.Controls.Control>, definujete jeho vzhled pomocí šablon. Díky tomu oddělíte provozní logiku od vizuální reprezentace. Můžete také zajistit odkázání uživatelského rozhraní a logiky pomocí příkazů a vazeb namísto událostí a zabránění odkazování na prvky v <xref:System.Windows.Controls.ControlTemplate>, kdykoli je to možné.  Pokud je uživatelské rozhraní a logika vašeho ovládacího prvku správně oddělitelné, uživatel vašeho ovládacího prvku může předefinovat <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku a přizpůsobit jeho vzhled. I když sestavíte vlastní <xref:System.Windows.Controls.Control> není tak jednoduché jako při sestavování <xref:System.Windows.Controls.UserControl>, vlastní <xref:System.Windows.Controls.Control> poskytuje největší flexibilitu.

#### <a name="benefits-of-deriving-from-control"></a>Výhody vyplývající z řízení

Zvažte odvození z <xref:System.Windows.Controls.Control> namísto použití <xref:System.Windows.Controls.UserControl> třídy, pokud platí některá z následujících možností:

- Chcete, aby byl vzhled ovládacího prvku přizpůsobitelný prostřednictvím <xref:System.Windows.Controls.ControlTemplate>.

- Chcete, aby ovládací prvek podporoval různé motivy.

### <a name="deriving-from-frameworkelement"></a>Odvození od prvku FrameworkElement

Ovládací prvky, které jsou odvozeny z <xref:System.Windows.Controls.UserControl> nebo <xref:System.Windows.Controls.Control>, spoléhají na vytváření existujících prvků. V mnoha scénářích se jedná o přijatelné řešení, protože libovolný objekt, který dědí z <xref:System.Windows.FrameworkElement>, může být v <xref:System.Windows.Controls.ControlTemplate>. Existují však situace, kdy vzhled ovládacího prvku vyžaduje více než funkce jednoduchého složení prvku. V těchto scénářích je ta součást na <xref:System.Windows.FrameworkElement> správnou volbou.

Existují dvě standardní metody pro vytváření komponent založených na <xref:System.Windows.FrameworkElement>: přímé vykreslování a vlastní kompozici prvků. Přímé vykreslování zahrnuje přepsání <xref:System.Windows.UIElement.OnRender%2A> metody <xref:System.Windows.FrameworkElement> a poskytování <xref:System.Windows.Media.DrawingContext> operací, které explicitně definují vizuály komponent. Toto je metoda, kterou používá <xref:System.Windows.Controls.Image> a <xref:System.Windows.Controls.Border>. Vlastní složení elementu zahrnuje použití objektů typu <xref:System.Windows.Media.Visual> k vytvoření vzhledu vaší komponenty. Příklad najdete v tématu [použití objektů DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track> je příkladem ovládacího prvku v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], který používá vlastní kompozici prvků. Je také možné kombinovat přímé vykreslování a vlastní kompozici prvků ve stejném ovládacím prvku.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>Výhody vyplývající z objektu FrameworkElement

Zvažte odvození z <xref:System.Windows.FrameworkElement>, pokud platí některá z následujících podmínek:

- Chcete mít přesnou kontrolu nad zobrazením ovládacího prvku nad rámec toho, co je k dispozici v jednoduchém složení prvku.

- Chcete definovat vzhled ovládacího prvku definováním vlastní logiky vykreslování.

- Chcete vytvářet existující prvky novými způsoby, které přesahují rámec toho, co je možné u <xref:System.Windows.Controls.UserControl> a <xref:System.Windows.Controls.Control>.

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>Základy vytváření ovládacích prvků

Jak je popsáno výše, jedna z nejúčinnějších funkcí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je možnost jít nad rámec nastavení základních vlastností ovládacího prvku, aby se změnil jeho vzhled a chování, ale stále není potřeba vytvořit vlastní ovládací prvek. K dispozici jsou možnosti stylů, datových vazeb a aktivačních funkcí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]m systémem vlastností a v systému událostí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Následující části popisují některé postupy, které byste měli dodržovat, bez ohledu na model, který použijete k vytvoření vlastního ovládacího prvku, aby uživatelé vlastního ovládacího prvku mohli tyto funkce používat stejně jako ovládací prvek, který je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

### <a name="use-dependency-properties"></a>Použít vlastnosti závislosti

Pokud je vlastnost vlastností závislosti, je možné provést následující akce:

- Nastavte vlastnost ve stylu.

- Navažte vlastnost na zdroj dat.

- Jako hodnotu vlastnosti použijte dynamický prostředek.

- Animovat vlastnost.

Pokud chcete, aby vlastnost vašeho ovládacího prvku podporovala tuto funkci, měli byste ji implementovat jako vlastnost závislosti. Následující příklad definuje vlastnost závislosti s názvem `Value` následujícím způsobem:

- Zadejte <xref:System.Windows.DependencyProperty> identifikátor s názvem `ValueProperty` jako pole `public` `static` `readonly`.

- Zaregistrujte název vlastnosti se systémem vlastností voláním <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>, abyste určili následující:

  - Název vlastnosti

  - Typ vlastnosti.

  - Typ, který vlastní vlastnost.

  - Metadata pro vlastnost Metadata obsahují výchozí hodnotu vlastnosti, <xref:System.Windows.CoerceValueCallback> a <xref:System.Windows.PropertyChangedCallback>.

- Definujte vlastnost obálky CLR s názvem `Value`, což je stejný název, který se používá k registraci vlastnosti závislosti, implementací `get` a `set`ch přístupových objektů vlastnosti. Všimněte si, že přístupové objekty `get` a `set` volají pouze <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A>. Doporučuje se, aby přistupující objekty vlastností závislosti neobsahovaly další logiku, protože klienti a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mohou obejít přístupové objekty a volat <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> přímo. Například pokud je vlastnost svázána se zdrojem dat, není volána vlastnost objektu `set` vlastnosti.  Namísto přidání další logiky do přístupových objektů Get a set použijte <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.CoerceValueCallback>a <xref:System.Windows.PropertyChangedCallback> delegáty k reakci na nebo kontrolu hodnoty, když se změní.  Další informace o těchto zpětných voláních naleznete v tématu [zpětná volání vlastností závislosti a ověřování](../advanced/dependency-property-callbacks-and-validation.md).

- Definujte metodu pro <xref:System.Windows.CoerceValueCallback> s názvem `CoerceValue`. `CoerceValue` zajistí, že `Value` je větší nebo rovno `MinValue` a menší nebo rovno `MaxValue`.

- Definujte metodu pro <xref:System.Windows.PropertyChangedCallback>s názvem `OnValueChanged`. `OnValueChanged` vytvoří objekt <xref:System.Windows.RoutedPropertyChangedEventArgs%601> a připraví k vyvolání události směrované `ValueChanged`. Směrované události jsou popsány v následující části.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Další informace najdete v tématu [vlastnosti vlastních závislostí](../advanced/custom-dependency-properties.md).

### <a name="use-routed-events"></a>Použít směrované události

Stejně jako vlastnosti závislosti rozšíří pojem vlastností CLR s dalšími funkcemi, směrované události rozšíří pojem standardních událostí CLR. Při vytváření nového ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je také vhodné implementovat událost jako směrovanou událost, protože směrovaná událost podporuje následující chování:

- Události lze zpracovat v nadřazeném více ovládacích prvků. Pokud je událost probublávání události, může se jedna nadřazená položka ve stromu elementu přihlásit k odběru události. Autoři aplikací potom mohou použít jednu obslužnou rutinu k reakci na událost více ovládacích prvků. Například pokud je váš ovládací prvek součástí každé položky v <xref:System.Windows.Controls.ListBox> (protože je součástí <xref:System.Windows.DataTemplate>), vývojář aplikace může definovat obslužnou rutinu události pro událost ovládacího prvku v <xref:System.Windows.Controls.ListBox>. Pokaždé, když dojde k události v jakémkoli ovládacím prvku, je volána obslužná rutina události.

- Směrované události lze použít v <xref:System.Windows.EventSetter>, což vývojářům aplikací umožňuje určit obslužnou rutinu události ve stylu.

- Směrované události lze použít v <xref:System.Windows.EventTrigger>, což je užitečné pro animování vlastností pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Další informace najdete v tématu [Přehled animací](../graphics-multimedia/animation-overview.md).

Následující příklad definuje směrnou událost pomocí následujícího postupu:

- Zadejte <xref:System.Windows.RoutedEvent> identifikátor s názvem `ValueChangedEvent` jako pole `public` `static` `readonly`.

- Zaregistrujte směrovanou událost voláním metody <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType>. Příklad určuje následující informace při volání <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:

  - Název události je `ValueChanged`.

  - Strategie směrování je <xref:System.Windows.RoutingStrategy.Bubble>, což znamená, že je nejprve volána obslužná rutina události na zdroji (objekt, který vyvolává událost), a poté obslužné rutiny události v nadřazených prvcích zdroje jsou volány po úspěchu, počínaje obslužnou rutinou události na nejbližším nadřazený element.

  - Typ obslužné rutiny události je <xref:System.Windows.RoutedPropertyChangedEventHandler%601>vytvořený pomocí typu <xref:System.Decimal>.

  - Vlastnící typ události je `NumericUpDown`.

- Deklarace veřejné události s názvem `ValueChanged` a zahrnuje deklarace přistupující k události. Příklad volá <xref:System.Windows.UIElement.AddHandler%2A> v deklaraci přístupového objektu `add` a <xref:System.Windows.UIElement.RemoveHandler%2A> v deklaraci přístupového objektu `remove` pro použití služby Event [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

- Vytvořte chráněnou virtuální metodu s názvem `OnValueChanged`, která vyvolá událost `ValueChanged`.

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Další informace najdete v tématu [Přehled směrovaných událostí](../advanced/routed-events-overview.md) a [Vytvoření vlastní směrované události](../advanced/how-to-create-a-custom-routed-event.md).

### <a name="use-binding"></a>Použití vazby

Chcete-li oddělit uživatelské rozhraní vašeho ovládacího prvku od jeho logiky, zvažte použití datové vazby. To je obzvláště důležité, pokud definujete vzhled ovládacího prvku pomocí <xref:System.Windows.Controls.ControlTemplate>. Pokud používáte datovou vazbu, může být možné eliminovat potřebu odkazů na konkrétní části uživatelského rozhraní z kódu. Je vhodné vyhnout se odkazování na prvky, které jsou v <xref:System.Windows.Controls.ControlTemplate>, protože když kód odkazuje na elementy, které jsou v <xref:System.Windows.Controls.ControlTemplate> a <xref:System.Windows.Controls.ControlTemplate> je změněn, odkazový element musí být zahrnut do nového <xref:System.Windows.Controls.ControlTemplate>.

Následující příklad aktualizuje <xref:System.Windows.Controls.TextBlock> ovládacího prvku `NumericUpDown`, přiřadí mu název a odkazuje na textové pole podle názvu v kódu.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

Následující příklad používá vazbu k tomu, aby provede stejnou věc.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Další informace o datové vazbě najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).

### <a name="design-for-designers"></a>Návrh pro návrháře

Chcete-li získat podporu pro vlastní ovládací prvky WPF v Návrháři WPF pro Visual Studio (například úpravy vlastností pomocí okno Vlastnosti), postupujte podle těchto pokynů.  Další informace o vývoji pro návrháře WPF naleznete [v tématu Design XAML v aplikaci Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

#### <a name="dependency-properties"></a>Vlastnosti závislosti

Ujistěte se, že implementujete přistupující objekty CLR `get` a `set`, jak je popsáno výše v části "použití vlastností závislosti". Návrháři mohou použít obálku k detekci přítomnosti vlastnosti závislosti, ale například [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a klientů ovládacího prvku, nejsou při získávání nebo nastavování vlastnosti vyžadovány.

#### <a name="attached-properties"></a>Přidružené vlastnosti

K vlastním ovládacím prvkům byste měli implementovat připojené vlastnosti pomocí následujících pokynů:

- Mít `public` `static` `readonly` <xref:System.Windows.DependencyProperty> formuláře *PropertyName*`Property`, který byl vytvořen pomocí metody <xref:System.Windows.DependencyProperty.RegisterAttached%2A>. Název vlastnosti, která je předána <xref:System.Windows.DependencyProperty.RegisterAttached%2A> musí odpovídat *PropertyName*.

- Implementujte dvojici `public` `static` metody CLR s názvem `Set`*PropertyName* a `Get`*PropertyName*. Obě metody by měly přijmout třídu odvozenou od <xref:System.Windows.DependencyProperty> jako jejich první argument. Metoda `Set`*PropertyName* také přijímá argument, jehož typ odpovídá zaregistrovanému datovému typu pro vlastnost. Metoda `Get`*PropertyName* by měla vracet hodnotu stejného typu. Pokud chybí metoda `Set`*PropertyName* , je vlastnost označena jen pro čtení.

- `Set` *PropertyName* a `Get`*PropertyName* musí směrovat přímo do <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A>ch metod v objektu Target Dependency (v uvedeném pořadí). Návrháři mohou přistupovat k vlastnosti připojené voláním prostřednictvím obálky metody nebo přímým voláním cílového objektu závislosti.

Další informace o připojených vlastnostech najdete v tématu [Přehled připojených vlastností](../advanced/attached-properties-overview.md).

### <a name="define-and-use-shared-resources"></a>Definování a použití sdílených prostředků

Můžete zahrnout svůj ovládací prvek do stejného sestavení jako aplikaci nebo můžete zabalit ovládací prvek v samostatném sestavení, které lze použít ve více aplikacích. Ve většině případů se informace popsané v tomto tématu vztahují bez ohledu na metodu, kterou používáte.  Je však potřeba poznamenat jednu rozdílovou hodnotu.  Po vložení ovládacího prvku do stejného sestavení jako aplikace můžete do souboru App. XAML přidat globální prostředky. Sestavení, které obsahuje pouze ovládací prvky, však nemá přidružený objekt <xref:System.Windows.Application>, takže soubor App. XAML není k dispozici.

Když aplikace vyhledá prostředek, prohledá tři úrovně v tomto pořadí:

1. Úroveň elementu.

   Systém se spustí s prvkem, který odkazuje na prostředek, a poté prohledá prostředky logického nadřazeného objektu a tak dále, dokud není dosaženo kořenového prvku.

2. Úroveň aplikace.

   Prostředky definované objektem <xref:System.Windows.Application>.

3. Úroveň motivu.

   Slovníky na úrovni motivu jsou uloženy v podsložce s názvem themes.  Soubory ve složce Themes odpovídají motivům.  Například můžete mít Aero. NormalColor. XAML, Luna. NormalColor. XAML, Royale. NormalColor. XAML a tak dále.  Můžete mít také soubor s názvem Generic. XAML.  Když systém vyhledá prostředek na úrovni motivů, nejprve ho vyhledá v souboru specifickém pro motiv a pak ho vyhledá v souboru Generic. XAML.

Když je ovládací prvek v sestavení, které je oddělené od aplikace, je nutné umístit globální prostředky na úrovni prvku nebo na úrovni motivu. Obě metody mají své výhody.

#### <a name="defining-resources-at-the-element-level"></a>Definování prostředků na úrovni elementu

Sdílené prostředky můžete definovat na úrovni elementu vytvořením vlastního slovníku prostředků a jeho sloučením do slovníku prostředků vašeho ovládacího prvku.  Když použijete tuto metodu, můžete si pojmenovat soubor prostředků cokoli, co potřebujete, a může být ve stejné složce jako vaše ovládací prvky. Prostředky na úrovni elementu můžou jako klíče používat taky jednoduché řetězce. Následující příklad vytvoří soubor prostředků <xref:System.Windows.Media.LinearGradientBrush> s názvem Dictionary1. XAML.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Po definování slovníku je potřeba ho sloučit se slovníkem prostředků vašeho ovládacího prvku.  Můžete to provést pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kódu.

Následující příklad sloučí slovník prostředků pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

Nevýhodou tohoto přístupu je, že se objekt <xref:System.Windows.ResourceDictionary> vytvoří pokaždé, když na něj odkazujete.  Například pokud máte v knihovně 10 vlastních ovládacích prvků a sloučíte sdílené slovníky prostředků pro každý ovládací prvek pomocí jazyka XAML, vytvoříte 10 identických <xref:System.Windows.ResourceDictionary> objektů.  K tomu je možné se vyhnout vytvořením statické třídy, která sloučí prostředky v kódu a vrátí výsledný <xref:System.Windows.ResourceDictionary>.

Následující příklad vytvoří třídu, která vrací sdílený <xref:System.Windows.ResourceDictionary>.

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

Následující příklad sloučí sdílený prostředek s prostředky vlastního ovládacího prvku v konstruktoru ovládacího prvku před voláním `InitializeComponent`.  Vzhledem k tomu, že `SharedDictionaryManager.SharedDictionary` je statická vlastnost, je <xref:System.Windows.ResourceDictionary> vytvořena pouze jednou. Vzhledem k tomu, že byl slovník prostředků sloučen před zavoláním `InitializeComponent`, prostředky jsou k dispozici pro ovládací prvek v jeho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru.

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Definování prostředků na úrovni motivu

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] slouží k vytváření prostředků pro různé motivy systému Windows.  Jako autor ovládacího prvku můžete definovat prostředek pro konkrétní motiv, který změní vzhled ovládacího prvku v závislosti na tom, jaký motiv se používá. Například vzhled <xref:System.Windows.Controls.Button> v motivu Windows Classic (výchozí motiv pro systém Windows 2000) se liší od <xref:System.Windows.Controls.Button> v motivu Windows Luna (výchozí motiv pro systém Windows XP), protože <xref:System.Windows.Controls.Button> používá pro každý motiv jiný <xref:System.Windows.Controls.ControlTemplate>.

Prostředky, které jsou specifické pro motiv, jsou uchovávány ve slovníku prostředků s určitým názvem souboru. Tyto soubory musí být ve složce s názvem `Themes`, která je podsložkou složky, která obsahuje ovládací prvek. V následující tabulce jsou uvedeny soubory slovníku prostředků a motiv, který je k jednotlivým souborům přidružen:

|Název souboru slovníku prostředků|Motiv Windows|
|-----------------------------------|-------------------|
|`Classic.xaml`|Klasické systémy Windows 9x/2000 – Prohlédněte si Windows XP|
|`Luna.NormalColor.xaml`|Výchozí modrý motiv v systému Windows XP|
|`Luna.Homestead.xaml`|Motiv olivového oleje v systému Windows XP|
|`Luna.Metallic.xaml`|Motiv stříbrného systému Windows XP|
|`Royale.NormalColor.xaml`|Výchozí motiv v systému Windows XP Media Center Edition|
|`Aero.NormalColor.xaml`|Výchozí motiv v systému Windows Vista|

Nemusíte definovat prostředek pro každý motiv. Pokud prostředek není definován pro určitý motiv, ovládací prvek zkontroluje `Classic.xaml` pro daný prostředek. Pokud prostředek není definován v souboru, který odpovídá aktuálnímu motivu nebo v `Classic.xaml`, ovládací prvek používá obecný prostředek, který je v souboru slovníku prostředků s názvem `generic.xaml`.  Soubor `generic.xaml` se nachází ve stejné složce jako soubory slovníku prostředků specifické pro motiv. Přestože `generic.xaml` neodpovídá konkrétnímu motivu systému Windows, je stále slovník na úrovni motivu.

Vlastní [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) ovládací prvek nebo [Visual Basicec](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) NumericUpDown s podporou motivů a automatizace uživatelského rozhraní obsahuje dva slovníky prostředků pro ovládací prvek `NumericUpDown`: jeden je v souboru Generic. XAML a druhý je v Luna. NormalColor. XAML. 

Při vložení <xref:System.Windows.Controls.ControlTemplate> do některého ze souborů slovníku prostředků specifických pro motiv, je nutné vytvořit statický konstruktor pro ovládací prvek a volat metodu <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> na <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, jak je znázorněno v následujícím příkladu.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Definování a odkazování klíčů pro prostředky motivů

Při definování prostředku na úrovni prvku můžete jako svůj klíč přiřadit řetězec a přistupovat k prostředku prostřednictvím řetězce. Při definování prostředku na úrovni motivu musíte jako klíč použít <xref:System.Windows.ComponentResourceKey>.  Následující příklad definuje prostředek v souboru Generic. XAML.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

Následující příklad odkazuje na prostředek zadáním <xref:System.Windows.ComponentResourceKey> jako klíče.

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Určení umístění prostředků motivu

Chcete-li najít prostředky pro ovládací prvek, hostující aplikace musí znát, že sestavení obsahuje prostředky specifické pro ovládací prvek. To lze provést přidáním <xref:System.Windows.ThemeInfoAttribute> do sestavení, které obsahuje ovládací prvek. <xref:System.Windows.ThemeInfoAttribute> má vlastnost <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>, která určuje umístění obecných prostředků a vlastnost <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>, která určuje umístění prostředků specifických pro motiv.

Následující příklad nastaví <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> a vlastnosti <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> na <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>, chcete-li určit, že obecné a specifické prostředky v rámci motivů jsou ve stejném sestavení jako ovládací prvek.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Viz také:

- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Sbalení URI v technologii WPF](../app-development/pack-uris-in-wpf.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
