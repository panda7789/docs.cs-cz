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
ms.openlocfilehash: fa0143aac4253b6a7648da589e01ac8abf9d4341
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492682"
---
# <a name="storyboards-overview"></a>Přehled scénářů
Toto téma ukazuje, jak používat <xref:System.Windows.Media.Animation.Storyboard> objekty k uspořádání a použití animací. Popisuje, jak interaktivně pracovat s <xref:System.Windows.Media.Animation.Storyboard> objektů a popisuje nepřímé vlastnost cílení na syntaxi.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu informace o tom, byste měli vědět, jak jiné typy a jejich základní funkce. Úvod do animace, najdete v článku [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). By měl také vědět, jak používat připojené vlastnosti. Další informace o přidružené vlastnosti, najdete v článku [přehled připojených vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>Co je scénáře?  
 Animace nejsou užitečné typu časové osy. Pomoci vám organizovat nastaví časové osy a chcete použít časové osy pro vlastnosti jsou k dispozici další třídy časové osy. Časové osy kontejneru odvozovat <xref:System.Windows.Media.Animation.TimelineGroup> třídy a zahrnují <xref:System.Windows.Media.Animation.ParallelTimeline> a <xref:System.Windows.Media.Animation.Storyboard>.  
  
 A <xref:System.Windows.Media.Animation.Storyboard> k typu časové osy kontejneru, který obsahuje cílení informace o časových os obsahuje. Scénář může obsahovat jakýkoli typ <xref:System.Windows.Media.Animation.Timeline>, včetně jiné časové osy kontejneru a animace. <xref:System.Windows.Media.Animation.Storyboard> objekty umožňují kombinovat časové osy, které ovlivňují celou řadu objektů a vlastností do stromu jediné časové osy, usnadňuje k uspořádání a řízení chování komplexní časování. Předpokládejme například, že chcete tlačítko, které nemá tyto tři věci.  
  
-   Růst a měnit barvy, když uživatel vybere tlačítko.  
  
-   Zmenšit okamžitě a pak zpátky na původní velikost při kliknutí na.  
  
-   Zmenšit a má vyblednout krytí 50 procent, když bude zakázáno.  
  
 V takovém případě máte víc kopií animace, které se vztahují ke stejnému objektu a chcete přehrát v různou dobu, závisí na stav tlačítka. <xref:System.Windows.Media.Animation.Storyboard> objekty umožňují organizovat animace a použít je ve skupinách na jeden nebo více objektů.  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>Kde můžete použít ve scénáři?  
 A <xref:System.Windows.Media.Animation.Storyboard> můžete použít pro animaci vlastnosti závislosti animovatelné tříd (Další informace o co dělá z třídy animovatelné, najdete v článku [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)). Však storyboarding je funkcí úrovni architektury, objekt musí být <xref:System.Windows.NameScope> z <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>.  
  
 Například můžete použít <xref:System.Windows.Media.Animation.Storyboard> můžete provádět následující:  
  
-   Animace <xref:System.Windows.Media.SolidColorBrush> (Non-framework prvek), která jsou vykreslovány na pozadí tlačítka (typ <xref:System.Windows.FrameworkElement>),  
  
-   Animace <xref:System.Windows.Media.SolidColorBrush> (Non-framework prvek), která jsou vykreslovány výplně <xref:System.Windows.Media.GeometryDrawing> (Non-framework element) zobrazí pomocí <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).  
  
