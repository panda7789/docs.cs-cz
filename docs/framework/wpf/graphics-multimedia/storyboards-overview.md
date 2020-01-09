---
title: Přehled scénářů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 5c058dbaf2ae209a198a8299790d4002447ac443
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559687"
---
# <a name="storyboards-overview"></a>Přehled scénářů

Toto téma ukazuje, jak použít objekty <xref:System.Windows.Media.Animation.Storyboard> k uspořádání a použití animací. Popisuje, jak interaktivně manipulovat s <xref:System.Windows.Media.Animation.Storyboard> objekty a popisuje syntaxi cílení na nepřímých vlastností.

## <a name="prerequisites"></a>Požadavky

Pro pochopení tohoto tématu byste měli být obeznámeni s různými typy animací a jejich základními funkcemi. Úvod do animace najdete v tématu [Přehled animace](animation-overview.md). Měli byste také zjistit, jak používat připojené vlastnosti. Další informace o připojených vlastnostech naleznete v tématu [Přehled připojených vlastností](../advanced/attached-properties-overview.md).

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>Co je scénář?

Animace nejsou jediným užitečným typem časové osy. K dispozici jsou další třídy časové osy, které vám pomůžou organizovat sady časových os a aplikovat časové osy na vlastnosti. Časové osy kontejneru jsou odvozeny od třídy <xref:System.Windows.Media.Animation.TimelineGroup> a zahrnují <xref:System.Windows.Media.Animation.ParallelTimeline> a <xref:System.Windows.Media.Animation.Storyboard>.

<xref:System.Windows.Media.Animation.Storyboard> je typ časové osy kontejneru, který poskytuje informace o cílení na časové osy, které obsahuje. Scénář může obsahovat jakýkoli typ <xref:System.Windows.Media.Animation.Timeline>, včetně dalších časových os a animací. <xref:System.Windows.Media.Animation.Storyboard> objekty vám umožní kombinovat časové osy, které ovlivňují nejrůznější objekty a vlastnosti, do jednoho stromu časové osy, což usnadňuje uspořádání a kontrolu složitých chování časování. Předpokládejme například, že chcete tlačítko, které provádí tyto tři věci.

- Zvětšení a změna barvy, když uživatel vybere tlačítko

- Zmenšit a po kliknutí přejít zpátky na původní velikost

- Zmenšení a rozzvolna od 50 procent neprůhlednosti, když se deaktivuje.

V takovém případě máte více sad animací, které se vztahují na stejný objekt a chcete je přehrát v různých časech, závisí na stavu tlačítka. <xref:System.Windows.Media.Animation.Storyboard> objekty umožňují organizovat animace a aplikovat je ve skupinách na jeden nebo více objektů.

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>Kde můžete použít scénář?

<xref:System.Windows.Media.Animation.Storyboard> lze použít k animaci vlastností závislosti animovaných tříd (pro další informace o tom, co je třída animována, přečtěte si [Přehled animace](animation-overview.md)). Jelikož scénář je však funkce na úrovni architektury, objekt musí patřit do <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>.

Můžete například použít <xref:System.Windows.Media.Animation.Storyboard> k následujícím akcím:

- Animace <xref:System.Windows.Media.SolidColorBrush> (nerámec elementu), který vykreslí pozadí tlačítka (typ <xref:System.Windows.FrameworkElement>),

- Animace <xref:System.Windows.Media.SolidColorBrush> (nerámec elementu), který vykreslí výplň <xref:System.Windows.Media.GeometryDrawing> (element non-Framework) zobrazeného pomocí <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).

- V kódu můžete animovat <xref:System.Windows.Media.SolidColorBrush> deklarované třídou, která obsahuje také <xref:System.Windows.FrameworkElement>, pokud <xref:System.Windows.Media.SolidColorBrush> zaregistrovali název s tímto <xref:System.Windows.FrameworkElement>.

Nemůžete však použít <xref:System.Windows.Media.Animation.Storyboard> k animaci <xref:System.Windows.Media.SolidColorBrush>, která nezaregistrovala svůj název pomocí <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>nebo nebyla použita k nastavení vlastnosti <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>.

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>Postup použití animací ve scénáři

