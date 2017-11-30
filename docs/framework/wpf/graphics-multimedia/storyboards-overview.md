---
title: "Přehled scénářů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c90fb49a8fb5c63a3bf680bbbe5347db881d500b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="storyboards-overview"></a>Přehled scénářů
Toto téma ukazuje, jak používat <xref:System.Windows.Media.Animation.Storyboard> objekty uspořádání a použít animace. Popisuje, jak interaktivně manipulaci s <xref:System.Windows.Media.Animation.Storyboard> objekty a popisuje nepřímých vlastnost cílení na syntaxi.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Zjistit v tomto tématu byste měli být obeznámeni s typy různých animace a jejich základní funkce. Úvod do animace, najdete v článku [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Také byste měli znát postup používání přidružené vlastnosti. Další informace o přidružené vlastnosti najdete v tématu [připojen přehled vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>Co je scénáře?  
 Animace nejsou jenom užitečné typ časové osy. Ostatní časová osa třídy jsou k dispozici uspořádat nastaví časové osy a chcete použít časové osy pro vlastnosti. Kontejner časové osy odvozena od <xref:System.Windows.Media.Animation.TimelineGroup> třídy a zahrnují <xref:System.Windows.Media.Animation.ParallelTimeline> a <xref:System.Windows.Media.Animation.Storyboard>.  
  
 A <xref:System.Windows.Media.Animation.Storyboard> je typ osy kontejneru, která poskytuje cílení informace pro časové osy obsahuje. Scénář může obsahovat jakýkoli typ <xref:System.Windows.Media.Animation.Timeline>, včetně dalších kontejneru časové osy a animace. <xref:System.Windows.Media.Animation.Storyboard>objekty umožňují kombinovat časových os, která ovlivňují různé objekty a vlastnosti do jediné časové osy stromu, což usnadňuje uspořádání a řízení chování komplexní časování. Předpokládejme například, že chcete tlačítko, které provádí tyto tři věci.  
  
-   Růst a měnit barvy, když uživatel vybere tlačítko.  
  
-   Zmenšit rychle a pak zpátky na původní velikost při kliknutí na zvýší.  
  
-   Zmenšení a vykreslit na 50 procent krytí, když se zakáže.  
  
 V takovém případě máte více sad animací, které se vztahují ke stejnému objektu, a chcete přehrávat v různou dobu, závisí na stavu tlačítka. <xref:System.Windows.Media.Animation.Storyboard>objekty umožňují uspořádat animace a použít je jeden nebo více objektů ve skupinách.  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>Kde můžete použít Storyboard?  
 A <xref:System.Windows.Media.Animation.Storyboard> slouží k animace vlastností závislostí animatable třídy (Další informace o třídě díky animatable najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)). Ale protože doplňku je funkce úrovni rozhraní, objekt musí patřit do <xref:System.Windows.NameScope> z <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>.  
  
 Například můžete použít <xref:System.Windows.Media.Animation.Storyboard> proveďte následující:  
  
-   Animace <xref:System.Windows.Media.SolidColorBrush> (Non-framework element), který Vybarví pozadí tlačítko (typ <xref:System.Windows.FrameworkElement>),  
  
-   Animace <xref:System.Windows.Media.SolidColorBrush> (Non-framework element), který vybarví výplně <xref:System.Windows.Media.GeometryDrawing> (Non-framework element) zobrazí pomocí <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).  
  
