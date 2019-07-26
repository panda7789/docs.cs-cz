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
ms.openlocfilehash: 3ea5519259ba2ee31bfd6bc25f6bedf1f1250799
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401543"
---
# <a name="control-authoring-overview"></a>Přehled řízeného vytváření

Rozšiřitelnost [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] modelu ovládacího prvku významně snižuje nutnost vytvoření nového ovládacího prvku. V některých případech však můžete stále potřebovat vytvořit vlastní ovládací prvek. Toto téma popisuje funkce, které minimalizují nutnost vytvořit vlastní ovládací prvek a různé modely vytváření ovládacích prvků v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]nástroji. Toto téma také ukazuje, jak vytvořit nový ovládací prvek.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Alternativy k psaní nového ovládacího prvku

Pokud jste si chtěli přizpůsobené prostředí získat z existujícího ovládacího prvku, bylo omezeno na změnu standardních vlastností ovládacího prvku, jako je barva pozadí, Šířka ohraničení a velikost písma. Pokud jste chtěli zvětšit vzhled nebo chování ovládacího prvku nad rámec těchto předdefinovaných parametrů, je nutné vytvořit nový ovládací prvek, obvykle děděním z existujícího ovládacího prvku a přepsáním metody zodpovědné za vykreslení ovládacího prvku.  I když je to stále možnost, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje přizpůsobit existující ovládací prvky pomocí modelu bohatých obsahu, stylů, šablon a triggerů. Následující seznam obsahuje příklady, jak lze tyto funkce použít k vytvoření vlastních a konzistentních prostředí, aniž byste museli vytvořit nový ovládací prvek.