-   V kódu, animace <xref:System.Windows.Media.SolidColorBrush> deklarovanou třídou, která obsahuje také <xref:System.Windows.FrameworkElement>, pokud <xref:System.Windows.Media.SolidColorBrush> zaregistrovaného na jeho název, který <xref:System.Windows.FrameworkElement>.  
  
 Však nelze použít <xref:System.Windows.Media.Animation.Storyboard> pro animaci <xref:System.Windows.Media.SolidColorBrush> nezaregistrovala stejný název jako <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, nebo se používá k nastavení vlastností <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>.  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>Postup použití animací pomocí scénáře  
 Použití <xref:System.Windows.Media.Animation.Storyboard> k uspořádání a použití animací, přidáte jako podřízených časových os z animací <xref:System.Windows.Media.Animation.Storyboard>. <xref:System.Windows.Media.Animation.Storyboard> Třída poskytuje <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> připojené vlastnosti. Tyto vlastnosti nastavit na animace k určení jeho cílové objektů a vlastností.  
  
 Použití animací na svých cílů, začít <xref:System.Windows.Media.Animation.Storyboard> pomocí akce aktivační události nebo metodu. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít <xref:System.Windows.Media.Animation.BeginStoryboard> objektu <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>, nebo <xref:System.Windows.DataTrigger>. V kódu, můžete použít také <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody.  
  
 V následující tabulce jsou uvedeny na různých místech kde každý <xref:System.Windows.Media.Animation.Storyboard> začít technikou je podporováno: jednotlivé instance, styl, šablony ovládacího prvku a šablony. "Za instanci" odkazuje na postup použití animaci nebo scénáře přímo do instance objektu, nikoli ve stylu, šablony ovládacího prvku nebo šablony.  
  
