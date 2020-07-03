---
title: Přehled scénářů
desription: Organize and apply animations in storyboards. Use property-targeting syntax and combine timelines in Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 50f45953da3801bf73016c09b78a6a1b54878bc0
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853641"
---
# <a name="storyboards-overview"></a>Přehled scénářů

V tomto tématu se dozvíte, jak pomocí <xref:System.Windows.Media.Animation.Storyboard> objektů organizovat a používat animace. Popisuje, jak interaktivně manipulovat s <xref:System.Windows.Media.Animation.Storyboard> objekty a popisuje syntaxi cílení na nepřímých vlastností.

## <a name="prerequisites"></a>Požadavky

Pro pochopení tohoto tématu byste měli být obeznámeni s různými typy animací a jejich základními funkcemi. Úvod do animace najdete v tématu [Přehled animace](animation-overview.md). Měli byste také zjistit, jak používat připojené vlastnosti. Další informace o připojených vlastnostech naleznete v tématu [Přehled připojených vlastností](../advanced/attached-properties-overview.md).

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>Co je scénář?

Animace nejsou jediným užitečným typem časové osy. K dispozici jsou další třídy časové osy, které vám pomůžou organizovat sady časových os a aplikovat časové osy na vlastnosti. Časové osy kontejneru jsou odvozeny od <xref:System.Windows.Media.Animation.TimelineGroup> třídy a zahrnují <xref:System.Windows.Media.Animation.ParallelTimeline> a <xref:System.Windows.Media.Animation.Storyboard> .

<xref:System.Windows.Media.Animation.Storyboard>Je typ časové osy kontejneru, který poskytuje informace o cílení na časové osy, které obsahuje. Scénář může obsahovat jakýkoli typ <xref:System.Windows.Media.Animation.Timeline> , včetně dalších Timeline a animací kontejneru. <xref:System.Windows.Media.Animation.Storyboard>objekty umožňují kombinovat časové osy, které ovlivňují nejrůznější objekty a vlastnosti, do jednoho stromu časové osy, což usnadňuje uspořádání a kontrolu složitých chování časování. Předpokládejme například, že chcete tlačítko, které provádí tyto tři věci.

- Zvětšení a změna barvy, když uživatel vybere tlačítko

- Zmenšit a po kliknutí přejít zpátky na původní velikost

- Zmenšení a rozzvolna od 50 procent neprůhlednosti, když se deaktivuje.

V takovém případě máte více sad animací, které se vztahují na stejný objekt a chcete je přehrát v různých časech, závisí na stavu tlačítka. <xref:System.Windows.Media.Animation.Storyboard>objekty umožňují organizovat animace a aplikovat je ve skupinách na jeden nebo více objektů.

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>Kde můžete použít scénář?

<xref:System.Windows.Media.Animation.Storyboard>Lze použít k animaci vlastností závislosti animovaných tříd (pro další informace o tom, co je třída animována, viz [Přehled animace](animation-overview.md)). Vzhledem k tomu, že scénář je funkce na úrovni architektury, objekt musí patřit do a <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> .

Například můžete použít <xref:System.Windows.Media.Animation.Storyboard> k následujícím akcím:

- Animace <xref:System.Windows.Media.SolidColorBrush> (nerámec elementu), který vykreslí pozadí tlačítka (typu <xref:System.Windows.FrameworkElement> ),

- Animace <xref:System.Windows.Media.SolidColorBrush> (nerámec elementu), který vykreslí výplň <xref:System.Windows.Media.GeometryDrawing> (nerámec elementu) zobrazeného pomocí <xref:System.Windows.Controls.Image> ( <xref:System.Windows.FrameworkElement> ).

- V kódu můžete animovat <xref:System.Windows.Media.SolidColorBrush> deklaraci deklarované třídou, která také obsahuje <xref:System.Windows.FrameworkElement> , pokud je <xref:System.Windows.Media.SolidColorBrush> název zaregistrovaný <xref:System.Windows.FrameworkElement> .

Nemůžete však použít <xref:System.Windows.Media.Animation.Storyboard> k animaci <xref:System.Windows.Media.SolidColorBrush> , která neregistrovala svůj název pomocí <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> , nebo nebyla použita k nastavení vlastnosti <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> .

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>Postup použití animací ve scénáři