Pokud chcete použít <xref:System.Windows.Media.Animation.Storyboard> k uspořádání a používání animací, přidejte animace jako podřízené časové osy <xref:System.Windows.Media.Animation.Storyboard>. Třída <xref:System.Windows.Media.Animation.Storyboard> poskytuje <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> připojené vlastnosti. Tyto vlastnosti lze nastavit na animaci pro určení jejího cílového objektu a vlastnosti.

Chcete-li použít animace na jejich cíle, zahajte <xref:System.Windows.Media.Animation.Storyboard> pomocí akce triggeru nebo metody. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]použijete objekt <xref:System.Windows.Media.Animation.BeginStoryboard> s <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>nebo <xref:System.Windows.DataTrigger>. V kódu lze také použít metodu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.

V následující tabulce jsou uvedena různá místa, kde je každá <xref:System.Windows.Media.Animation.Storyboard>a, která začíná technikou, je podporována: dle instance, stylu, šablony ovládacího prvku a šablony dat. "Per-instance" odkazuje na techniku použití animace nebo scénáře přímo na instance objektu, nikoli ve stylu, šabloně ovládacího prvku nebo šabloně dat.

|Scénář se začal používat...|Podle instance|Styl|Šablona ovládacího prvku|Šablona dat|Příklad|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.EventTrigger>|Ano|Ano|Ano|Ano|[Animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard> a vlastnost <xref:System.Windows.Trigger>|Ne|Ano|Ano|Ano|[Spuštění animace při změně hodnoty vlastnosti](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.DataTrigger>|Ne|Ano|Ano|Ano|[Postupy: spuštění animace při změně dat](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|Metoda <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Ano|Ne|Ne|Ne|[Animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md)|

Následující příklad používá <xref:System.Windows.Media.Animation.Storyboard> k animaci <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle>ho prvku a <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush>, který se používá k malování <xref:System.Windows.Shapes.Rectangle>.

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

Následující části popisují <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojené vlastnosti podrobněji.

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Cílení elementů architektury, prvků obsahu architektury a Zablokovatelné

Výše zmíněná část uvádí, že pro animaci, která má najít cíl, musí znát název cíle a vlastnost, která se má animovat. Určení vlastnosti pro animaci je rovné: jednoduše nastavte <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> s názvem vlastnosti, která se má animovat.  Název objektu, jehož vlastnost chcete animovat, určíte nastavením vlastnosti <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> u animace.

Aby vlastnost <xref:System.Windows.Setter.TargetName%2A> fungovala, musí mít cílový objekt název. Přiřazení názvu <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se liší od přiřazení názvu k <xref:System.Windows.Freezable> objektu.

Prvky rozhraní jsou třídy, které dědí z třídy <xref:System.Windows.FrameworkElement>. Příklady prvků rozhraní zahrnují <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>a <xref:System.Windows.Shapes.Rectangle>. V podstatě jsou k disprvcích všechny okna, panely a ovládací prvky. Prvky obsahu architektury jsou třídy, které dědí z třídy <xref:System.Windows.FrameworkContentElement>. Příklady prvků obsahu architektury zahrnují <xref:System.Windows.Documents.FlowDocument> a <xref:System.Windows.Documents.Paragraph>. Pokud si nejste jistí, zda je typ prvkem architektury nebo element obsahu architektury, zkontrolujte, zda má vlastnost název. V takovém případě se pravděpodobně jedná o prvek rozhraní nebo prvek obsahu architektury. Chcete-li si být jisti, podívejte se do části Hierarchie dědičnosti v jeho typu stránky.

Chcete-li povolit cílení prvku rozhraní nebo prvku obsahu architektury v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nastavte jeho vlastnost <xref:System.Windows.FrameworkElement.Name%2A>. V kódu je také nutné použít metodu <xref:System.Windows.NameScope.RegisterName%2A> k registraci názvu elementu pomocí elementu, pro který jste vytvořili <xref:System.Windows.NameScope>.

Následující příklad pořízený z předchozího příkladu přiřadí název `MyRectangle` <xref:System.Windows.Shapes.Rectangle>, typ <xref:System.Windows.FrameworkElement>.

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

Po názvu můžete animovat vlastnost tohoto prvku.

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

<xref:System.Windows.Freezable> typy jsou třídy, které dědí z třídy <xref:System.Windows.Freezable>. Příklady <xref:System.Windows.Freezable> zahrnují <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>a <xref:System.Windows.Media.GradientStop>.

Chcete-li povolit cílení <xref:System.Windows.Freezable> animací v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte [direktivu x:Name](../../../desktop-wpf/xaml-services/xname-directive.md) k přiřazení názvu. V kódu pomocí metody <xref:System.Windows.NameScope.RegisterName%2A> zaregistrujete svůj název s prvkem, pro který jste vytvořili <xref:System.Windows.NameScope>.

Následující příklad přiřadí název objektu <xref:System.Windows.Freezable>.

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

Objekt pak může být cílem animace.

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

<xref:System.Windows.Media.Animation.Storyboard> objekty používají obory názvů k překladu vlastnosti <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>. Další informace o oborech názvů WPF naleznete v tématu [WPF XAML obory názvů WPF](../advanced/wpf-xaml-namescopes.md). Pokud je vlastnost <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> vynechána, animace cílí na prvek, ve kterém je definován, nebo v případě stylů, elementu style.

Někdy je možné, že název nelze přiřadit objektu <xref:System.Windows.Freezable>. Pokud je například deklarace <xref:System.Windows.Freezable> deklarována jako prostředek nebo použita k nastavení hodnoty vlastnosti ve stylu, nemůže se mu předávat název. Vzhledem k tomu, že nemá název, nejde na něj cílit přímo, ale dá se cílit nepřímo. Následující části popisují způsob použití nepřímých cílů.

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>Nepřímý cíl

Existují situace, kdy <xref:System.Windows.Freezable> nemůže být cílen přímo pomocí animace, například když je <xref:System.Windows.Freezable> deklarován jako prostředek nebo použit k nastavení hodnoty vlastnosti ve stylu. V takových případech, i když nemůžete cílit přímo na něj, můžete i nadále animovat objekt <xref:System.Windows.Freezable>. Namísto nastavení vlastnosti <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> s názvem <xref:System.Windows.Freezable>mu přidělíte název prvku, ke kterému <xref:System.Windows.Freezable> "patří". Například <xref:System.Windows.Media.SolidColorBrush> slouží k nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> prvku obdélníku, který patří do tohoto obdélníku. Pro animaci štětce byste nastavili <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> animace pomocí řetězce vlastností, který začíná vlastností elementu architektury nebo elementu obsahu architektury, <xref:System.Windows.Freezable> byl použit k nastavení a ukončení s vlastností <xref:System.Windows.Freezable> k animaci.

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

Všimněte si, že pokud je <xref:System.Windows.Freezable> zmrazena, vytvoří se klon a tato klona bude animována. Pokud k tomu dojde, vlastnost původního objektu <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> nadále vrací `false`, protože původní objekt není ve skutečnosti animovaný. Další informace o klonování naleznete v tématu [Freezable Objects Overview](../advanced/freezable-objects-overview.md).

Všimněte si také, že při použití cíle nepřímých vlastností je možné cílit na objekty, které neexistují. Můžete například předpokládat, že <xref:System.Windows.Controls.Control.Background%2A> konkrétního tlačítka bylo nastaveno s <xref:System.Windows.Media.SolidColorBrush> a pokusíte se animovat jeho barvu, když ve skutečnosti byl použit <xref:System.Windows.Media.LinearGradientBrush> k nastavení pozadí tlačítka. V těchto případech není vyvolána žádná výjimka; animace nemůže mít viditelný efekt, protože <xref:System.Windows.Media.LinearGradientBrush> nereaguje na změny vlastnosti <xref:System.Windows.Media.SolidColorBrush.Color%2A>.

Následující oddíly popisují nepřímou syntaxi cílení vlastnosti podrobněji.

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Nepřímo zaměřené na vlastnost Freezable v jazyce XAML

Chcete-li cílit na vlastnost Freezable v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte následující syntaxi.

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Where

- *ElementPropertyName* je vlastnost <xref:System.Windows.FrameworkElement>, kterou <xref:System.Windows.Freezable> použít k nastavení a

- *FreezablePropertyName* je vlastnost <xref:System.Windows.Freezable> k animaci.

Následující kód ukazuje, jak animovat <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> použit k nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> prvku Rectangle.

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

Někdy je potřeba cílit na Freezable obsažený v kolekci nebo poli.

Chcete-li cílit na Freezable obsažený v kolekci, použijte následující syntaxi cesty.

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

Kde *CollectionIndex* je index objektu ve svém poli nebo kolekci.

Předpokládejme například, že obdélník má <xref:System.Windows.Media.TransformGroup> prostředek aplikovaný na jeho vlastnost <xref:System.Windows.UIElement.RenderTransform%2A> a chcete animovat jednu z transformací, kterou obsahuje.

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

Následující kód ukazuje, jak animovat vlastnost <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform>, jak je znázorněno v předchozím příkladu.

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Nepřímo zaměřené na vlastnost Freezable v kódu

V kódu vytvoříte objekt <xref:System.Windows.PropertyPath>. Při vytváření <xref:System.Windows.PropertyPath>zadáte <xref:System.Windows.PropertyPath.Path%2A> a <xref:System.Windows.PropertyPath.PathParameters%2A>.

Chcete-li vytvořit <xref:System.Windows.PropertyPath.PathParameters%2A>, vytvořte pole typu <xref:System.Windows.DependencyProperty> obsahující seznam polí identifikátoru vlastnosti závislosti. Pole prvního identifikátoru je určena pro vlastnost <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, že je <xref:System.Windows.Freezable> použito k nastavení. Pole s dalším identifikátorem představuje vlastnost <xref:System.Windows.Freezable> k cíli. Můžete si ho představit jako řetězec vlastností, které propojí <xref:System.Windows.Freezable> s objektem <xref:System.Windows.FrameworkElement>.

Následuje příklad řetězu vlastností závislosti, který cílí na <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> použit k nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> prvku Rectangle.

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

Je také nutné zadat <xref:System.Windows.PropertyPath.Path%2A>. <xref:System.Windows.PropertyPath.Path%2A> je <xref:System.String>, který oznamuje <xref:System.Windows.PropertyPath.Path%2A>, jak interpretovat jeho <xref:System.Windows.PropertyPath.PathParameters%2A>. Používá následující syntaxi.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|

Where

- *OwnerPropertyArrayIndex* je index pole <xref:System.Windows.DependencyProperty>, které obsahuje identifikátor vlastnosti <xref:System.Windows.FrameworkElement> objektu, kterou <xref:System.Windows.Freezable> použít k nastavení a

- *FreezablePropertyArrayIndex* je index pole <xref:System.Windows.DependencyProperty>, které obsahuje identifikátor vlastnosti, kterou chcete cílit.

Následující příklad ukazuje <xref:System.Windows.PropertyPath.Path%2A>, která by mohla doprovázet <xref:System.Windows.PropertyPath.PathParameters%2A> definované v předchozím příkladu.

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

Následující příklad kombinuje kód v předchozích příkladech k animaci <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> použit k nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> prvku Rectangle.

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

Někdy je potřeba cílit na Freezable obsažený v kolekci nebo poli. Předpokládejme například, že obdélník má <xref:System.Windows.Media.TransformGroup> prostředek aplikovaný na jeho vlastnost <xref:System.Windows.UIElement.RenderTransform%2A> a chcete animovat jednu z transformací, kterou obsahuje.

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

Chcete-li cílit na <xref:System.Windows.Freezable> obsažené v kolekci, použijte následující syntaxi cesty.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|

Kde *CollectionIndex* je index objektu ve svém poli nebo kolekci.

Chcete-li cílit na vlastnost <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform>, druhá transformace v <xref:System.Windows.Media.TransformGroup>by používala následující <xref:System.Windows.PropertyPath.Path%2A> a <xref:System.Windows.PropertyPath.PathParameters%2A>.

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

Následující příklad ukazuje úplný kód pro animování <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform> obsažených v <xref:System.Windows.Media.TransformGroup>.

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Nepřímo cílící na Freezable jako výchozí bod

Předchozí části popisují, jak nepřímo cílit na <xref:System.Windows.Freezable> pomocí <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> a vytvořením řetězu vlastností pro <xref:System.Windows.Freezable> dílčí vlastnost. Můžete také použít <xref:System.Windows.Freezable> jako výchozí bod a nepřímo cílit na jednu z jejích <xref:System.Windows.Freezable> dílčích vlastností. Jedno další omezení platí při použití <xref:System.Windows.Freezable> jako výchozího bodu pro nepřímý cíl: počáteční <xref:System.Windows.Freezable> a každý <xref:System.Windows.Freezable> mezi ním a nepřímo cílenou dílčí vlastností nesmí být zmrazený.

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Interaktivní řízení scénáře v jazyce XAML

Pokud chcete začít scénář v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], použijte akci aktivace <xref:System.Windows.Media.Animation.BeginStoryboard>. <xref:System.Windows.Media.Animation.BeginStoryboard> distribuuje animace do objektů a vlastností, které animuje, a spustí scénář. (Podrobné informace o tomto procesu najdete v tématu [Přehled systému animace a časování](animation-and-timing-system-overview.md).) Pokud poskytnete <xref:System.Windows.Media.Animation.BeginStoryboard> název zadáním jeho vlastnosti <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>, provedete si ho jako ověřitelné scénář. Scénář pak můžete interaktivně kontrolovat po jeho spuštění. Níže je seznam přidaných akcí scénářů, které můžete použít s triggery událostí k řízení scénáře.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: pozastaví scénář.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: obnoví pozastavený scénář.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: mění rychlost scénáře.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: posune scénář do konce jeho období vyplňování, pokud má jednu z nich.

- <xref:System.Windows.Media.Animation.StopStoryboard>: zastaví scénář.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Odebere scénář.

V následujícím příkladu se pro interaktivní řízení scénáře používají ověřitelné akce scénářů.

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Interaktivní řízení scénáře pomocí kódu

Předchozí příklady ukázaly, jak animovat pomocí akcí triggeru. V kódu můžete také řídit scénář pomocí interaktivních metod třídy <xref:System.Windows.Media.Animation.Storyboard>. Aby <xref:System.Windows.Media.Animation.Storyboard> mohl být v kódu interaktivní, je nutné použít příslušné přetížení <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody scénáře a zadat `true`, aby jej bylo možné řídit. Další informace najdete na stránce <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>.

Následující seznam obsahuje metody, které lze použít k manipulaci s <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

Výhodou použití těchto metod je, že nemusíte vytvářet objekty <xref:System.Windows.Trigger> ani <xref:System.Windows.TriggerAction>; potřebujete pouze odkaz na ověřitelné <xref:System.Windows.Media.Animation.Storyboard>, které chcete manipulovat.

> [!NOTE]
> Všechny interaktivní akce prováděné na <xref:System.Windows.Media.Animation.Clock>, a proto se na <xref:System.Windows.Media.Animation.Storyboard> objeví na dalším taktu modulu časování, ke kterému dojde krátce před dalším vykreslováním. Například pokud použijete metodu <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> k přechodu na jiný bod v animaci, hodnota vlastnosti se nemění okamžitě, místo toho se hodnota změní při dalším taktu modulu časování.

Následující příklad ukazuje, jak použít a ovládat animace pomocí interaktivních metod třídy <xref:System.Windows.Media.Animation.Storyboard>.

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>Animace ve stylu

Můžete použít <xref:System.Windows.Media.Animation.Storyboard> objekty k definování animací v <xref:System.Windows.Style>. Animace s <xref:System.Windows.Media.Animation.Storyboard> v <xref:System.Windows.Style> je podobná použití <xref:System.Windows.Media.Animation.Storyboard> jinde, s následujícími třemi výjimkami:

- Nezadáváte <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; <xref:System.Windows.Media.Animation.Storyboard> vždy cílí na prvek, na který je <xref:System.Windows.Style> použit. Chcete-li cílit na <xref:System.Windows.Freezable> objekty, je nutné použít nepřímé cílení. Další informace o nepřímých cílících cíle najdete v části [nepřímé cílení](#pathsyntaxforchangeable) .

- Pro <xref:System.Windows.EventTrigger> nebo <xref:System.Windows.Trigger>nemůžete zadat <xref:System.Windows.EventTrigger.SourceName%2A>.

- K nastavení hodnot vlastností <xref:System.Windows.Media.Animation.Storyboard> nebo animace nelze použít dynamické odkazy na prostředky nebo výrazy vazby dat. To je proto, že vše uvnitř <xref:System.Windows.Style> musí být bezpečné pro přístup z více vláken a systém časování musí <xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard> objektů, aby byly bezpečné pro přístup z více vláken. <xref:System.Windows.Media.Animation.Storyboard> nelze zmrazit, pokud má nebo jeho podřízené časové osy obsahují odkazy na dynamické prostředky nebo výrazy datových vazeb. Další informace o zamrznutí a dalších funkcích <xref:System.Windows.Freezable> najdete v tématu [Přehled objektů Freezable](../advanced/freezable-objects-overview.md).

- V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nemůžete deklarovat obslužné rutiny událostí pro události <xref:System.Windows.Media.Animation.Storyboard> nebo animace.

Příklad znázorňující, jak definovat scénář ve stylu, naleznete v [animaci v příkladu stylu](how-to-animate-in-a-style.md) .

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>Animace v objektu ControlTemplate

Můžete použít <xref:System.Windows.Media.Animation.Storyboard> objekty k definování animací v <xref:System.Windows.Controls.ControlTemplate>. Animace s <xref:System.Windows.Media.Animation.Storyboard> v <xref:System.Windows.Controls.ControlTemplate> je podobná použití <xref:System.Windows.Media.Animation.Storyboard> jinde, s následujícími dvěma výjimkami:

- <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> může odkazovat pouze na podřízené objekty <xref:System.Windows.Controls.ControlTemplate>. Není-li zadán <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>, animace cílí na prvek, na který je <xref:System.Windows.Controls.ControlTemplate> použit.

- <xref:System.Windows.EventTrigger.SourceName%2A> pro <xref:System.Windows.EventTrigger> nebo <xref:System.Windows.Trigger> může odkazovat pouze na podřízené objekty <xref:System.Windows.Controls.ControlTemplate>.

- K nastavení hodnot vlastností <xref:System.Windows.Media.Animation.Storyboard> nebo animace nelze použít dynamické odkazy na prostředky nebo výrazy vazby dat. To je proto, že vše uvnitř <xref:System.Windows.Controls.ControlTemplate> musí být bezpečné pro přístup z více vláken a systém časování musí <xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard> objektů, aby byly bezpečné pro přístup z více vláken. <xref:System.Windows.Media.Animation.Storyboard> nelze zmrazit, pokud má nebo jeho podřízené časové osy obsahují odkazy na dynamické prostředky nebo výrazy datových vazeb. Další informace o zamrznutí a dalších funkcích <xref:System.Windows.Freezable> najdete v tématu [Přehled objektů Freezable](../advanced/freezable-objects-overview.md).

- V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nemůžete deklarovat obslužné rutiny událostí pro události <xref:System.Windows.Media.Animation.Storyboard> nebo animace.

Příklad znázorňující, jak definovat scénář v <xref:System.Windows.Controls.ControlTemplate>, naleznete v tématu [animace v ControlTemplate](how-to-animate-in-a-controltemplate.md) příkladu.

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>Animace při změně hodnoty vlastnosti

V šablonách stylů a ovládacích prvků lze pomocí objektů triggeru spustit scénář při změně vlastnosti. Příklady naleznete v tématu [triggering animace při změně hodnoty vlastnosti](how-to-trigger-an-animation-when-a-property-value-changes.md) a [animace v ControlTemplate](how-to-animate-in-a-controltemplate.md).

Animace aplikované vlastnostmi <xref:System.Windows.Trigger> objekty se chovají složitějším způsobem než <xref:System.Windows.EventTrigger> animace nebo animace spuštěné pomocí <xref:System.Windows.Media.Animation.Storyboard>ch metod.  Předávají s animacemi definovanými jinými <xref:System.Windows.Trigger> objekty, ale vytvářejí <xref:System.Windows.EventTrigger> a animace aktivované metodami.

## <a name="see-also"></a>Viz také:

- [Přehled animace](animation-overview.md)
- [Přehled způsobů animace vlastností](property-animation-techniques-overview.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