- **Bohatě bohatý obsah.** Mnohé ze standardních [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků podporují bohatou obsah. Například vlastnost <xref:System.Windows.Controls.Button> Content typu je typu <xref:System.Object>, takže teoreticky <xref:System.Windows.Controls.Button>může být zobrazeno na.  Chcete-li zobrazit tlačítko <xref:System.Windows.Controls.TextBlock> s obrázkem a textem, můžete přidat obrázek a <xref:System.Windows.Controls.StackPanel> k <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnosti a přiřadit <xref:System.Windows.Controls.StackPanel> ji. Vzhledem k tomu, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky mohou zobrazovat vizuální prvky a libovolná data, je méně nutné vytvořit nový ovládací prvek nebo upravit existující ovládací prvek, aby podporoval složitou vizualizaci. Další informace o modelu obsahu pro <xref:System.Windows.Controls.Button> a dalších modelech obsahu v nástroji naleznete v [](wpf-content-model.md) [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tématu model obsahu WPF.

- **Nadpis.** <xref:System.Windows.Style> Je kolekce hodnot, které reprezentují vlastnosti ovládacího prvku. Pomocí stylů lze vytvořit opakovaně použitelná reprezentace požadovaného vzhledu a chování ovládacího prvku bez psaní nového ovládacího prvku. Předpokládejme například, že chcete, aby všechny <xref:System.Windows.Controls.TextBlock> ovládací prvky měly červené písmo Arial Font s velikostí písma 14. Můžete vytvořit styl jako prostředek a odpovídajícím způsobem nastavit odpovídající vlastnosti. Každý <xref:System.Windows.Controls.TextBlock> , který přidáte do vaší aplikace, bude mít stejný vzhled.

- **Datové šablony.** <xref:System.Windows.DataTemplate> Umožňuje přizpůsobit způsob zobrazení dat na ovládacím prvku. Například <xref:System.Windows.DataTemplate> lze použít k určení způsobu zobrazení dat <xref:System.Windows.Controls.ListBox>v.  Příklad najdete v tématu [Přehled šablonování dat](../data/data-templating-overview.md).  Kromě přizpůsobení vzhledu dat <xref:System.Windows.DataTemplate> může přidat prvky uživatelského rozhraní, které vám poskytnou značnou flexibilitu ve vlastních uživatelská rozhraní.  Například <xref:System.Windows.DataTemplate>pomocí můžete <xref:System.Windows.Controls.ComboBox> vytvořit, kde každá položka obsahuje zaškrtávací políčko.

- **Šablony ovládacích prvků.** Mnoho ovládacích prvků [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , které <xref:System.Windows.Controls.ControlTemplate> jsou používány k definování struktury a vzhledu ovládacího prvku, který odděluje vzhled ovládacího prvku od funkce ovládacího prvku. Vzhled ovládacího prvku můžete významně změnit tak, že ho převedete <xref:System.Windows.Controls.ControlTemplate>podle definice.  Předpokládejme například, že chcete ovládací prvek, který vypadá jako semafor. Tento ovládací prvek má jednoduché uživatelské rozhraní a funkce.  Ovládací prvek je tři kroužky, pouze jeden z nich lze rozsvítit současně. Po určité reflexi se můžete setkat s <xref:System.Windows.Controls.RadioButton> tím, že nabízí funkce pouze jednoho výběru, ale výchozí vzhled <xref:System.Windows.Controls.RadioButton> indikátoru nevypadá jako světla v semaforu.  Vzhledem k tomu, že <xref:System.Windows.Controls.ControlTemplate> používášablonuovládacíhoprvkukdefinováníjehovzhledu,jesnadnéhopředefinovattak,abyodpovídalpožadavkůmovládacíhoprvku,apoužítpřepínačektomu,abybylsemafor.<xref:System.Windows.Controls.RadioButton>

  > [!NOTE]
  > I když <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate> může používat, není v tomto příkladu dostačující. <xref:System.Windows.Controls.RadioButton>  <xref:System.Windows.DataTemplate> Definuje vzhled obsahu ovládacího prvku. V případě a <xref:System.Windows.Controls.RadioButton>se obsah zobrazuje napravo od kruhu, který označuje, <xref:System.Windows.Controls.RadioButton> zda je vybrána položka.  Přepínač v příkladu semaforu potřebuje jenom kruh, který může "světlo". Vzhledem k tomu <xref:System.Windows.Controls.RadioButton>, že je požadavek na zobrazení semaforu jiný než výchozí vzhled, je nutné <xref:System.Windows.Controls.ControlTemplate>předefinovat.  Obecně <xref:System.Windows.DataTemplate> se používá pro definování obsahu (nebo dat) ovládacího prvku <xref:System.Windows.Controls.ControlTemplate> a slouží k definování způsobu, jakým je ovládací prvek strukturovaný.

- **Zpráv.** <xref:System.Windows.Trigger> Umožňuje dynamicky měnit vzhled a chování ovládacího prvku bez vytvoření nového ovládacího prvku. Předpokládejme například, že máte v aplikaci <xref:System.Windows.Controls.ListBox> více ovládacích prvků a chcete, aby byly položky v <xref:System.Windows.Controls.ListBox> každém z nich tučné a červené při jejich výběru. První Instinct může být vytvořit třídu, která dědí z <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> přepsat metodu pro změnu vzhledu vybrané položky, ale lepším přístupem je přidat Trigger <xref:System.Windows.Controls.ListBoxItem> do stylu, který změní vzhled Vybraná položka. Aktivační událost umožňuje změnit hodnoty vlastností nebo provést akce na základě hodnoty vlastnosti. <xref:System.Windows.EventTrigger> Umožňuje provést akce, když dojde k události.

Další informace o stylech, šablonách a triggerech naleznete v tématu [stylování and šablonování](styling-and-templating.md).

Obecně platí, že pokud váš ovládací prvek zrcadlí funkčnost stávajícího ovládacího prvku, ale chcete, aby ovládací prvek vypadal jinak, měli byste nejprve zvážit, zda můžete použít kteroukoli z metod popsaných v této části, chcete-li změnit vzhled stávajícího ovládacího prvku.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Modely pro vytváření ovládacích prvků

Bohatě vytvořený model obsahu, styly, šablony a triggery minimalizují nutnost vytvoření nového ovládacího prvku. Pokud však potřebujete vytvořit nový ovládací prvek, je důležité pochopit různé modely vytváření ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nástroji. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje tři obecné modely pro vytvoření ovládacího prvku, z nichž každý nabízí různé sady funkcí a úrovně flexibility. Základní třídy pro tři modely jsou <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control>a <xref:System.Windows.FrameworkElement>.

### <a name="deriving-from-usercontrol"></a>Odvození od prvku UserControl

Nejjednodušší způsob, jak vytvořit ovládací prvek v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nástroji, je odvozovat z. <xref:System.Windows.Controls.UserControl> Při sestavování ovládacího prvku, který <xref:System.Windows.Controls.UserControl>dědí z, přidáte existující součásti <xref:System.Windows.Controls.UserControl>do, pojmenujte komponenty a referenční obslužné rutiny [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]událostí v. Pak můžete odkazovat na pojmenované elementy a definovat obslužné rutiny událostí v kódu. Tento model vývoje se velmi podobá modelu používanému pro vývoj aplikací v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

V případě, že je <xref:System.Windows.Controls.UserControl> správně sestaven, může využít výhody bohatě formátovaného obsahu, stylů a triggerů. Nicméně pokud váš ovládací prvek dědí z <xref:System.Windows.Controls.UserControl>, uživatelé, kteří používají ovládací prvek, nebudou moci <xref:System.Windows.DataTemplate> použít nebo <xref:System.Windows.Controls.ControlTemplate> k přizpůsobení jeho vzhledu.  Aby bylo možné vytvořit vlastní ovládací prvek <xref:System.Windows.Controls.Control> , který podporuje šablony, je nutné odvozovat z <xref:System.Windows.Controls.UserControl>třídy nebo jedné z jeho odvozených tříd (jiné než).

#### <a name="benefits-of-deriving-from-usercontrol"></a>Výhody vyplývající z prvku UserControl

Zvažte odvození z <xref:System.Windows.Controls.UserControl> následujících podmínek:

- Chcete sestavit svůj ovládací prvek podobně jako při sestavování aplikace.

- Váš ovládací prvek se skládá pouze ze stávajících součástí.

- Nemusíte podporovat složité přizpůsobení.

### <a name="deriving-from-control"></a>Odvození od ovládacího prvku

Odvození od <xref:System.Windows.Controls.Control> třídy je model používaný většinou z existujících [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků. Když vytvoříte ovládací prvek, který dědí z <xref:System.Windows.Controls.Control> třídy, definujete jeho vzhled pomocí šablon. Díky tomu oddělíte provozní logiku od vizuální reprezentace. Můžete také zajistit oddálení uživatelského rozhraní a logiky pomocí příkazů a vazeb namísto událostí a vyhnutí se odkazování na prvky, kdykoli <xref:System.Windows.Controls.ControlTemplate> je to možné.  Pokud je uživatelské rozhraní a logika vašeho ovládacího prvku správně oddělitelné, uživatel vašeho ovládacího prvku může předefinovat svůj ovládací prvek <xref:System.Windows.Controls.ControlTemplate> a přizpůsobit jeho vzhled. I když sestavování vlastního <xref:System.Windows.Controls.Control> není jednoduché jako sestavování a <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control> vlastní možnost poskytuje největší flexibilitu.

#### <a name="benefits-of-deriving-from-control"></a>Výhody vyplývající z řízení

Zvažte odvozování <xref:System.Windows.Controls.Control> namísto použití třídy, <xref:System.Windows.Controls.UserControl> pokud platí kterákoli z následujících možností:

- Chcete, aby byl vzhled ovládacího prvku přizpůsobitelný prostřednictvím <xref:System.Windows.Controls.ControlTemplate>.

- Chcete, aby ovládací prvek podporoval různé motivy.

### <a name="deriving-from-frameworkelement"></a>Odvození od prvku FrameworkElement

Ovládací prvky, které <xref:System.Windows.Controls.UserControl> jsou <xref:System.Windows.Controls.Control> odvozeny z nebo spoléhají na vytváření existujících prvků. Pro mnoho scénářů se jedná o přijatelné řešení, protože libovolný objekt, který dědí <xref:System.Windows.FrameworkElement> z, může být <xref:System.Windows.Controls.ControlTemplate>v. Existují však situace, kdy vzhled ovládacího prvku vyžaduje více než funkce jednoduchého složení prvku. V těchto scénářích je vhodná volba pro <xref:System.Windows.FrameworkElement> založení komponenty na.

Existují dvě standardní metody pro stavební <xref:System.Windows.FrameworkElement>komponenty: přímé vykreslování a vlastní kompozici prvků. Přímé vykreslování zahrnuje přepsání <xref:System.Windows.UIElement.OnRender%2A> <xref:System.Windows.FrameworkElement> metody a poskytování <xref:System.Windows.Media.DrawingContext> operací, které explicitně definují vizuály komponenty. Toto je metoda, kterou používá <xref:System.Windows.Controls.Image> a <xref:System.Windows.Controls.Border>. Vlastní složení elementu zahrnuje použití objektů typu <xref:System.Windows.Media.Visual> k vytvoření vzhledu vaší komponenty. Příklad najdete v tématu [použití objektů DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track>je příkladem ovládacího prvku v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , který používá vlastní kompozici prvků. Je také možné kombinovat přímé vykreslování a vlastní kompozici prvků ve stejném ovládacím prvku.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>Výhody vyplývající z objektu FrameworkElement

Zvažte odvození z <xref:System.Windows.FrameworkElement> , pokud platí některá z následujících podmínek:

- Chcete mít přesnou kontrolu nad zobrazením ovládacího prvku nad rámec toho, co je k dispozici v jednoduchém složení prvku.

- Chcete definovat vzhled ovládacího prvku definováním vlastní logiky vykreslování.

- Chcete vytvořit existující prvky novými způsoby, které přesahují rámec toho, co je možné s <xref:System.Windows.Controls.UserControl> a <xref:System.Windows.Controls.Control>.

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>Základy vytváření ovládacích prvků

Jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je popsáno výše, jedna z nejúčinnějších funkcí nástroje je schopnost přejít nad rámec nastavení základních vlastností ovládacího prvku, aby se změnil jeho vzhled a chování, ale stále není potřeba vytvořit vlastní ovládací prvek. K dispozici jsou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] možnosti stylů, datových vazeb a aktivačních funkcí v systému vlastností a v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému událostí. Následující části popisují některé postupy, které byste měli dodržovat, bez ohledu na model, který použijete k vytvoření vlastního ovládacího prvku, aby uživatelé vlastního ovládacího prvku mohli tyto funkce používat stejně jako ovládací prvek, který je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nástroje.

### <a name="use-dependency-properties"></a>Použít vlastnosti závislosti

Pokud je vlastnost vlastností závislosti, je možné provést následující akce:

- Nastavte vlastnost ve stylu.

- Navažte vlastnost na zdroj dat.

- Jako hodnotu vlastnosti použijte dynamický prostředek.

- Animovat vlastnost.

Pokud chcete, aby vlastnost vašeho ovládacího prvku podporovala tuto funkci, měli byste ji implementovat jako vlastnost závislosti. Následující příklad definuje vlastnost závislosti s názvem `Value` následujícím způsobem:

- `public` Definujteidentifikátors`readonly` názvem `ValueProperty` jako`static` pole. <xref:System.Windows.DependencyProperty>

- Zaregistrujte název vlastnosti se systémem vlastností zavoláním <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>metody, abyste určili následující:

  - Název vlastnosti

  - Typ vlastnosti.

  - Typ, který vlastní vlastnost.

  - Metadata pro vlastnost Metadata obsahují výchozí hodnotu vlastnosti, <xref:System.Windows.CoerceValueCallback> <xref:System.Windows.PropertyChangedCallback>a a.

- Definujte vlastnost obálky CLR s názvem `Value`, což je stejný název, který se používá k registraci vlastnosti závislosti, implementací `get` a `set` přístupových objektů vlastnosti. Všimněte si, `get` že `set` přístupovéobjekty<xref:System.Windows.DependencyObject.GetValue%2A> a jsou volány pouze v uvedenémpořadí.<xref:System.Windows.DependencyObject.SetValue%2A> Doporučuje se, aby přistupující objekty vlastností závislosti neobsahovaly další logiku, protože klienti a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mohou obejít přistupující objekty a volat <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> přímo. Například pokud je vlastnost svázána se zdrojem dat, `set` přístup k vlastnosti není volán.  Namísto přidání další logiky do přístupových objektů Get a set použijte <xref:System.Windows.ValidateValueCallback>delegáty, <xref:System.Windows.CoerceValueCallback>a <xref:System.Windows.PropertyChangedCallback> k reakci na nebo kontrolu hodnoty, když se změní.  Další informace o těchto zpětných voláních naleznete v tématu [zpětná volání vlastností závislosti a ověřování](../advanced/dependency-property-callbacks-and-validation.md).

- Definujte metodu pro <xref:System.Windows.CoerceValueCallback> pojmenovaný `CoerceValue`. `CoerceValue`zajistí, `Value` že je větší nebo `MinValue` rovno a `MaxValue`menší nebo rovno.

- Definujte metodu pro <xref:System.Windows.PropertyChangedCallback>, s názvem `OnValueChanged`. `OnValueChanged`Vytvoří objekt a připraví na `ValueChanged` vyvolání směrované události. <xref:System.Windows.RoutedPropertyChangedEventArgs%601> Směrované události jsou popsány v následující části.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Další informace najdete v tématu [vlastnosti vlastních závislostí](../advanced/custom-dependency-properties.md).

### <a name="use-routed-events"></a>Použít směrované události

Stejně jako vlastnosti závislosti rozšíří pojem vlastností CLR s dalšími funkcemi, směrované události rozšíří pojem standardních událostí CLR. Při vytváření nového [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku je také vhodné implementovat událost jako směrovanou událost, protože směrovaná událost podporuje následující chování:

- Události lze zpracovat v nadřazeném více ovládacích prvků. Pokud je událost probublávání události, může se jedna nadřazená položka ve stromu elementu přihlásit k odběru události. Autoři aplikací potom mohou použít jednu obslužnou rutinu k reakci na událost více ovládacích prvků. Například pokud je váš ovládací prvek součástí každé položky v <xref:System.Windows.Controls.ListBox> (protože je součástí <xref:System.Windows.DataTemplate>), může vývojář aplikace definovat obslužnou rutinu události pro událost <xref:System.Windows.Controls.ListBox>ovládacího prvku v. Pokaždé, když dojde k události v jakémkoli ovládacím prvku, je volána obslužná rutina události.

- Směrované události lze použít v <xref:System.Windows.EventSetter>, což umožňuje vývojářům aplikací určit obslužnou rutinu události ve stylu.

- Směrované události lze použít v <xref:System.Windows.EventTrigger>, což je užitečné pro animování vlastností pomocí. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Další informace najdete v tématu [Přehled animací](../graphics-multimedia/animation-overview.md).

Následující příklad definuje směrnou událost pomocí následujícího postupu:

- `public` Definujteidentifikátors`readonly` názvem `ValueChangedEvent` jako`static` pole. <xref:System.Windows.RoutedEvent>

- Zaregistrujte směrovanou událost voláním <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> metody. Příklad určuje následující informace při volání <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:

  - Název události je `ValueChanged`.

  - Strategie směrování je <xref:System.Windows.RoutingStrategy.Bubble>, což znamená, že obslužná rutina události na zdroji (objekt, který vyvolává událost) je volána jako první, a poté jsou obslužné rutiny události v nadřazených prvcích zdroje volány po úspěchu, počínaje obslužnou rutinou události na nejbližším nadřazený element.

  - Typ obslužné rutiny události je <xref:System.Windows.RoutedPropertyChangedEventHandler%601>vytvořen <xref:System.Decimal> pomocí typu.

  - Vlastnící typ události je `NumericUpDown`.

- Deklarace veřejné události s názvem `ValueChanged` a zahrnutí deklarací přistupujícího objektu na událost. <xref:System.Windows.UIElement.AddHandler%2A> Příklad volá <xref:System.Windows.UIElement.RemoveHandler%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deklaraci`remove` přistupujícího objektu a v deklaraci přistupujícího objektu pro použití služeb Event. `add`

- Vytvořte chráněnou virtuální metodu s názvem `OnValueChanged` , která `ValueChanged` událost vyvolá.

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Další informace najdete v tématu [Přehled směrovaných událostí](../advanced/routed-events-overview.md) a [Vytvoření vlastní směrované události](../advanced/how-to-create-a-custom-routed-event.md).

### <a name="use-binding"></a>Použití vazby

Chcete-li oddělit uživatelské rozhraní vašeho ovládacího prvku od jeho logiky, zvažte použití datové vazby. To je obzvláště důležité, pokud definujete vzhled ovládacího prvku pomocí <xref:System.Windows.Controls.ControlTemplate>. Pokud používáte datovou vazbu, může být možné eliminovat potřebu odkazů na konkrétní části uživatelského rozhraní z kódu. Je vhodné vyhnout se odkazování na prvky, které jsou v <xref:System.Windows.Controls.ControlTemplate> rozhraní, protože když kód odkazuje na elementy, které jsou <xref:System.Windows.Controls.ControlTemplate> v a <xref:System.Windows.Controls.ControlTemplate> , je nutné, aby byl odkazovaný element součástí nového <xref:System.Windows.Controls.ControlTemplate>.

Následující příklad aktualizuje <xref:System.Windows.Controls.TextBlock> `NumericUpDown` ovládací prvek, přiřadí mu název a odkazuje na textové pole podle názvu v kódu.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

Následující příklad používá vazbu k tomu, aby provede stejnou věc.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Další informace o datové vazbě najdete v tématu [Přehled datových vazeb](../data/data-binding-overview.md).

### <a name="design-for-designers"></a>Návrh pro návrháře

Chcete-li získat podporu pro vlastní ovládací prvky [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] WPF v nástroji (například pro úpravu vlastností pomocí okno Vlastnosti), postupujte podle těchto pokynů.  Další informace o vývoji pro [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]naleznete v tématu [design XAML v aplikaci Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).

#### <a name="dependency-properties"></a>Vlastnosti závislosti

Nezapomeňte implementovat CLR `get` a `set` přistupující objekty, jak je popsáno výše v části "použití vlastností závislosti". Návrháři mohou použít obálku k detekci přítomnosti vlastnosti závislosti, například jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a klientů ovládacího prvku, nejsou při získávání nebo nastavování vlastnosti vyžadovány.

#### <a name="attached-properties"></a>Přidružené vlastnosti

K vlastním ovládacím prvkům byste měli implementovat připojené vlastnosti pomocí následujících pokynů:

- `public`  Mítformu<xref:System.Windows.DependencyProperty.RegisterAttached%2A> PropertyName, která byla vytvořena pomocí metody.`Property` `static` `readonly` <xref:System.Windows.DependencyProperty> Název vlastnosti, která je předána <xref:System.Windows.DependencyProperty.RegisterAttached%2A> , musí odpovídat hodnotě *PropertyName*.

- Implementujte dvojici `public` `static` metod CLR s `Set`názvem *PropertyName* a `Get` *PropertyName*. Obě metody by měly přijmout třídu odvozenou <xref:System.Windows.DependencyProperty> z jako jejich první argument. Metoda propertyName také přijímá argument, jehož typ odpovídá zaregistrovanému datovému typu pro vlastnost.  `Set` Metoda propertyName by měla vracet hodnotu stejného typu.  `Get` Pokud metoda propertyName chybí, vlastnost je označena jen pro čtení.  `Set`

- `Set` Hodnoty PropertyName `Get`a *PropertyName* musí směrovat přímo <xref:System.Windows.DependencyObject.GetValue%2A> na metody <xref:System.Windows.DependencyObject.SetValue%2A> a cílového objektu závislosti v uvedeném pořadí. Návrháři mohou přistupovat k vlastnosti připojené voláním prostřednictvím obálky metody nebo přímým voláním cílového objektu závislosti.

Další informace o připojených vlastnostech najdete v tématu [Přehled připojených vlastností](../advanced/attached-properties-overview.md).

### <a name="define-and-use-shared-resources"></a>Definování a použití sdílených prostředků

Můžete zahrnout svůj ovládací prvek do stejného sestavení jako aplikaci nebo můžete zabalit ovládací prvek v samostatném sestavení, které lze použít ve více aplikacích. Ve většině případů se informace popsané v tomto tématu vztahují bez ohledu na metodu, kterou používáte.  Je však potřeba poznamenat jednu rozdílovou hodnotu.  Po vložení ovládacího prvku do stejného sestavení jako aplikace můžete do souboru App. XAML přidat globální prostředky. Sestavení, které obsahuje pouze ovládací prvky <xref:System.Windows.Application> , však nemá přidružený objekt, takže soubor App. XAML není k dispozici.

Když aplikace vyhledá prostředek, prohledá tři úrovně v tomto pořadí:

1. Úroveň elementu.

   Systém se spustí s prvkem, který odkazuje na prostředek, a poté prohledá prostředky logického nadřazeného objektu a tak dále, dokud není dosaženo kořenového prvku.

2. Úroveň aplikace.

   Prostředky definované <xref:System.Windows.Application> objektem.

3. Úroveň motivu.

   Slovníky na úrovni motivu jsou uloženy v podsložce s názvem themes.  Soubory ve složce Themes odpovídají motivům.  Například můžete mít Aero. NormalColor. XAML, Luna. NormalColor. XAML, Royale. NormalColor. XAML a tak dále.  Můžete mít také soubor s názvem Generic. XAML.  Když systém vyhledá prostředek na úrovni motivů, nejprve ho vyhledá v souboru specifickém pro motiv a pak ho vyhledá v souboru Generic. XAML.

Když je ovládací prvek v sestavení, které je oddělené od aplikace, je nutné umístit globální prostředky na úrovni prvku nebo na úrovni motivu. Obě metody mají své výhody.

#### <a name="defining-resources-at-the-element-level"></a>Definování prostředků na úrovni elementu

Sdílené prostředky můžete definovat na úrovni elementu vytvořením vlastního slovníku prostředků a jeho sloučením do slovníku prostředků vašeho ovládacího prvku.  Když použijete tuto metodu, můžete si pojmenovat soubor prostředků cokoli, co potřebujete, a může být ve stejné složce jako vaše ovládací prvky. Prostředky na úrovni elementu můžou jako klíče používat taky jednoduché řetězce. Následující příklad vytvoří <xref:System.Windows.Media.LinearGradientBrush> soubor prostředků s názvem Dictionary1. XAML.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Po definování slovníku je potřeba ho sloučit se slovníkem prostředků vašeho ovládacího prvku.  Můžete to provést pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kódu.

Následující příklad sloučí slovník prostředků pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

Nevýhodou tohoto přístupu je, že <xref:System.Windows.ResourceDictionary> objekt je vytvořen pokaždé, když na něj odkazujete.  Například pokud máte v knihovně 10 vlastních ovládacích prvků a sloučíte sdílené slovníky prostředků pro každý ovládací prvek pomocí jazyka XAML, vytvoříte 10 identických <xref:System.Windows.ResourceDictionary> objektů.  K tomu je možné se vyhnout vytvořením statické třídy, která sloučí prostředky v kódu a vrátí výsledek <xref:System.Windows.ResourceDictionary>.

Následující příklad vytvoří třídu, která vrací Shared <xref:System.Windows.ResourceDictionary>.

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

Následující příklad sloučí sdílený prostředek s prostředky vlastního ovládacího prvku v konstruktoru ovládacího prvku před voláním `InitializeComponent`.  Vzhledem k tomu <xref:System.Windows.ResourceDictionary> , že jestatickávlastnost,jevytvořenapouzejednou.`SharedDictionaryManager.SharedDictionary` Vzhledem k tomu, že byl slovník `InitializeComponent` prostředků sloučen před voláním, jsou prostředky k dispozici pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ovládací prvek v jeho souboru.

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Definování prostředků na úrovni motivu

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umožňuje vytvářet prostředky pro různé motivy systému Windows.  Jako autor ovládacího prvku můžete definovat prostředek pro konkrétní motiv, který změní vzhled ovládacího prvku v závislosti na tom, jaký motiv se používá. Například vzhled <xref:System.Windows.Controls.Button> v klasickém motivu systému Windows (výchozí motiv pro systém Windows 2000) se liší od a <xref:System.Windows.Controls.Button> v motivu Windows Luna (výchozí motiv pro systém Windows XP), <xref:System.Windows.Controls.Button> protože používá jinou <xref:System.Windows.Controls.ControlTemplate> pro každý motiv.

Prostředky, které jsou specifické pro motiv, jsou uchovávány ve slovníku prostředků s určitým názvem souboru. Tyto soubory musí být ve složce s názvem `Themes` , která je podsložkou složky, která obsahuje ovládací prvek. V následující tabulce jsou uvedeny soubory slovníku prostředků a motiv, který je k jednotlivým souborům přidružen:

|Název souboru slovníku prostředků|Motiv Windows|
|-----------------------------------|-------------------|
|`Classic.xaml`|Klasické systémy Windows 9x/2000 – Prohlédněte si Windows XP|
|`Luna.NormalColor.xaml`|Výchozí modrý motiv v systému Windows XP|
|`Luna.Homestead.xaml`|Motiv olivového oleje v systému Windows XP|
|`Luna.Metallic.xaml`|Motiv stříbrného systému Windows XP|
|`Royale.NormalColor.xaml`|Výchozí motiv v systému Windows XP Media Center Edition|
|`Aero.NormalColor.xaml`|Výchozí motiv v systému Windows Vista|

Nemusíte definovat prostředek pro každý motiv. Pokud prostředek není definován pro konkrétní motiv, ovládací prvek zkontroluje `Classic.xaml` prostředek. Pokud prostředek není definován v souboru, který odpovídá aktuálnímu motivu nebo v `Classic.xaml`, ovládací prvek používá obecný prostředek, který je v souboru slovníku prostředků s názvem. `generic.xaml`  `generic.xaml` Soubor je umístěn ve stejné složce jako soubory slovníku prostředků specifické pro motiv. I `generic.xaml` když neodpovídá konkrétnímu motivu systému Windows, je stále slovník na úrovni motivu.

[Vlastní ovládací prvek NumericUpDown s podporou pro automatizaci motivů a uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=160025) obsahuje dva `NumericUpDown` slovníky prostředků pro ovládací prvek: jeden je v souboru Generic. XAML a jeden je v Luna. NormalColor. XAML.  Můžete spustit aplikaci a přepnout mezi motivem stříbrného v systému Windows XP a jiným motivem a zobrazit rozdíl mezi těmito dvěma šablonami ovládacích prvků. (Pokud používáte systém Windows Vista, můžete přejmenovat Luna. NormalColor. XAML na Aero. NormalColor. XAML a přepínat mezi dvěma motivy, například Windows Classic a výchozím motivem pro systém Windows Vista.)

Když umístíte <xref:System.Windows.Controls.ControlTemplate> do některého ze souborů slovníku prostředků specifických pro motiv, je nutné vytvořit statický konstruktor pro váš ovládací prvek a <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> volat metodu na <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, jak je znázorněno v následujícím příkladu.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Definování a odkazování klíčů pro prostředky motivů

Při definování prostředku na úrovni prvku můžete jako svůj klíč přiřadit řetězec a přistupovat k prostředku prostřednictvím řetězce. Při definování prostředku na úrovni motivu je nutné použít <xref:System.Windows.ComponentResourceKey> jako klíč.  Následující příklad definuje prostředek v souboru Generic. XAML.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

Následující příklad odkazuje na prostředek <xref:System.Windows.ComponentResourceKey> zadáním jako klíč.

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Určení umístění prostředků motivu

Chcete-li najít prostředky pro ovládací prvek, hostující aplikace musí znát, že sestavení obsahuje prostředky specifické pro ovládací prvek. To lze provést přidáním <xref:System.Windows.ThemeInfoAttribute> do sestavení, které obsahuje ovládací prvek. Má vlastnost, která určuje umístění <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> obecných prostředků a vlastnost, která určuje umístění prostředků specifických pro motiv. <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> <xref:System.Windows.ThemeInfoAttribute>

V následujícím příkladu je nastavena <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> vlastnost <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> a vlastností <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>na, k určení, zda jsou prostředky obecné a specifické pro motiv ve stejném sestavení jako ovládací prvek.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Viz také:

- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Sbalení URI v technologii WPF](../app-development/pack-uris-in-wpf.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