Chcete-li použít <xref:System.Windows.Media.Animation.Storyboard> k uspořádání a uplatnění animací, přidejte animace jako podřízené časové osy <xref:System.Windows.Media.Animation.Storyboard> . <xref:System.Windows.Media.Animation.Storyboard>Třída poskytuje <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> vlastnosti a připojené. Tyto vlastnosti lze nastavit na animaci pro určení jejího cílového objektu a vlastnosti.

Pokud chcete použít animace na jejich cíle, zahájíte <xref:System.Windows.Media.Animation.Storyboard> akci s triggerem nebo metodou. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použijte <xref:System.Windows.Media.Animation.BeginStoryboard> objekt s <xref:System.Windows.EventTrigger> , <xref:System.Windows.Trigger> nebo <xref:System.Windows.DataTrigger> . V kódu lze také použít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu.

V následující tabulce jsou uvedena různá místa, kde <xref:System.Windows.Media.Animation.Storyboard> jsou jednotlivé postupy zahájení podporovány: pro jednotlivé instance, styl, šablonu ovládacího prvku a šablonu dat. "Per-instance" odkazuje na techniku použití animace nebo scénáře přímo na instance objektu, nikoli ve stylu, šabloně ovládacího prvku nebo šabloně dat.

|Scénář se začal používat...|Podle instance|Styl|Šablona ovládacího prvku|Šablona dat|Příklad|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard>a<xref:System.Windows.EventTrigger>|Ano|Ano|Ano|Ano|[Animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>a vlastnost<xref:System.Windows.Trigger>|No|Ano|Ano|Ano|[Spuštění animace při změně hodnoty vlastnosti](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>a a<xref:System.Windows.DataTrigger>|No|Ano|Ano|Ano|[Postupy: spuštění animace při změně dat](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|Metoda <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Ano|No|No|No|[Animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md)|

V následujícím příkladu se používá <xref:System.Windows.Media.Animation.Storyboard> k animaci <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> prvku <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> , který je použit k malování <xref:System.Windows.Shapes.Rectangle> .

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

V následujících částech jsou podrobněji popsány <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojené vlastnosti.

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Cílení elementů architektury, prvků obsahu architektury a Zablokovatelné

Výše zmíněná část uvádí, že pro animaci, která má najít cíl, musí znát název cíle a vlastnost, která se má animovat. Určení vlastnosti, která má být animována, je přímá předána: jednoduše nastavte <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> s názvem vlastnosti, která se má animovat.  Zadejte název objektu, jehož vlastnost má být animována, nastavením <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> vlastnosti animace.

Aby tato <xref:System.Windows.Setter.TargetName%2A> vlastnost fungovala, musí mít cílový objekt název. Přiřazení názvu k <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se liší od přiřazení názvu k <xref:System.Windows.Freezable> objektu.

Prvky architektury jsou třídy, které dědí z <xref:System.Windows.FrameworkElement> třídy. Příklady prvků rozhraní zahrnují <xref:System.Windows.Window> , <xref:System.Windows.Controls.DockPanel> , <xref:System.Windows.Controls.Button> a <xref:System.Windows.Shapes.Rectangle> . V podstatě jsou k disprvcích všechny okna, panely a ovládací prvky. Prvky obsahu architektury jsou třídy, které dědí z <xref:System.Windows.FrameworkContentElement> třídy. Příklady prvků obsahu architektury zahrnují <xref:System.Windows.Documents.FlowDocument> a <xref:System.Windows.Documents.Paragraph> . Pokud si nejste jistí, zda je typ prvkem architektury nebo element obsahu architektury, zkontrolujte, zda má vlastnost název. V takovém případě se pravděpodobně jedná o prvek rozhraní nebo prvek obsahu architektury. Chcete-li si být jisti, podívejte se do části Hierarchie dědičnosti v jeho typu stránky.

Chcete-li povolit cílení prvku rozhraní nebo prvku obsahu architektury v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , nastavte jeho <xref:System.Windows.FrameworkElement.Name%2A> vlastnost. V kódu je také nutné použít <xref:System.Windows.NameScope.RegisterName%2A> metodu k registraci názvu elementu pomocí elementu, pro který jste vytvořili <xref:System.Windows.NameScope> .

Následující příklad pořízený z předchozího příkladu přiřadí název `MyRectangle` a <xref:System.Windows.Shapes.Rectangle> , typ <xref:System.Windows.FrameworkElement> .

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

Po názvu můžete animovat vlastnost tohoto prvku.

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

<xref:System.Windows.Freezable>typy jsou třídy, které dědí z <xref:System.Windows.Freezable> třídy. Příklady příkazů <xref:System.Windows.Freezable> include <xref:System.Windows.Media.SolidColorBrush> , <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.GradientStop> .

Chcete-li povolit cílení <xref:System.Windows.Freezable> pomocí animace v nástroji [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , použijte [direktivu x:Name](../../../desktop-wpf/xaml-services/xname-directive.md) k přiřazení názvu. V kódu použijte <xref:System.Windows.NameScope.RegisterName%2A> metodu k registraci jejího názvu s prvkem, pro který jste vytvořili <xref:System.Windows.NameScope> .

Následující příklad přiřadí název <xref:System.Windows.Freezable> objektu.

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

Objekt pak může být cílem animace.

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

<xref:System.Windows.Media.Animation.Storyboard>objekty používají obory názvů k vyřešení <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Vlastnosti. Další informace o oborech názvů WPF naleznete v tématu [WPF XAML obory názvů WPF](../advanced/wpf-xaml-namescopes.md). Pokud <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> je vlastnost vynechána, animace cílí na prvek, ve kterém je definován, nebo v případě stylů, elementu style.

Někdy není možné přiřadit název k <xref:System.Windows.Freezable> objektu. Například pokud <xref:System.Windows.Freezable> je deklarován jako prostředek nebo použit k nastavení hodnoty vlastnosti ve stylu, nemůže být název zadán. Vzhledem k tomu, že nemá název, nejde na něj cílit přímo, ale dá se cílit nepřímo. Následující části popisují způsob použití nepřímých cílů.

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>Nepřímý cíl

Existují situace, kdy <xref:System.Windows.Freezable> nelze cílit přímo pomocí animace, například když <xref:System.Windows.Freezable> je deklarován jako prostředek nebo použit k nastavení hodnoty vlastnosti ve stylu. V takových případech, i když nemůžete cílit přímo na něj, můžete objekt stále animovat <xref:System.Windows.Freezable> . Namísto nastavování <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> vlastnosti s názvem <xref:System.Windows.Freezable> Zadejte název elementu, do kterého <xref:System.Windows.Freezable> "patří". Například <xref:System.Windows.Media.SolidColorBrush> použít k nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> prvku Rectangle, který patří do tohoto obdélníku. Pro animaci štětce byste nastavili animaci <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> s řetězcem vlastností, které začínají na vlastností elementu architektury nebo elementu obsahu architektury, který se <xref:System.Windows.Freezable> použil k nastavení a ukončení s vlastností, která <xref:System.Windows.Freezable> se má animovat.

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

Všimněte si, že pokud <xref:System.Windows.Freezable> je zmrazený, provede se klon, který bude animovaný. Pokud k tomu dojde, vlastnost původního objektu se <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> nadále vrátí `false` , protože původní objekt není ve skutečnosti animovaný. Další informace o klonování naleznete v tématu [Freezable Objects Overview](../advanced/freezable-objects-overview.md).

Všimněte si také, že při použití cíle nepřímých vlastností je možné cílit na objekty, které neexistují. Můžete například předpokládat, že <xref:System.Windows.Controls.Control.Background%2A> konkrétní tlačítko bylo nastaveno pomocí <xref:System.Windows.Media.SolidColorBrush> a a pokusí se animovat jeho barvu, pokud se ve skutečnosti a <xref:System.Windows.Media.LinearGradientBrush> použila k nastavení pozadí tlačítka. V těchto případech není vyvolána žádná výjimka; animace nemůže mít viditelný efekt, protože <xref:System.Windows.Media.LinearGradientBrush> nereaguje na změny <xref:System.Windows.Media.SolidColorBrush.Color%2A> Vlastnosti.

Následující oddíly popisují nepřímou syntaxi cílení vlastnosti podrobněji.

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Nepřímo zaměřené na vlastnost Freezable v jazyce XAML

Chcete-li cílit na vlastnost Freezable v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , použijte následující syntaxi.

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Kde

- *ElementPropertyName* je vlastnost <xref:System.Windows.FrameworkElement> , která se <xref:System.Windows.Freezable> používá k nastavení a

- *FreezablePropertyName* je vlastnost, která se má <xref:System.Windows.Freezable> animovat.

Následující kód ukazuje, jak animovat <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.SolidColorBrush> použít k nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> prvku Rectangle.

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

Někdy je potřeba cílit na Freezable obsažený v kolekci nebo poli.

Chcete-li cílit na Freezable obsažený v kolekci, použijte následující syntaxi cesty.

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

Kde *CollectionIndex* je index objektu ve svém poli nebo kolekci.

Předpokládejme například, že obdélník obsahuje <xref:System.Windows.Media.TransformGroup> prostředek aplikovaný na jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost a chcete animovat jednu z transformací, kterou obsahuje.

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

Následující kód ukazuje, jak animovat vlastnost, která je <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform> znázorněna v předchozím příkladu.

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Nepřímo zaměřené na vlastnost Freezable v kódu

V kódu vytvoříte <xref:System.Windows.PropertyPath> objekt. Při vytváření <xref:System.Windows.PropertyPath> Zadejte <xref:System.Windows.PropertyPath.Path%2A> a <xref:System.Windows.PropertyPath.PathParameters%2A> .

Chcete-li vytvořit <xref:System.Windows.PropertyPath.PathParameters%2A> pole typu <xref:System.Windows.DependencyProperty> , které obsahuje seznam polí identifikátoru vlastnosti závislosti. Pole prvního identifikátoru je určena pro vlastnost <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> , která <xref:System.Windows.Freezable> je použita k nastavení. Pole s následujícím identifikátorem představuje vlastnost cílové třídy <xref:System.Windows.Freezable> . Můžete si ho představit jako řetězec vlastností, které se připojují <xref:System.Windows.Freezable> k <xref:System.Windows.FrameworkElement> objektu.

Následuje příklad řetězu vlastností závislosti, který cílí na <xref:System.Windows.Media.SolidColorBrush.Color%2A> hodnotu <xref:System.Windows.Media.SolidColorBrush> použitou pro nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> prvku Rectangle.

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

Je také nutné zadat <xref:System.Windows.PropertyPath.Path%2A> . <xref:System.Windows.PropertyPath.Path%2A>Je a <xref:System.String> , který dává pokyn <xref:System.Windows.PropertyPath.Path%2A> k interpretaci <xref:System.Windows.PropertyPath.PathParameters%2A> . Používá následující syntaxi.

| |
|-|
|`(`*OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex*`)`|

Kde

- *OwnerPropertyArrayIndex* je index <xref:System.Windows.DependencyProperty> pole, které obsahuje identifikátor <xref:System.Windows.FrameworkElement> vlastnosti objektu, který <xref:System.Windows.Freezable> je použit k nastavení a

- *FreezablePropertyArrayIndex* je index <xref:System.Windows.DependencyProperty> pole, které obsahuje identifikátor vlastnosti k cíli.

Následující příklad ukazuje <xref:System.Windows.PropertyPath.Path%2A> , který se doprovází, jak je <xref:System.Windows.PropertyPath.PathParameters%2A> uvedeno v předchozím příkladu.

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

Následující příklad kombinuje kód v předchozích příkladech k animaci, která se <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> používá k nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> prvku Rectangle.

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

Někdy je potřeba cílit na Freezable obsažený v kolekci nebo poli. Předpokládejme například, že obdélník obsahuje <xref:System.Windows.Media.TransformGroup> prostředek aplikovaný na jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost a chcete animovat jednu z transformací, kterou obsahuje.

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

Chcete-li cílit na <xref:System.Windows.Freezable> obsažený v kolekci, použijte následující syntaxi cesty.

| |
|-|
|`(`*OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex*`)`|

Kde *CollectionIndex* je index objektu ve svém poli nebo kolekci.

Chcete-li cílit na <xref:System.Windows.Media.RotateTransform.Angle%2A> vlastnost <xref:System.Windows.Media.RotateTransform> druhé transformace v <xref:System.Windows.Media.TransformGroup> , použijte následující <xref:System.Windows.PropertyPath.Path%2A> a <xref:System.Windows.PropertyPath.PathParameters%2A> .

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

Následující příklad ukazuje úplný kód pro animování <xref:System.Windows.Media.RotateTransform.Angle%2A> z <xref:System.Windows.Media.RotateTransform> obsažený v <xref:System.Windows.Media.TransformGroup> .

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Nepřímo cílící na Freezable jako výchozí bod

Předchozí části popisují, jak nepřímo cílit na, spuštěním <xref:System.Windows.Freezable> s <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> a vytvořením řetězu vlastností pro <xref:System.Windows.Freezable> dílčí vlastnost. Můžete také použít <xref:System.Windows.Freezable> jako výchozí bod a nepřímo cílit na jednu z jejích <xref:System.Windows.Freezable> dílčích vlastností. Jedno další omezení platí při použití <xref:System.Windows.Freezable> jako výchozí bod pro nepřímý cíl: začátek <xref:System.Windows.Freezable> a každý <xref:System.Windows.Freezable> mezi ním a nepřímo cílovou dílčí vlastnost nesmí být zmrazen.

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Interaktivní řízení scénáře v jazyce XAML

Pokud chcete začít scénář v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , použijte <xref:System.Windows.Media.Animation.BeginStoryboard> akci triggeru. <xref:System.Windows.Media.Animation.BeginStoryboard>distribuuje animace do objektů a vlastností, které animuje, a spustí scénář. (Podrobné informace o tomto procesu najdete v tématu [Přehled systému animace a časování](animation-and-timing-system-overview.md).) Pokud pojmenujete <xref:System.Windows.Media.Animation.BeginStoryboard> název tak, že určíte jeho <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> vlastnost, provedete si ho pomocí vlastního scénáře. Scénář pak můžete interaktivně kontrolovat po jeho spuštění. Níže je seznam přidaných akcí scénářů, které můžete použít s triggery událostí k řízení scénáře.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Pozastaví scénář.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Obnoví pozastavený scénář.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Změní rychlost scénáře.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Posune scénář do konce jeho období vyplňování, pokud má nějaký.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Zastaví scénář.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Odebere scénář.

V následujícím příkladu se pro interaktivní řízení scénáře používají ověřitelné akce scénářů.

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Interaktivní řízení scénáře pomocí kódu

Předchozí příklady ukázaly, jak animovat pomocí akcí triggeru. V kódu můžete také řídit scénář pomocí interaktivních metod <xref:System.Windows.Media.Animation.Storyboard> třídy. <xref:System.Windows.Media.Animation.Storyboard>Aby bylo možné provést interaktivní v kódu, je nutné použít příslušné přetížení <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody scénáře a určit, `true` aby bylo možné je ovládat. <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>Další informace najdete na stránce.

V následujícím seznamu jsou uvedeny metody, které lze použít k manipulaci s a <xref:System.Windows.Media.Animation.Storyboard> po jejím spuštění:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

Výhodou použití těchto metod je, že nemusíte vytvářet <xref:System.Windows.Trigger> ani vytvářet <xref:System.Windows.TriggerAction> objekty, stačí pouze odkaz na ovladatelné, <xref:System.Windows.Media.Animation.Storyboard> které chcete manipulovat.

> [!NOTE]
> Všechny interaktivní akce provedené na <xref:System.Windows.Media.Animation.Clock> , a proto dojde k <xref:System.Windows.Media.Animation.Storyboard> dalšímu taktování modulu časování, ke kterému dojde krátce před dalším vykreslováním. Například pokud použijete <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metodu k přechodu na jiný bod v animaci, hodnota vlastnosti se nemění okamžitě, místo toho se hodnota změní na další taktování modulu časování.

Následující příklad ukazuje, jak použít a ovládat animace pomocí interaktivních metod <xref:System.Windows.Media.Animation.Storyboard> třídy.

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>Animace ve stylu

Můžete použít <xref:System.Windows.Media.Animation.Storyboard> objekty k definování animací v <xref:System.Windows.Style> . Animace s a <xref:System.Windows.Media.Animation.Storyboard> v <xref:System.Windows.Style> je podobná použití <xref:System.Windows.Media.Animation.Storyboard> jinde, s následujícími třemi výjimkami:

- Neurčíte a <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ; <xref:System.Windows.Media.Animation.Storyboard> vždy cílí na element, na který <xref:System.Windows.Style> je použit. Chcete-li cílit na <xref:System.Windows.Freezable> objekty, je nutné použít nepřímé cílení. Další informace o nepřímých cílících cíle najdete v části [nepřímé cílení](#pathsyntaxforchangeable) .

- Nemůžete zadat <xref:System.Windows.EventTrigger.SourceName%2A> <xref:System.Windows.EventTrigger> ani <xref:System.Windows.Trigger> .

- Nemůžete použít dynamické odkazy na prostředky nebo výrazy vazby dat k nastavení <xref:System.Windows.Media.Animation.Storyboard> hodnot vlastností nebo animací. To je proto, že všechno, co uvnitř <xref:System.Windows.Style> musí být bezpečné pro přístup z více vláken, a systém časování musí <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> objekty, aby byly bezpečné pro přístup z více vláken. A <xref:System.Windows.Media.Animation.Storyboard> nemůže být zmrazen, pokud mu nebo jeho podřízené časové osy obsahují odkazy na dynamické prostředky nebo výrazy datových vazeb. Další informace o zamrznutí a dalších <xref:System.Windows.Freezable> funkcích najdete v tématu [Přehled objektů Freezable](../advanced/freezable-objects-overview.md).

- V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemůžete deklarovat obslužné rutiny událostí pro <xref:System.Windows.Media.Animation.Storyboard> události nebo animace.

Příklad znázorňující, jak definovat scénář ve stylu, naleznete v [animaci v příkladu stylu](how-to-animate-in-a-style.md) .

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>Animace v objektu ControlTemplate

Můžete použít <xref:System.Windows.Media.Animation.Storyboard> objekty k definování animací v <xref:System.Windows.Controls.ControlTemplate> . Animování s a <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Controls.ControlTemplate> je podobné použití <xref:System.Windows.Media.Animation.Storyboard> jinde, s následujícími dvěma výjimkami:

- <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>Může odkazovat pouze na podřízené objekty <xref:System.Windows.Controls.ControlTemplate> . Není <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> -li parametr zadán, animace cílí na element, na který <xref:System.Windows.Controls.ControlTemplate> je použit.

- <xref:System.Windows.EventTrigger.SourceName%2A>Pro <xref:System.Windows.EventTrigger> nebo <xref:System.Windows.Trigger> může odkazovat pouze na podřízené objekty <xref:System.Windows.Controls.ControlTemplate> .

- Nemůžete použít dynamické odkazy na prostředky nebo výrazy vazby dat k nastavení <xref:System.Windows.Media.Animation.Storyboard> hodnot vlastností nebo animací. To je proto, že všechno, co uvnitř <xref:System.Windows.Controls.ControlTemplate> musí být bezpečné pro přístup z více vláken, a systém časování musí <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> objekty, aby byly bezpečné pro přístup z více vláken. A <xref:System.Windows.Media.Animation.Storyboard> nemůže být zmrazen, pokud mu nebo jeho podřízené časové osy obsahují odkazy na dynamické prostředky nebo výrazy datových vazeb. Další informace o zamrznutí a dalších <xref:System.Windows.Freezable> funkcích najdete v tématu [Přehled objektů Freezable](../advanced/freezable-objects-overview.md).

- V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemůžete deklarovat obslužné rutiny událostí pro <xref:System.Windows.Media.Animation.Storyboard> události nebo animace.

Příklad znázorňující, jak definovat scénář v <xref:System.Windows.Controls.ControlTemplate> naleznete v tématu [animace v ControlTemplate](how-to-animate-in-a-controltemplate.md) příkladu.

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>Animace při změně hodnoty vlastnosti

V šablonách stylů a ovládacích prvků lze pomocí objektů triggeru spustit scénář při změně vlastnosti. Příklady naleznete v tématu [triggering animace při změně hodnoty vlastnosti](how-to-trigger-an-animation-when-a-property-value-changes.md) a [animace v ControlTemplate](how-to-animate-in-a-controltemplate.md).

Animace aplikované <xref:System.Windows.Trigger> objekty vlastností se chovají složitějším způsobem než <xref:System.Windows.EventTrigger> animace nebo animace spuštěné pomocí <xref:System.Windows.Media.Animation.Storyboard> metod.  Předávají s animacemi definovanými jinými <xref:System.Windows.Trigger> objekty, ale vytvářejí <xref:System.Windows.EventTrigger> animace a triggery spouštěné metodou.

## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Přehled způsobů animace vlastností](property-animation-techniques-overview.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