-   V kódu animace <xref:System.Windows.Media.SolidColorBrush> deklarované třídou, která obsahuje také <xref:System.Windows.FrameworkElement>, pokud <xref:System.Windows.Media.SolidColorBrush> registrovány na jeho název, <xref:System.Windows.FrameworkElement>.  
  
 Však nelze použít <xref:System.Windows.Media.Animation.Storyboard> pro animaci <xref:System.Windows.Media.SolidColorBrush> neregistrovala jeho název <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, nebo nebyl použit nastavit vlastnost <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>.  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>Jak se má použít animací s scénáře  
 Použít <xref:System.Windows.Media.Animation.Storyboard> uspořádání a použít animací, přidejte animací jako podřízené časové osy z <xref:System.Windows.Media.Animation.Storyboard>. <xref:System.Windows.Media.Animation.Storyboard> Třída poskytuje <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> přidružené vlastnosti. Nastavení těchto vlastností na animace a zadat jeho cílový objekt a vlastnost.  
  
 Použít animací na jejich cíle, začnete <xref:System.Windows.Media.Animation.Storyboard> pomocí akce aktivační události nebo metodu. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít <xref:System.Windows.Media.Animation.BeginStoryboard> objektu s <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>, nebo <xref:System.Windows.DataTrigger>. V kódu, můžete také použít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda.  
  
 V následující tabulce jsou uvedeny různých místech kde každý <xref:System.Windows.Media.Animation.Storyboard> začít technika je podporována: jednotlivých instancí, styl, šablony správy a datová šablona. "Jednotlivých instancí" odkazuje na techniku použití animaci nebo storyboard přímo do instance objektu, nikoli v styl, řízení šablony nebo šablony data.  
  