|Scénář je nezačali používat...|Jednotlivé instance|Styl|Šablony ovládacího prvku|Datové šablony|Příklad|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.EventTrigger>|Ano|Ano|Ano|Ano|[Animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a vlastnosti <xref:System.Windows.Trigger>|Ne|Ano|Ano|Ano|[Spuštění animace při změně hodnoty vlastnosti](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.DataTrigger>|Ne|Ano|Ano|Ano|[Postupy: Spuštění animace při změně dat](https://msdn.microsoft.com/library/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> – Metoda|Ano|Ne|Ne|Ne|[Animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 V následujícím příkladu <xref:System.Windows.Media.Animation.Storyboard> pro animaci <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> elementu a <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> , kterým se má <xref:System.Windows.Shapes.Rectangle>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 V následujících částech <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> připojených vlastností podrobněji.  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Cílení rozhraní Framework prvky, Framework elementů obsahu a Zablokovatelné  
 V předchozí části uvedeno, že pro animaci najít svůj cíl, je třeba znát název cíle a vlastnosti pro animaci. Určení vlastností pro animaci je jednoduché: stačí nastavit <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> s názvem vlastnosti pro animaci.  Zadejte název objektu, jehož vlastnosti chcete animovat nastavením <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> vlastnosti animace.  
  
 Pro <xref:System.Windows.Setter.TargetName%2A> vlastnost pro práci, cílový objekt musí mít název. Přiřazuje se název, který má <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se liší od přiřazení název, který má <xref:System.Windows.Freezable> objektu.  
  
 Elementy rozhraní jsou tyto třídy, které dědí z <xref:System.Windows.FrameworkElement> třídy. Příklady prvků framework <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>, a <xref:System.Windows.Shapes.Rectangle>. V podstatě všech windows, panely a ovládací prvky jsou elementy. Elementy obsahu Framework jsou tyto třídy, které dědí z <xref:System.Windows.FrameworkContentElement> třídy. Příklady elementů obsahu framework <xref:System.Windows.Documents.FlowDocument> a <xref:System.Windows.Documents.Paragraph>. Pokud si nejste jisti, zda je typ framework element nebo element content rozhraní framework, zkontrolujte, zda má vlastnost Name. Pokud ano, je to pravděpodobně framework element nebo framework content element. Opravdu zkontrolujte část jeho typ stránky hierarchii dědičnosti.  
  
 Chcete-li povolit cílení na rozhraní framework element nebo element content framework v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nastavíte jeho <xref:System.Windows.FrameworkElement.Name%2A> vlastnost. V kódu, budete také muset použít <xref:System.Windows.NameScope.RegisterName%2A> metody pro registraci v názvu prvku s elementem, pro kterou jste vytvořili <xref:System.Windows.NameScope>.  
  
 Následující příklad přijatá z předchozího příkladu, přiřadí název `MyRectangle` <xref:System.Windows.Shapes.Rectangle>, typ <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 Jakmile má název, lze animovat vlastnost daného prvku.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable> typy jsou tyto třídy, které dědí <xref:System.Windows.Freezable> třídy. Příklady <xref:System.Windows.Freezable> zahrnují <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>, a <xref:System.Windows.Media.GradientStop>.  
  
 Povolit cílení <xref:System.Windows.Freezable> podle animace v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], je použít [x: Name – direktiva](../../../../docs/framework/xaml-services/x-name-directive.md) přiřadit název. V kódu, můžete použít <xref:System.Windows.NameScope.RegisterName%2A> metody pro registraci názvu s elementem, pro kterou jste vytvořili <xref:System.Windows.NameScope>.  
  
 Následující příklad přiřadí název, který má <xref:System.Windows.Freezable> objektu.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 Objekt, můžete potom zacílit podle animace.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> objekty vyřešit pomocí oborů názvů <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> vlastnost. Další informace o oborů názvů WPF naleznete v tématu [obory názvů WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md). Pokud <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> vlastnost vynecháte, animace, zaměřuje elementu, na který je definován, nebo v případě styly, upravený elementu.  
  
 V některých případech nelze přiřadit název k <xref:System.Windows.Freezable> objektu. Například pokud <xref:System.Windows.Freezable> je deklarován jako prostředek nebo použít k nastavení hodnoty vlastnosti ve stylu, nemůže být přiřazen název. Protože nemá název, nelze cílit přímo, ale může být cílem nepřímo. Následující části popisují způsob použití nepřímé cílení.  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>Nepřímé cílení  
 Existují situace <xref:System.Windows.Freezable> nemůže být cílem přímo animaci, jako např. kdy <xref:System.Windows.Freezable> je deklarován jako prostředek nebo použít k nastavení hodnoty vlastnosti ve stylu. V těchto případech i v případě, že ji nelze cílit přímo, můžete stále animovat <xref:System.Windows.Freezable> objektu. Místo nastavení <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> vlastnost s názvem <xref:System.Windows.Freezable>, je jí název elementu ke kterému <xref:System.Windows.Freezable> "patří." Například <xref:System.Windows.Media.SolidColorBrush> lze nastavit <xref:System.Windows.Shapes.Shape.Fill%2A> obdélníku element patří do tohoto obdélníku. Animování štětec nastavíte animace <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> řetězem vlastnosti, která začíná na vlastnost framework element nebo framework content element <xref:System.Windows.Freezable> se použil k a končí <xref:System.Windows.Freezable> vlastností pro animaci.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 Všimněte si, že pokud <xref:System.Windows.Freezable> je zmrazeno, bude proveden klon a bude při animaci pohybovat této klonování. Pokud k tomu dojde, na původní objekt <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> vlastnost nadále vrátit `false`, protože původní objekt není ve skutečnosti animovat. Další informace o klonování, najdete v článku [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Všimněte si také, že při použití cílení nepřímé vlastnost, je možné cílové objektů, které neexistují. Můžete například předpokládat, který <xref:System.Windows.Controls.Control.Background%2A> konkrétní tlačítko byl nastaven s <xref:System.Windows.Media.SolidColorBrush> a pokuste se animace barev, když ve skutečnosti <xref:System.Windows.Media.LinearGradientBrush> se použil k pozadí tlačítka. V takových případech není vyvolána žádná výjimka; animace se nepodaří mít viditelné efekt, protože <xref:System.Windows.Media.LinearGradientBrush> nereaguje na změny <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost.  
  
 Nepřímé vlastnost cílení syntaxe podrobněji v následujících částech.  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Nepřímo cílení na vlastnost zablokovatelného objektu v XAML  
 Cílit na vlastnost zablokovatelného objektu v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte následující syntaxi.  
  
| |  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 Where  
  
-   *ElementPropertyName* zůstává ve vlastnictví <xref:System.Windows.FrameworkElement> která <xref:System.Windows.Freezable> slouží k nastavení, a  
  
-   *FreezablePropertyName* zůstává ve vlastnictví <xref:System.Windows.Freezable> pro animaci.  
  
 Následující kód ukazuje, jak animovat <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> lze nastavit  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A> elementu obdélníku.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 Někdy je potřeba cílit zablokovatelných součástí kolekce nebo pole.  
  
 Cílit na zablokovatelných obsažen v kolekci, použijte následující syntaxe cesty.  
  
| |  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 Kde *CollectionIndex* je index objektu na jeho pole nebo kolekce.  
  
 Předpokládejme například, že má obdélníku <xref:System.Windows.Media.TransformGroup> použit prostředek jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost a chcete vytvořit animaci transformací obsahuje.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 Následující kód ukazuje, jak animovat <xref:System.Windows.Media.RotateTransform.Angle%2A> vlastnost <xref:System.Windows.Media.RotateTransform> je znázorněno v předchozím příkladu.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Nepřímo cílení na vlastnost zablokovatelného objektu v kódu  
 V kódu, můžete vytvořit <xref:System.Windows.PropertyPath> objektu. Při vytváření <xref:System.Windows.PropertyPath>, zadáte <xref:System.Windows.PropertyPath.Path%2A> a <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 Chcete-li vytvořit <xref:System.Windows.PropertyPath.PathParameters%2A>, vytvořit pole typu <xref:System.Windows.DependencyProperty> , který obsahuje seznam pole identifikátoru vlastnosti závislosti. První identifikátor pole je pro vlastnost <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> , který <xref:System.Windows.Freezable> slouží k nastavení. Další pole identifikátor představuje vlastnost <xref:System.Windows.Freezable> do cíle. Ho představit jako řetězec vlastnosti, která se připojuje <xref:System.Windows.Freezable> k <xref:System.Windows.FrameworkElement> objektu.  
  
 Následující je příkladem kdekoliv vlastnost, která se zaměřuje <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> lze nastavit <xref:System.Windows.Shapes.Shape.Fill%2A> elementu obdélníku.  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 Budete taky muset zadat <xref:System.Windows.PropertyPath.Path%2A>. A <xref:System.Windows.PropertyPath.Path%2A> je <xref:System.String> , které sděluje, <xref:System.Windows.PropertyPath.Path%2A> jak interpretovat jeho <xref:System.Windows.PropertyPath.PathParameters%2A>. Používá následující syntaxi.  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|  
  
 Where  
  
-   *OwnerPropertyArrayIndex* je index <xref:System.Windows.DependencyProperty> pole, která obsahuje identifikátor <xref:System.Windows.FrameworkElement> vlastnosti objektu, který <xref:System.Windows.Freezable> slouží k nastavení, a  
  
-   *FreezablePropertyArrayIndex* je index <xref:System.Windows.DependencyProperty> pole, která obsahuje identifikátor vlastnosti k cíli.  
  
 Následující příklad ukazuje <xref:System.Windows.PropertyPath.Path%2A> , který doprovází <xref:System.Windows.PropertyPath.PathParameters%2A> definované v předchozím příkladu.
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 Kombinuje v následujícím příkladu kódu v předchozích příkladech pro animaci <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> lze nastavit <xref:System.Windows.Shapes.Shape.Fill%2A> elementu obdélníku.  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 Někdy je potřeba cílit zablokovatelných součástí kolekce nebo pole. Předpokládejme například, že má obdélníku <xref:System.Windows.Media.TransformGroup> použit prostředek jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost a chcete vytvořit animaci transformací obsahuje.  
  
 [!code-xaml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 K cíli <xref:System.Windows.Freezable> obsažen v kolekci, použijte následující syntaxi cestu.  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|  
  
 Kde *CollectionIndex* je index objektu na jeho pole nebo kolekce.  
  
 K cíli <xref:System.Windows.Media.RotateTransform.Angle%2A> vlastnost <xref:System.Windows.Media.RotateTransform>, druhý transformace v <xref:System.Windows.Media.TransformGroup>, můžete využít následující <xref:System.Windows.PropertyPath.Path%2A> a <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 Následující příklad ukazuje kompletní kód pro animaci <xref:System.Windows.Media.RotateTransform.Angle%2A> z <xref:System.Windows.Media.RotateTransform> obsažené <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Nepřímo cílení zablokovatelného objektu jako počáteční bod  
 Jak nepřímo cílit popsané v předchozích částech <xref:System.Windows.Freezable> začínající <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> a vytváří řetěz vlastnost k <xref:System.Windows.Freezable> dílčí vlastnosti. Můžete také použít <xref:System.Windows.Freezable> jako počáteční bod a nepřímo cílit na jeden z jeho <xref:System.Windows.Freezable> dílčí vlastnosti. Jeden další omezení platí při použití <xref:System.Windows.Freezable> jako výchozí bod pro cílení na nepřímé: počáteční <xref:System.Windows.Freezable> a každý <xref:System.Windows.Freezable> mezi ním a nepřímo cílové dílčí vlastnost nesmí být zmrazené.  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Interaktivní řízení scénáře v XAML  
 Pro spuštění scénáře v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], je použít <xref:System.Windows.Media.Animation.BeginStoryboard> aktivovat akci. <xref:System.Windows.Media.Animation.BeginStoryboard> Animace objektů a vlastností animace a spustí scénáři distribuuje. (Podrobnosti o tomto procesu najdete v tématu [animace a časování přehledu systému](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).) Pokud dáte <xref:System.Windows.Media.Animation.BeginStoryboard> název tak, že zadáte jeho <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> vlastnost, provedete to může ovládat scénáře. Pak můžete interaktivně ovládat scénáře po jeho spuštění. Následuje seznam akcí může ovládat scénáře pomocí aktivačních procedur událostí pro řízení scénáře.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Pozastaví scénáři.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Obnoví pozastavenou scénáře.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Změní scénáře rychlost.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Pokročilé funkce scénáře do konce doby výplň, má-li nějaký.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Zastaví scénáři.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Odebere scénáři.  
  
 V následujícím příkladu může ovládat scénáře akce slouží k interaktivní řízení scénáře.  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Interaktivní řízení scénáře pomocí kódu  
 V předchozích příkladech ukázaly, jak animovat pomocí aktivační události akcí. V kódu, můžete také řídit scénáře pomocí interaktivních metod <xref:System.Windows.Media.Animation.Storyboard> třídy. Pro <xref:System.Windows.Media.Animation.Storyboard> má být provedeno interaktivní v kódu, je nutné použít odpovídající přetížení do scénáře <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu a zadejte `true` k němu může ovládat. Zobrazit <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> stránky pro další informace.  
  
 Následující seznam obsahuje metody, které lze použít k manipulaci <xref:System.Windows.Media.Animation.Storyboard> po spuštění:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 Výhodou použití těchto metod je, že není nutné vytvořit <xref:System.Windows.Trigger> nebo <xref:System.Windows.TriggerAction> objektů; je třeba odkaz na dát řídit <xref:System.Windows.Media.Animation.Storyboard> chcete pracovat.  
  
 **Poznámka:** Všechny interaktivní akcí provedených ve <xref:System.Windows.Media.Animation.Clock>a proto také na <xref:System.Windows.Media.Animation.Storyboard> dojde u další značky časování modul, který se stane, krátce před další metodou render. Například, pokud použijete <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metoda pro přechod na jiném místě animace, hodnota vlastnosti nezmění okamžitě, místo, hodnota se změní na další značky modul časování.  
  
 Následující příklad ukazuje, jak použít a řízení animací použitím interaktivních metod <xref:System.Windows.Media.Animation.Storyboard> třídy.  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>Animace ve stylu  
 Můžete použít <xref:System.Windows.Media.Animation.Storyboard> objektů definovat animací <xref:System.Windows.Style>. Animace s <xref:System.Windows.Media.Animation.Storyboard> v <xref:System.Windows.Style> podobá se to používání <xref:System.Windows.Media.Animation.Storyboard> jinde, s následujícími třemi výjimkami:  
  
-   Nezadáte <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; <xref:System.Windows.Media.Animation.Storyboard> vždy cílí na element, ke kterému <xref:System.Windows.Style> platí. K cíli <xref:System.Windows.Freezable> objekty, je nutné použít nepřímé cílení. Další informace o nepřímé zaměření, najdete v článku [nepřímé cílení](#pathsyntaxforchangeable) oddílu.  
  
-   Nelze zadat <xref:System.Windows.EventTrigger.SourceName%2A> pro <xref:System.Windows.EventTrigger> nebo <xref:System.Windows.Trigger>.  
  
-   Dynamický prostředek odkazy nebo data vazbové výrazy nelze použít k nastavení <xref:System.Windows.Media.Animation.Storyboard> nebo hodnot vlastností animace. Důvodem je, že všechno, co je uvnitř <xref:System.Windows.Style> musí být bezpečná pro vlákno, a systému časování musíte <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> objekty tak, aby byly bezpečné pro vlákna. A <xref:System.Windows.Media.Animation.Storyboard> nelze zmrazit, pokud ho nebo jeho podřízených časových os obsahují vazby výrazů dynamický prostředek odkazy nebo data. Další informace o mrazu a dalších <xref:System.Windows.Freezable> funkce, najdete v článku [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nelze deklarovat obslužné rutiny událostí pro <xref:System.Windows.Media.Animation.Storyboard> nebo události animace.  
  
 Příklad ukazuje, jak definovat ve stylu ve scénáři, najdete v článku [animace ve stylu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md) příklad.  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>Animace v objektu ControlTemplate  
 Můžete použít <xref:System.Windows.Media.Animation.Storyboard> objektů definovat animací <xref:System.Windows.Controls.ControlTemplate>. Animace s <xref:System.Windows.Media.Animation.Storyboard> v <xref:System.Windows.Controls.ControlTemplate> podobá se to používání <xref:System.Windows.Media.Animation.Storyboard> jinde, s následujícími dvěma výjimkami:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Mohou odkazovat pouze na podřízené objekty <xref:System.Windows.Controls.ControlTemplate>. Pokud <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> není zadán, animace, zaměřuje elementu, do kterého <xref:System.Windows.Controls.ControlTemplate> platí.  
  
-   <xref:System.Windows.EventTrigger.SourceName%2A> Pro <xref:System.Windows.EventTrigger> nebo <xref:System.Windows.Trigger> mohou odkazovat pouze na podřízené objekty <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Dynamický prostředek odkazy nebo data vazbové výrazy nelze použít k nastavení <xref:System.Windows.Media.Animation.Storyboard> nebo hodnot vlastností animace. Důvodem je, že všechno, co je uvnitř <xref:System.Windows.Controls.ControlTemplate> musí být bezpečná pro vlákno, a systému časování musíte <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> objekty tak, aby byly bezpečné pro vlákna. A <xref:System.Windows.Media.Animation.Storyboard> nelze zmrazit, pokud ho nebo jeho podřízených časových os obsahují vazby výrazů dynamický prostředek odkazy nebo data. Další informace o mrazu a dalších <xref:System.Windows.Freezable> funkce, najdete v článku [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nelze deklarovat obslužné rutiny událostí pro <xref:System.Windows.Media.Animation.Storyboard> nebo události animace.  
  
 Příklad ukazuje, jak definovat scénáře v <xref:System.Windows.Controls.ControlTemplate>, najdete v článku [animace v objektu ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md) příklad.  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>Animace při změně hodnoty vlastnosti  
 Styly a šablony ovládacích prvků můžete použít aktivační událost objektů spustit scénář, když se změní vlastnost. Příklady najdete v tématu [aktivovat animace při změně hodnoty vlastnosti](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md) a [animace v objektu ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md).  
  
 Animace použít vlastností <xref:System.Windows.Trigger> objekty se chovají způsobem složitější než <xref:System.Windows.EventTrigger> animace nebo animace spuštěna pomocí <xref:System.Windows.Media.Animation.Storyboard> metody.  Jsou "předání" s použitím animací definované jinými <xref:System.Windows.Trigger> objekty, ale compose s <xref:System.Windows.EventTrigger> a aktivaci metody animace.  
  
## <a name="see-also"></a>Viz také:
- [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Přehled způsobů animace vlastností](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
- [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
