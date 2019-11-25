---
title: Přehled vlastností závislosti
description: Vlastnost, která je zajištěna systémem vlastností WPF, je známá jako vlastnost závislosti. Tento přehled popisuje systém vlastností WPF a možnosti vlastnosti závislosti.
ms.date: 06/06/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], attached
- properties [WPF], overview
- styles [WPF]
- attached properties [WPF]
- data binding [WPF]
- dependency properties [WPF]
- resources [WPF], references to
ms.assetid: d119d00c-3afb-48d6-87a0-c4da4f83dee5
ms.openlocfilehash: 5803d656d765f3f4fe3039e28b9c06202218fcfc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973990"
---
# <a name="dependency-properties-overview"></a>Přehled vlastností závislosti

Windows Presentation Foundation (WPF) poskytuje sadu služeb, které lze použít k rozšiřování funkcí [vlastnosti](../../../standard/base-types/common-type-system.md#Properties)typu. Souhrnně se tyto služby obvykle označují jako systém vlastností WPF. Vlastnost, která je zajištěna systémem vlastností WPF, je známá jako vlastnost závislosti. Tento přehled popisuje systém vlastností WPF a možnosti vlastnosti závislosti. To zahrnuje způsob použití existujících vlastností závislosti v jazyce XAML a v kódu. Tento přehled obsahuje taky specializované aspekty vlastností závislosti, jako jsou metadata vlastností závislosti, a postup vytvoření vlastní vlastnosti závislosti ve vlastní třídě.

## <a name="prerequisites"></a>Požadavky
V tomto tématu se předpokládá, že máte základní znalosti typu .NET System a objektově orientovaného programování. Aby bylo možné postupovat podle příkladů v tomto tématu, měli byste také pochopit XAML a vědět, jak psát aplikace WPF. Další informace najdete v tématu [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Vlastnosti závislosti a vlastnosti CLR
 Ve WPF se vlastnosti obvykle zveřejňují jako standardní [vlastnosti](../../../standard/base-types/common-type-system.md#Properties)rozhraní .NET. Na základní úrovni můžete s těmito vlastnostmi pracovat přímo a nikdy neznáte, že jsou implementované jako vlastnost závislosti. Měli byste však být obeznámeni s některými nebo všemi funkcemi systému vlastností WPF, abyste mohli využít výhod těchto funkcí.

Účelem vlastností závislosti je poskytnout způsob, jak vypočítat hodnotu vlastnosti na základě hodnoty jiných vstupů. Tyto další vstupy můžou zahrnovat systémové vlastnosti, jako jsou například motivy a preference uživatele, mechanismy určení vlastností za běhu, jako jsou datové vazby a animace/scénáře, šablony s více podobami použití, například prostředky a styly nebo známé hodnoty. pomocí vztahů nadřazenosti a podřízenosti s dalšími prvky ve stromu elementu. Kromě toho je možné implementovat vlastnost závislosti k poskytnutí samostatného ověřování, výchozích hodnot, zpětných volání, která sledují změny v jiných vlastnostech, a systému, který může převést hodnoty vlastností na základě potenciálně běhových informací. Odvozené třídy mohou také změnit některé konkrétní charakteristiky existující vlastnosti pomocí přepsání metadat vlastností závislosti namísto přepsání skutečné implementace existujících vlastností nebo vytváření nových vlastností.

V referenčních informacích k sadě SDK můžete určit, která vlastnost je vlastností závislosti, podle přítomnosti části informace o vlastnostech závislosti na spravované referenční stránce pro danou vlastnost. Oddíl informace o vlastnostech závislosti obsahuje odkaz na pole identifikátoru <xref:System.Windows.DependencyProperty> pro danou vlastnost závislosti a také obsahuje seznam možností metadat, které jsou nastaveny pro danou vlastnost, informace o přepsání jednotlivých tříd a další podrobnosti.

## <a name="dependency-properties-back-clr-properties"></a>Vlastnosti závislosti – vlastnosti zpětného CLR
Vlastnosti závislostí a systém vlastností WPF – funkce rozšířené vlastnosti poskytují typ, který vrátí vlastnost, jako alternativní implementaci standardního vzoru zálohování vlastnosti s privátním polem. Název tohoto typu je <xref:System.Windows.DependencyProperty>. Dalším důležitým typem, který definuje systém vlastností WPF, je <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject> definuje základní třídu, která může registrovat a vlastnit vlastnost závislosti.

Následující seznam obsahuje terminologii, která se používá s vlastnostmi závislosti:

- **Vlastnost závislosti:** Vlastnost, která je zazálohována <xref:System.Windows.DependencyProperty>.

- **Identifikátor vlastnosti závislosti:** Instance <xref:System.Windows.DependencyProperty>, která se získá jako návratová hodnota při registraci vlastnosti závislosti, a pak se uloží jako statický člen třídy. Tento identifikátor se používá jako parametr pro mnoho rozhraní API, která pracují se systémem vlastností WPF.

- **CLR "Obálka":** Skutečné implementace Get a set pro vlastnost. Tyto implementace zahrnují identifikátor vlastnosti závislosti jeho použitím v <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> volání, čímž se poskytuje zálohování pro vlastnost pomocí systému vlastností WPF.

Následující příklad definuje vlastnost závislosti `IsSpinning` a zobrazuje vztah <xref:System.Windows.DependencyProperty> identifikátoru k vlastnosti, kterou vrátí.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Zásady vytváření názvů vlastností a pole pro jeho <xref:System.Windows.DependencyProperty> jsou důležité. Název pole je vždy název vlastnosti, kde je přípona `Property` připojena. Další informace o této konvenci a jejich příčinách najdete v tématu [vlastnosti vlastních závislostí](custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Nastavení hodnot vlastností
Vlastnosti lze nastavit buď v kódu, nebo v jazyce XAML.

### <a name="setting-property-values-in-xaml"></a>Nastavení hodnot vlastností v jazyce XAML 
Následující příklad XAML Určuje barvu pozadí tlačítka jako červené. Tento příklad ukazuje případ, kde je jednoduchá řetězcová hodnota pro atribut XAML typu převáděná analyzátorem XAML WPF na typ WPF (<xref:System.Windows.Media.Color>, v <xref:System.Windows.Media.SolidColorBrush>) ve vygenerovaném kódu.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML podporuje nejrůznější formy syntaxe pro nastavení vlastností. Která syntaxe má být použita pro konkrétní vlastnost, bude záviset na typu hodnoty, který vlastnost používá, a také na dalších faktorech, jako je přítomnost konvertoru typu. Další informace o syntaxi jazyka XAML pro nastavení vlastnosti naleznete v tématu detailed [XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) a [syntaxe jazyka XAML](xaml-syntax-in-detail.md).

Jako příklad syntaxe bez atributů ukazuje následující příklad XAML další pozadí tlačítka. Místo toho, aby se nastavila jednoduchá plná barva, je pozadí nastaveno na obrázek, s prvkem, který představuje tento obrázek, a zdrojem tohoto obrázku zadaného jako atribut vnořeného prvku. Toto je příklad syntaxe prvku vlastnosti.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Nastavení vlastností v kódu
 Nastavení hodnot vlastností závislosti v kódu je obvykle pouze voláním implementace množiny vystavené obálkou CLR.

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Získání hodnoty vlastnosti je také v podstatě voláním implementace "Obálka":

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Můžete také volat rozhraní API systému vlastností <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> přímo. To není obvykle nutné v případě, že používáte existující vlastnosti (obálky jsou užitečnější a poskytují lepší expozici vlastnosti pro vývojářské nástroje), ale volání rozhraní API je vhodné pro určité scénáře.

Vlastnosti lze také nastavit v jazyce XAML a následně je použít později v kódu, a to prostřednictvím kódu na pozadí. Podrobnosti najdete v tématu [Code-na pozadí a XAML v WPF](code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Funkce vlastnosti poskytované vlastností závislosti
Vlastnost závislosti poskytuje funkce, které rozšiřují funkce vlastnosti na rozdíl od vlastnosti, která je zajištěna polem. Tyto funkce často představují nebo podporují jednu z následujících specifických funkcí:

- [Prostředky](#resources)

- [Datová vazba](#data-binding)

- [Styly](#styles)

- [Animace](#animations)

- [Přepsání metadat](#metadata-overrides)

- [Dědičnost hodnoty vlastnosti](#property-value-inheritance)

- [Integrace návrháře WPF](#wpf-designer-integration)

### <a name="resources"></a>Prostředky
Hodnotu vlastnosti závislosti lze nastavit odkazem na prostředek. Prostředky se obvykle zadává jako hodnota vlastnosti `Resources` kořenového elementu stránky nebo aplikace (Tato umístění umožňují nejpohodlnější přístup k prostředku). Následující příklad ukazuje, jak definovat prostředek <xref:System.Windows.Media.SolidColorBrush>.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Po definování prostředku můžete na prostředek odkazovat a použít ho k poskytnutí hodnoty vlastnosti:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Na tento konkrétní prostředek se odkazuje jako na [DynamicResource Markup Extension](dynamicresource-markup-extension.md) (v jazyce WPF XAML, můžete použít buď statický, nebo dynamický odkaz na prostředek). Chcete-li použít dynamický odkaz na prostředek, musíte být nastaven na vlastnost závislosti, takže je konkrétně použití dynamického odkazu prostředku, které je povoleno systémem vlastností WPF. Další informace naleznete v tématu [prostředky XAML](xaml-resources.md).

> [!NOTE]
> Prostředky se považují za místní hodnotu, což znamená, že pokud nastavíte jinou místní hodnotu, odstraní se odkaz na prostředek. Další informace najdete v tématu [Priorita hodnoty vlastností závislosti](dependency-property-value-precedence.md).

### <a name="data-binding"></a>Datová vazba
Vlastnost závislosti může odkazovat na hodnotu prostřednictvím datové vazby. Datové vazby fungují v rámci specifické syntaxe rozšíření značek v jazyce XAML nebo objektu <xref:System.Windows.Data.Binding> v kódu. S datovou vazbou je konečné určení hodnoty vlastnosti odloženo až do doby spuštění, kdy je hodnota získána ze zdroje dat.

Následující příklad nastaví vlastnost <xref:System.Windows.Controls.ContentControl.Content%2A> pro <xref:System.Windows.Controls.Button>pomocí vazby deklarované v jazyce XAML. Vazba používá zděděný kontext dat a <xref:System.Windows.Data.XmlDataProvider> zdroj dat (nezobrazený). Vazba sama Určuje požadovanou zdrojovou vlastnost <xref:System.Windows.Data.Binding.XPath%2A> v rámci zdroje dat.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Vazby jsou považovány za místní hodnotu, což znamená, že pokud nastavíte jinou místní hodnotu, budete vazbu eliminovat. Podrobnosti najdete v tématu [Priorita hodnoty vlastností závislosti](dependency-property-value-precedence.md).

Vlastnosti závislosti nebo třída <xref:System.Windows.DependencyObject> nepodporují nativně <xref:System.ComponentModel.INotifyPropertyChanged> pro účely vytváření oznámení o změnách v <xref:System.Windows.DependencyObject> hodnotě vlastnosti zdroje pro operace datové vazby. Další informace o tom, jak vytvořit vlastnosti pro použití v datové vazbě, které mohou nahlásit změny v cíli datové vazby, najdete v tématu [Přehled datové vazby](../data/data-binding-overview.md).

### <a name="styles"></a>Styly
Styly a šablony jsou dva ze scénářů hlavní motivace pro použití vlastností závislosti. Styly jsou zvláště užitečné pro nastavení vlastností, které definují [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]aplikace. Styly jsou obvykle definovány jako prostředky v jazyce XAML. Styly spolupracují se systémem vlastností, protože obvykle obsahují "metody setter" pro konkrétní vlastnosti a také "triggery", které mění hodnotu vlastnosti na základě hodnoty v reálném čase pro jinou vlastnost.

Následující příklad vytvoří velmi jednoduchý styl (který by byl definován uvnitř <xref:System.Windows.FrameworkElement.Resources%2A> slovníku, není zobrazen), pak použije tento styl přímo na vlastnost <xref:System.Windows.FrameworkElement.Style%2A> pro <xref:System.Windows.Controls.Button>. Metoda setter v rámci stylu nastavuje vlastnost <xref:System.Windows.Controls.Control.Background%2A> pro styl <xref:System.Windows.Controls.Button> na zelenou.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Další informace najdete v tématu [stylování a šablonování](../controls/styling-and-templating.md).

### <a name="animations"></a>Animace
Vlastnosti závislosti můžou být animované. Při použití animace a jejím spuštění funguje animovaná hodnota s vyšší prioritou než libovolná hodnota (například místní hodnota), kterou vlastnost jinak má.

Následující příklad animuje <xref:System.Windows.Controls.Control.Background%2A> vlastnosti <xref:System.Windows.Controls.Button> (technicky, <xref:System.Windows.Controls.Control.Background%2A> je animovaný pomocí syntaxe elementu Property k určení prázdného <xref:System.Windows.Media.SolidColorBrush> jako <xref:System.Windows.Controls.Control.Background%2A>, pak vlastnost <xref:System.Windows.Media.SolidColorBrush.Color%2A> tohoto <xref:System.Windows.Media.SolidColorBrush> je vlastnost, která je přímo animovaná).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Další informace o animování vlastností naleznete v tématu Přehled [animace](../graphics-multimedia/animation-overview.md) a [Přehled scénářů](../graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Přepsání metadat
Můžete změnit určité chování vlastnosti závislosti přepsáním metadat pro tuto vlastnost při odvozování od třídy, která původně registruje vlastnost závislosti. Přepsání metadat závisí na identifikátoru <xref:System.Windows.DependencyProperty>. Přepsání metadat nevyžaduje znovu implementaci vlastnosti. Změny metadat jsou zpracovávány nativním systémem vlastností. Každá třída potenciálně uchovává jednotlivá metadata pro všechny vlastnosti, které jsou zděděny ze základních tříd, na základě typu.

Následující příklad přepisuje metadata pro vlastnost závislosti <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. Přepsání těchto metadat vlastností závislosti je součástí vzoru implementace, který vytváří ovládací prvky, které mohou používat výchozí styly z motivů.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Další informace o přepsání nebo získání metadat vlastností naleznete v tématu [metadata vlastnosti závislosti](dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Dědičnost hodnoty vlastnosti
Element může dědit hodnotu vlastnosti závislosti ze své nadřazené položky ve stromové struktuře objektů.

> [!NOTE]
> Chování dědičnosti hodnoty vlastností není globálně povoleno pro všechny vlastnosti závislosti, protože čas výpočtu dědičnosti má vliv na výkon. Dědičnost hodnoty vlastnosti je obvykle povolena pouze pro vlastnosti, kde konkrétní scénář naznačuje, že je dědičnost hodnoty vlastnosti vhodná. To, jestli vlastnost závislosti dědí, můžete zjistit tak, že v odkazu na sadu SDK prohlížíte část **informace o vlastnosti závislosti** pro tuto vlastnost závislosti.

Následující příklad ukazuje vazbu a nastavuje vlastnost <xref:System.Windows.FrameworkElement.DataContext%2A>, která určuje zdroj vazby, který nebyl zobrazen v předchozím příkladu vazby. Jakékoli následné vazby v podřízených objektech nemusejí určovat zdroj, můžou použít zděděnou hodnotu z <xref:System.Windows.FrameworkElement.DataContext%2A> v nadřazeném objektu <xref:System.Windows.Controls.StackPanel>. (Případně může podřízený objekt místo toho zvolit přímé určení vlastního <xref:System.Windows.FrameworkElement.DataContext%2A> nebo <xref:System.Windows.Data.Binding.Source%2A> v <xref:System.Windows.Data.Binding>a záměrně nepoužívat zděděnou hodnotu pro kontext dat jeho vazeb.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Další informace najdete v tématu [Dědičnost hodnot vlastností](property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Integrace návrháře WPF
Vlastní ovládací prvek s vlastnostmi, které jsou implementovány jako vlastnosti závislosti, obdrží vhodného návrháře WPF pro podporu sady Visual Studio. Jedním z příkladů je možnost upravovat vlastnosti přímé a připojené závislosti v okně **vlastnosti** . Další informace najdete v tématu [Přehled tvorby řízení](../controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Priorita hodnoty vlastnosti závislosti
Po získání hodnoty vlastnosti závislosti můžete potenciálně získat hodnotu, která byla nastavena na danou vlastnost prostřednictvím jakékoli jiné vstupy založené na vlastnostech, které se účastní systému vlastností WPF. Priorita hodnoty vlastnosti závislosti existuje, takže celá řada scénářů, jak vlastnosti získají jejich hodnoty, může popracovat předvídatelným způsobem.

Vezměte v úvahu následující příklad. Příklad obsahuje styl, který se vztahuje na všechna tlačítka a jejich <xref:System.Windows.Controls.Control.Background%2A> vlastnosti, ale pak také určuje jedno tlačítko s lokálně nastavenou <xref:System.Windows.Controls.Control.Background%2A> hodnotou.

> [!NOTE]
> Dokumentace k sadě SDK používá při diskusích na vlastnosti závislosti výrazy "místní hodnota" nebo "místně nastavenou hodnotu". Místně nastavená hodnota je hodnota vlastnosti, která je nastavena přímo na instanci objektu v kódu nebo jako atribut u prvku v jazyce XAML.  
  
V zásadě pro první tlačítko je vlastnost nastavena dvakrát, ale je použita pouze jedna hodnota: hodnota s nejvyšší prioritou. Místně nastavená hodnota má nejvyšší prioritu (kromě spuštěné animace, ale v tomto příkladu se nepoužívá žádná animace), a proto se místo hodnoty setter stylu pro pozadí na prvním tlačítku použije hodnota v místním nastavení. Druhé tlačítko nemá žádnou místní hodnotu (a nemá žádnou jinou hodnotu s vyšší prioritou než Style setter), a proto pozadí v tomto tlačítku pochází z setter Style.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Proč existuje priorita vlastnosti závislosti?
Obvykle byste neměli chtít, aby styly vždy používaly a zakrývaly i lokálně nastavenou hodnotu jednotlivého prvku (jinak by bylo velmi obtížné použít buď styly nebo prvky obecně). Proto hodnoty, které pocházejí z stylů, pracují s nižším předchůdcem než s lokálně nastavenou hodnotou. Podrobnější výpis vlastností závislosti a umístění, ze kterého může pocházet efektivní hodnota vlastnosti závislosti, najdete v tématu [Priorita hodnoty vlastností závislosti](dependency-property-value-precedence.md).

> [!NOTE]
> Pro elementy WPF, které nejsou vlastnosti závislostí, je definováno několik vlastností. Po a velkými, byly vlastnosti implementovány jako vlastnosti závislosti pouze v případě, že bylo nutné podporovat alespoň jeden z scénářů, které jsou povoleny v systému vlastností: datové vazby, styly, animace, výchozí podpora hodnot, dědičnost, připojené vlastnosti nebo zneplatnění.

## <a name="learning-more-about-dependency-properties"></a>Více informací o vlastnostech závislosti  

- Připojená vlastnost je typ vlastnosti, která podporuje specializovanou syntaxi v jazyce XAML. Přidružená vlastnost často neobsahuje 1:1 korespondence s vlastností Common Language Runtime (CLR) a není nutně vlastností závislosti. Typickým účelem připojené vlastnosti je povolit podřízeným elementům nahlásit hodnoty vlastností nadřazenému prvku, i když nadřazený element a podřízený element nedisponují touto vlastností jako součást výpisu členů třídy. Jedním z primárních scénářů je povolit podřízeným elementům informování nadřazeného prvku, jak by měly být prezentovány v [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; Příklad naleznete v tématu <xref:System.Windows.Controls.DockPanel.Dock%2A> nebo <xref:System.Windows.Controls.Canvas.Left%2A>. Podrobnosti najdete v tématu [připojené vlastnosti – přehled](attached-properties-overview.md).

- Vývojáři komponent nebo vývojáři aplikací mohou chtít vytvořit vlastní vlastnost závislosti, aby bylo možné povolit funkce, jako je například podpora datových vazeb nebo stylů, nebo pro zajištění neplatnosti a podpory pro vynucení hodnoty. Podrobnosti najdete v tématu [vlastnosti vlastních závislostí](custom-dependency-properties.md).

- Vlastnosti závislosti by se obecně měly považovat za veřejné vlastnosti, přístupné nebo aspoň zjistitelné jakýmkoli volajícím, který má přístup k instanci. Další informace najdete v tématu [zabezpečení vlastností závislosti](dependency-property-security.md).

## <a name="see-also"></a>Viz také:

- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Vlastnosti závislosti jen pro čtení](read-only-dependency-properties.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Architektura WPF](wpf-architecture.md)