|Scénáře je spuštěno pomocí...|Jednotlivých instancí|Styl|Šablony správy|Datová šablona|Příklad|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>a<xref:System.Windows.EventTrigger>|Ano|Ano|Ano|Ano|[Animace vlastnost pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>a vlastnost<xref:System.Windows.Trigger>|Ne|Ano|Ano|Ano|[Aktivace animace, když hodnota vlastnosti](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>a<xref:System.Windows.DataTrigger>|Ne|Ano|Ano|Ano|[Postupy: aktivace animace při změně dat](http://msdn.microsoft.com/en-us/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>– Metoda|Ano|Ne|Ne|Ne|[Animace vlastnost pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Storyboard> pro animaci <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> elementu a <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> použita k vyplnění, <xref:System.Windows.Shapes.Rectangle>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 Následující části popisují <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> přidružené vlastnosti podrobněji.  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Cílení na elementy Framework, Framework obsahu prvky a Freezables  
 V předchozí části je uvedeno, že pro animace najít cíli, je třeba znát název cílové složky a vlastností pro animaci. Určení vlastností pro animaci je přímo dál: jednoduše nastavit <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> s názvem vlastnosti, která má animace.  Zadejte název objektu, jehož vlastnosti chcete animace nastavením <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> vlastnost animace.  
  
 Pro <xref:System.Windows.Setter.TargetName%2A> vlastnost pracovat, cílový objekt musí mít název. Přiřazení název <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je jiný než název přiřazení <xref:System.Windows.Freezable> objektu.  
  
 Framework prvky jsou tyto třídy, které dědí od <xref:System.Windows.FrameworkElement> třídy. Příklady elementů framework <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>, a <xref:System.Windows.Shapes.Rectangle>. Prvky jsou v podstatě všechny windows, panelů a ovládací prvky. Framework obsahu prvky jsou tyto třídy, které dědí od <xref:System.Windows.FrameworkContentElement> třídy. Příklady obsahu elementů framework <xref:System.Windows.Documents.FlowDocument> a <xref:System.Windows.Documents.Paragraph>. Pokud si nejste jistí, jestli je typ framework element nebo framework content element, zkontrolujte, zda má vlastnost názvu. Pokud ano, je to pravděpodobně framework element nebo framework content element. Aby byly zkontrolujte oddíl hierarchie dědičnosti jeho typ stránky.  
  
 Chcete-li povolit cílení na framework element nebo element framework obsahu v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nastavíte jeho <xref:System.Windows.FrameworkElement.Name%2A> vlastnost. V kódu, budete také muset použít <xref:System.Windows.NameScope.RegisterName%2A> metoda zaregistrovat název elementu s elementem, pro který jste vytvořili <xref:System.Windows.NameScope>.  
  
 Následující příklad, prováděné z předchozího příkladu, přiřadí název `MyRectangle` <xref:System.Windows.Shapes.Rectangle>, typ <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 Jakmile má název, můžete animace vlastnost tohoto elementu.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable>typy jsou tyto třídy, které dědí od <xref:System.Windows.Freezable> třídy. Příklady <xref:System.Windows.Freezable> zahrnují <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>, a <xref:System.Windows.Media.GradientStop>.  
  
 Chcete-li povolit cílení <xref:System.Windows.Freezable> podle animace v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijete [x: Name – direktiva](../../../../docs/framework/xaml-services/x-name-directive.md) přiřadit název. V kódu, můžete použít <xref:System.Windows.NameScope.RegisterName%2A> metoda zaregistrovat svůj název s elementem, pro který jste vytvořili <xref:System.Windows.NameScope>.  
  
 Následující příklad přiřadí název <xref:System.Windows.Freezable> objektu.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 Objekt může být cílem pak animace.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard>objekty pomocí názvu oborů přeložit <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> vlastnost. Další informace o oborech název WPF najdete v tématu [WPF XAML Namescopes](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md). Pokud <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> vlastnost je vynechána, cílem animace elementu, na který je definován, nebo v případě styly prvku s vzhledem.  
  
 Někdy název nemůže být přiřazen, <xref:System.Windows.Freezable> objektu. Například pokud <xref:System.Windows.Freezable> je deklarován jako prostředek nebo použít k nastavení hodnoty vlastnosti ve stylu, nemůže být zadán název. Protože nemá název, nelze cílit přímo, ale je možné cílit nepřímo. Následující části popisují, jak používat nepřímé cílení.  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>Nepřímý cílení  
 V určitých časech <xref:System.Windows.Freezable> nemůže být cílem přímo animace, jako např. kdy <xref:System.Windows.Freezable> je deklarován jako prostředek nebo použít k nastavení hodnoty vlastnosti ve stylu. V těchto případech i v případě, že ji nelze cílit přímo, vám může stále animace <xref:System.Windows.Freezable> objektu. Místo nastavení <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> vlastnost s názvem <xref:System.Windows.Freezable>, je mu název elementu ke kterému <xref:System.Windows.Freezable> "patří." Například <xref:System.Windows.Media.SolidColorBrush> použít k nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> obdélník element patří do tohoto rámečku. Pro animaci štětec, se nastavuje animace <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> s řetěz vlastnosti, který začíná na vlastnost framework element nebo framework content element <xref:System.Windows.Freezable> se používá k nastavení a končí <xref:System.Windows.Freezable> vlastností pro animaci.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 Všimněte si, že, pokud <xref:System.Windows.Freezable> je pozastaveny, budou provedeny klon, a že klon bude animovaný. Pokud k tomu dojde, původní objekt <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> vlastnost nadále vrátit `false`, protože původní objekt není ve skutečnosti animovaný. Další informace o klonování, najdete v článku [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Všimněte si také, že při použití cílení nepřímých vlastnost, je možné cílové objekty, které neexistují. Například může předpokládá, že <xref:System.Windows.Controls.Control.Background%2A> tlačítka s konkrétní byl nastaven s <xref:System.Windows.Media.SolidColorBrush> a pokuste se použije animaci jeho barvu, když ve skutečnosti <xref:System.Windows.Media.LinearGradientBrush> byla použita k nastavení pozadí na tlačítko. V těchto případech je vyvolána žádná výjimka; animace nepodaří mít viditelné vliv, protože <xref:System.Windows.Media.LinearGradientBrush> nereaguje na změny <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost.  
  
 Následující části popisují nepřímých vlastnost cílení syntaxe podrobněji.  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Nepřímo cílení na vlastnost zmrazitelné v jazyce XAML  
 Pro vlastnost zmrazitelné v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte následující syntaxi.  
  
||  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 Where  
  
-   *ElementPropertyName* je vlastnost <xref:System.Windows.FrameworkElement> který <xref:System.Windows.Freezable> se používá k nastavení, a  
  
-   *FreezablePropertyName* je vlastnost <xref:System.Windows.Freezable> pro animaci.  
  
 Následující kód ukazuje, jak animace <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> použít k nastavení  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A>rámeček elementu.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 V některých případech musíte cílové zmrazitelné obsažené v kolekci nebo pole.  
  
 Pokud chcete zacílit zmrazitelné obsažené v kolekci, pomocí následující syntaxe cesty.  
  
||  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 Kde *CollectionIndex* je index objektu v jeho pole nebo kolekce.  
  
 Předpokládejme například, že má obdélníku <xref:System.Windows.Media.TransformGroup> prostředků u jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost a chcete vytvořit animaci transformací obsahuje.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 Následující kód ukazuje, jak animace <xref:System.Windows.Media.RotateTransform.Angle%2A> vlastnost <xref:System.Windows.Media.RotateTransform> ukazuje předchozí příklad.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Nepřímo cílení na vlastnost zmrazitelné v kódu  
 V kódu, můžete vytvořit <xref:System.Windows.PropertyPath> objektu. Když vytvoříte <xref:System.Windows.PropertyPath>, zadáte <xref:System.Windows.PropertyPath.Path%2A> a <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 Chcete-li vytvořit <xref:System.Windows.PropertyPath.PathParameters%2A>, vytvoříte pole typu <xref:System.Windows.DependencyProperty> obsahující seznam pole identifikátoru vlastnosti závislosti. První identifikátor pole je pro vlastnost <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> , <xref:System.Windows.Freezable> slouží k nastavení. Další pole identifikátor představuje vlastnost <xref:System.Windows.Freezable> k cíli. Považujte to jako řetěz vlastnosti, která se připojuje <xref:System.Windows.Freezable> k <xref:System.Windows.FrameworkElement> objektu.  
  
 Tady je příklad řetězec závislostí vlastnost, která je cílena <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> použít k nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> elementu obdélníku.  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 Budete taky muset zadat <xref:System.Windows.PropertyPath.Path%2A>. A <xref:System.Windows.PropertyPath.Path%2A> je <xref:System.String> , která oznamuje <xref:System.Windows.PropertyPath.Path%2A> interpretace jeho <xref:System.Windows.PropertyPath.PathParameters%2A>. Používá následující syntaxe.  
  
||  
|-|  
|`(`*OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex*`)`|  
  
 Where  
  
-   *OwnerPropertyArrayIndex* je index <xref:System.Windows.DependencyProperty> pole, která obsahuje identifikátor <xref:System.Windows.FrameworkElement> vlastnost objektu, <xref:System.Windows.Freezable> se používá k nastavení, a  
  
-   *FreezablePropertyArrayIndex* je index <xref:System.Windows.DependencyProperty> pole, která obsahuje identifikátor vlastnosti k cíli.  
  
 Následující příklad ukazuje <xref:System.Windows.PropertyPath.Path%2A> který doprovází <xref:System.Windows.PropertyPath.PathParameters%2A> definované v předchozím příkladu.
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 Následující příklad kombinuje kód v předchozích příkladech pro animaci <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> použít k nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> elementu obdélníku.  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 V některých případech musíte cílové zmrazitelné obsažené v kolekci nebo pole. Předpokládejme například, že má obdélníku <xref:System.Windows.Media.TransformGroup> prostředků u jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost a chcete vytvořit animaci transformací obsahuje.  
  
 [!code-xaml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 Cíl <xref:System.Windows.Freezable> obsažené v kolekci, použijte následující syntaxi cestu.  
  
||  
|-|  
|`(`*OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex*`)`|  
  
 Kde *CollectionIndex* je index objektu v jeho pole nebo kolekce.  
  
 Cíl <xref:System.Windows.Media.RotateTransform.Angle%2A> vlastnost <xref:System.Windows.Media.RotateTransform>, druhý transformace v <xref:System.Windows.Media.TransformGroup>, byste použili následující <xref:System.Windows.PropertyPath.Path%2A> a <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 Následující příklad ukazuje kompletní kód animace <xref:System.Windows.Media.RotateTransform.Angle%2A> z <xref:System.Windows.Media.RotateTransform> obsažené v <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Nepřímo cílení zmrazitelné jako počáteční bod  
 Postup nepřímo cíle popsané v předchozích částech <xref:System.Windows.Freezable> od <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> a řetěz vlastnost k vytvoření <xref:System.Windows.Freezable> dílčí vlastnosti. Můžete použít také <xref:System.Windows.Freezable> jako počáteční bod a nepřímo cíle jeden z jeho <xref:System.Windows.Freezable> dílčí vlastnosti. Jeden další omezení platí při použití <xref:System.Windows.Freezable> jako počáteční bod pro nepřímou cílení: počáteční <xref:System.Windows.Freezable> a každý <xref:System.Windows.Freezable> mezi ním nepřímo cílové dílčí vlastnosti nesmí být pozastaveny.  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Interaktivně řízení Storyboard v jazyce XAML  
 Ke spuštění scénáře v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete použít <xref:System.Windows.Media.Animation.BeginStoryboard> aktivovat akce. <xref:System.Windows.Media.Animation.BeginStoryboard>Animace objektů a vlastností animace a spustí scénáři distribuuje. (Podrobnosti o tomto procesu najdete v tématu [animace a přehled systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).) Pokud zadáte název <xref:System.Windows.Media.Animation.BeginStoryboard> název zadáním jeho <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> vlastnost, provedete ho ovladatelné scénáře. Pak můžete interaktivně ovládat scénáři po jeho spuštění. Následuje seznam akcí ovladatelné storyboard pomocí aktivačních událostí k řízení scénáře.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Pozastaví scénáři.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Obnoví pozastavenou scénáře.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Změny do scénáře rychlost.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Pokud má jedna přejde storyboard na konci období jeho výplně.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Zastaví scénáři.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Odebere scénáři.  
  
 V následujícím příkladu je možné řídit storyboard akce interaktivně určit scénáře.  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Interaktivně řízení scénáře pomocí kódu  
 V předchozích příkladech ukázaly, jak animace pomocí akce aktivační události. V kódu, může také řídit scénáře použití interaktivní metod <xref:System.Windows.Media.Animation.Storyboard> třídy. Pro <xref:System.Windows.Media.Animation.Storyboard> má být provedeno interaktivní v kódu, musíte použít příslušnému přetížení do scénáře <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda a zadejte `true` Chcete-li řídit. Najdete v článku <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> stránka Další informace.  
  
 Následující seznam obsahuje metody, které můžete použít k manipulaci <xref:System.Windows.Media.Animation.Storyboard> po spuštění:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 Pomocí těchto metod výhodou je, že nemusíte vytvářet <xref:System.Windows.Trigger> nebo <xref:System.Windows.TriggerAction> objekty; je právě třeba odkaz na ovladatelné <xref:System.Windows.Media.Animation.Storyboard> chcete upravit.  
  
 **Poznámka:** všechny interaktivní akce prováděné <xref:System.Windows.Media.Animation.Clock>a proto také na <xref:System.Windows.Media.Animation.Storyboard> dojde na další značek časování modulu, který se stane krátce před další vykreslení. Například pokud použijete <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metoda přejít do jiného bodu v animaci, hodnota vlastnosti nemění okamžitě, místo toho hodnota změní na další značek časování stroje.  
  
 Následující příklad ukazuje, jak použít a řídit použití interaktivní metod animace <xref:System.Windows.Media.Animation.Storyboard> třídy.  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>Animace ve stylu  
 Můžete použít <xref:System.Windows.Media.Animation.Storyboard> objekty, které chcete definovat animace v <xref:System.Windows.Style>. Animace s <xref:System.Windows.Media.Animation.Storyboard> v <xref:System.Windows.Style> je podobný používání <xref:System.Windows.Media.Animation.Storyboard> jinam, s následujícími třemi výjimkami:  
  
-   Nezadáte <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; <xref:System.Windows.Media.Animation.Storyboard> vždy cílí element ke kterému <xref:System.Windows.Style> platí. Cíl <xref:System.Windows.Freezable> objekty, je nutné použít nepřímé cílení. Další informace o nepřímých cílení najdete v tématu [nepřímých cílení](#pathsyntaxforchangeable) části.  
  
-   Nelze zadat <xref:System.Windows.EventTrigger.SourceName%2A> pro <xref:System.Windows.EventTrigger> nebo <xref:System.Windows.Trigger>.  
  
-   Dynamické prostředků odkazy nebo datové vazby výrazů nelze použít k nastavení <xref:System.Windows.Media.Animation.Storyboard> nebo hodnoty vlastností animace. Je to způsobeno všechno uvnitř <xref:System.Windows.Style> musí být bezpečné pro přístup z více vláken, a musí systém časování <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> objekty tak, aby byly bezpečné pro přístup z více vláken. A <xref:System.Windows.Media.Animation.Storyboard> nelze pozastaveny, pokud ho nebo jeho podřízených časové osy obsahovat výrazy dynamické prostředků odkazy nebo datové vazby. Další informace o zmrazení a dalších <xref:System.Windows.Freezable> funkce, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nelze deklarovat obslužné rutiny události pro <xref:System.Windows.Media.Animation.Storyboard> nebo události animace.  
  
 Příkladem zobrazujícím postup definice scénáře ve stylu, najdete v článku [animace ve stylu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md) příklad.  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>Animace v objektu ControlTemplate  
 Můžete použít <xref:System.Windows.Media.Animation.Storyboard> objekty, které chcete definovat animace v <xref:System.Windows.Controls.ControlTemplate>. Animace s <xref:System.Windows.Media.Animation.Storyboard> v <xref:System.Windows.Controls.ControlTemplate> je podobný používání <xref:System.Windows.Media.Animation.Storyboard> jinam, s následujícími dvěma výjimkami:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Mohou odkazovat pouze na podřízené objekty <xref:System.Windows.Controls.ControlTemplate>. Pokud <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> není zadán, animace cílí element ke kterému <xref:System.Windows.Controls.ControlTemplate> platí.  
  
-   <xref:System.Windows.EventTrigger.SourceName%2A> Pro <xref:System.Windows.EventTrigger> nebo <xref:System.Windows.Trigger> mohou odkazovat pouze na podřízené objekty <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Dynamické prostředků odkazy nebo datové vazby výrazů nelze použít k nastavení <xref:System.Windows.Media.Animation.Storyboard> nebo hodnoty vlastností animace. Je to způsobeno všechno uvnitř <xref:System.Windows.Controls.ControlTemplate> musí být bezpečné pro přístup z více vláken, a musí systém časování <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> objekty tak, aby byly bezpečné pro přístup z více vláken. A <xref:System.Windows.Media.Animation.Storyboard> nelze pozastaveny, pokud ho nebo jeho podřízených časové osy obsahovat výrazy dynamické prostředků odkazy nebo datové vazby. Další informace o zmrazení a dalších <xref:System.Windows.Freezable> funkce, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nelze deklarovat obslužné rutiny události pro <xref:System.Windows.Media.Animation.Storyboard> nebo události animace.  
  
 Příklad zobrazuje jak definovat storyboard v <xref:System.Windows.Controls.ControlTemplate>, najdete v článku [animace v ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md) příklad.  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>Animace při změně hodnoty vlastnosti  
 Styly a šablon ovládacích prvků můžete použít aktivační objekty zahájíte storyboard při změně vlastnosti. Příklady najdete v tématu [aktivovat animace při změn hodnot vlastností](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md) a [animace v ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md).  
  
 Použité vlastností animace <xref:System.Windows.Trigger> objekty chovat způsobem složitější než <xref:System.Windows.EventTrigger> animací nebo animace spuštěna pomocí <xref:System.Windows.Media.Animation.Storyboard> metody.  Jejich "aby handoff" animací definované jiná <xref:System.Windows.Trigger> objekty, ale tvoří s <xref:System.Windows.EventTrigger> a metoda aktivované animace.  
  
## <a name="see-also"></a>Viz také  
 [Animace – přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vlastnost animace techniky – přehled](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
