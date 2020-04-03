---
title: Přehled vlastností závislostí
description: Vlastnost, která je zálohována systémem vlastností WPF, se označuje jako vlastnost závislosti. Tento přehled popisuje systém vlastností WPF a možnosti vlastnosti závislosti.
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
ms.openlocfilehash: 542e0a84e4c5cfc3750c33fe29cb40d3643e91e3
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80636029"
---
# <a name="dependency-properties-overview"></a>Přehled vlastností závislostí

Windows Presentation Foundation (WPF) poskytuje sadu služeb, které lze použít k rozšíření funkce [vlastnosti](../../../standard/base-types/common-type-system.md#properties)typu . Společně tyto služby jsou obvykle označovány jako wpf systém vlastností. Vlastnost, která je zálohována systémem vlastností WPF, se označuje jako vlastnost závislosti. Tento přehled popisuje systém vlastností WPF a možnosti vlastnosti závislosti. To zahrnuje použití existujících vlastností závislostí v XAML a v kódu. Tento přehled také zavádí specializované aspekty vlastností závislostí, jako jsou metadata vlastností závislostí a jak vytvořit vlastní vlastnost závislostí ve vlastní třídě.

## <a name="prerequisites"></a>Požadavky
Toto téma předpokládá, že máte některé základní znalosti systému typu .NET a objektově orientované programování. Chcete-li sledovat příklady v tomto tématu, měli byste také pochopit XAML a vědět, jak psát aplikace WPF. Další informace naleznete [v tématu Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Vlastnosti závislostí a vlastnosti CLR
 V WPF vlastnosti jsou obvykle vystaveny jako standardní [vlastnosti](../../../standard/base-types/common-type-system.md#properties).NET . Na základní úrovni můžete komunikovat s těmito vlastnostmi přímo a nikdy nevíte, že jsou implementovány jako vlastnost závislosti. Měli byste se však seznámit s některými nebo všemi funkcemi systému vlastností WPF, abyste mohli tyto funkce využít.

Účelem vlastností závislostí je poskytnout způsob, jak vypočítat hodnotu vlastnosti na základě hodnoty jiných vstupů. Tyto další vstupy mohou zahrnovat vlastnosti systému, jako jsou motivy a uživatelské předvolby, mechanismy určení vlastností just-in-time, jako jsou datové vazby a animace/scénáře, šablony pro více použití, jako jsou prostředky a styly, nebo hodnoty známé prostřednictvím vztahů nadřazený-podřízený s jinými prvky ve stromu prvků. Kromě toho lze implementovat vlastnost závislosti, která poskytuje samostatné ověření, výchozí hodnoty, zpětná volání, která sledují změny jiných vlastností, a systém, který může dosáhovat hodnoty vlastností na základě potenciálně informací o běhu. Odvozené třídy můžete také změnit některé specifické charakteristiky existující vlastnosti přepsáním metadat vlastnosti závislost, spíše než přepsání skutečné implementace existujících vlastností nebo vytváření nových vlastností.

V odkazu sady SDK můžete určit, která vlastnost je vlastnost závislostí podle přítomnosti části Informace o vlastnostech závislostí na spravované referenční stránce pro tuto vlastnost. Část Informace o vlastnostech závislostí <xref:System.Windows.DependencyProperty> obsahuje odkaz na pole identifikátoru pro tuto vlastnost závislosti a také seznam možností metadat, které jsou nastaveny pro tuto vlastnost, informace o přepsání na třídu a další podrobnosti.

## <a name="dependency-properties-back-clr-properties"></a>Vlastnosti závislostí zpět CLR vlastnosti
Vlastnosti závislostí a systém vlastností WPF rozšiřují funkce vlastností poskytnutím typu, který podporuje vlastnost, jako alternativní implementaci standardního vzoru zálohování vlastnosti soukromým polem. Název tohoto typu <xref:System.Windows.DependencyProperty>je . Další důležitý typ, který definuje wpf <xref:System.Windows.DependencyObject>vlastnost systému je . <xref:System.Windows.DependencyObject>definuje základní třídu, která může registrovat a vlastnit vlastnost závislosti.

V následujícím seznamu je uvedena terminologie, která se používá s vlastnostmi závislostí:

- **Vlastnost závislostí:** Vlastnost, která je podpořena <xref:System.Windows.DependencyProperty>.

- **Identifikátor vlastnosti závislosti:** Instance, <xref:System.Windows.DependencyProperty> která je získána jako vrácená hodnota při registraci vlastnosti závislosti a poté uložena jako statický člen třídy. Tento identifikátor se používá jako parametr pro mnoho rozhraní API, které interagují se systémem vlastností WPF.

- **CLR "obálka":** Skutečné get a set implementace pro vlastnost. Tyto implementace začlenit identifikátor vlastnosti závislosti pomocí <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> v a volání, a tím poskytuje podporu pro vlastnost pomocí wpf systémvlastnosti.

Následující příklad definuje `IsSpinning` vlastnost závislosti a zobrazuje vztah <xref:System.Windows.DependencyProperty> identifikátoru k vlastnosti, kterou podporuje.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Konvence pojmenování vlastnosti a <xref:System.Windows.DependencyProperty> její záložní pole je důležité. Název pole je vždy název vlastnosti s připojenou `Property` příponou. Další informace o této konvenci a důvodech této konvence naleznete v [tématu Vlastnosti vlastních závislostí](custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Nastavení hodnot vlastností
Vlastnosti můžete nastavit buď v kódu, nebo v XAML.

### <a name="setting-property-values-in-xaml"></a>Nastavení hodnot vlastností v XAML
Následující příklad XAML určuje barvu pozadí tlačítka jako červenou. Tento příklad ilustruje případ, kdy je jednoduchá hodnota řetězce pro atribut XAML typu převedena analyzátorem WPF <xref:System.Windows.Media.Color>XAML na <xref:System.Windows.Media.SolidColorBrush>typ WPF (a , prostřednictvím ) v generovaném kódu.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML podporuje různé syntaktické formuláře pro nastavení vlastností. Syntaxe, která má být pro určitou vlastnost, bude záviset na typu hodnoty, který vlastnost používá, a také na dalších faktorech, jako je například přítomnost převaděče typu. Další informace o syntaxi XAML pro nastavení vlastností naleznete v tématu [XAML Přehled (WPF)](../../../desktop-wpf/fundamentals/xaml.md) a [Syntaxe XAML podrobně .](xaml-syntax-in-detail.md)

Jako příklad syntaxe bez atributů následující příklad XAML ukazuje další pozadí tlačítka. Tentokrát místo nastavení jednoduché plné barvy je pozadí nastaveno na obrázek, přičemž prvek reprezentující tento obraz a zdroj tohoto obrazu je určen jako atribut vnořeného prvku. Toto je příklad syntaxe prvku vlastnosti.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Nastavení vlastností v kódu
 Nastavení hodnoty vlastností závislostí v kódu je obvykle pouze volání set implementace vystavené CLR "obálka".

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Získání hodnoty vlastnosti je také v podstatě volání get "obálka" implementace:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Můžete také volat zařízení API <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> systému vlastností a přímo. To není obvykle nutné, pokud používáte existující vlastnosti (obálky jsou pohodlnější a poskytují lepší expozici vlastnosti pro vývojářské nástroje), ale volání rozhraní API přímo je vhodné pro určité scénáře.

Vlastnosti lze také nastavit v XAML a později přistupovat později v kódu, prostřednictvím kódu na pozadí. Podrobnosti naleznete v [tématu Code-Behind a XAML v WPF](code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Funkce vlastností poskytovaná vlastností závislostí
Vlastnost závislosti poskytuje funkce, které rozšiřuje funkce vlastnosti na rozdíl od vlastnosti, která je zálohována polem. Tyto funkce často představují nebo podporují jednu z následujících specifických funkcí:

- [Materiály](#resources)

- [Datová vazba](#data-binding)

- [Styly](#styles)

- [Animace](#animations)

- [Přepsání metadat](#metadata-overrides)

- [Dědičnost hodnoty vlastnosti](#property-value-inheritance)

- [Integrace návrháře WPF](#wpf-designer-integration)

### <a name="resources"></a>Prostředky
Hodnotu vlastnosti závislosti lze nastavit odkazem na prostředek. Prostředky jsou obvykle určeny jako hodnota `Resources` vlastnosti kořenového prvku stránky nebo aplikace (tato umístění umožňují nejvhodnější přístup k prostředku). Následující příklad ukazuje, jak <xref:System.Windows.Media.SolidColorBrush> definovat prostředek.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Jakmile je prostředek definován, můžete na prostředek odkazovat a použít jej k zadání hodnoty vlastnosti:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Tento konkrétní prostředek je odkazován jako [rozšíření dynamicResource Markup Extension](dynamicresource-markup-extension.md) (v WPF XAML můžete použít statický nebo dynamický odkaz na prostředek). Chcete-li použít odkaz na dynamický prostředek, musíte nastavit vlastnost závislosti, takže se jedná konkrétně o využití odkazu na dynamický prostředek, které je povoleno systémem vlastností WPF. Další informace naleznete v tématu [XAML Resources](xaml-resources.md).

> [!NOTE]
> Prostředky jsou považovány za místní hodnotu, což znamená, že pokud nastavíte jinou místní hodnotu, odstraníte odkaz na prostředek. Další informace naleznete v [tématu Priorita hodnoty vlastnosti závislostí](dependency-property-value-precedence.md).

### <a name="data-binding"></a>Datová vazba
Vlastnost závislosti může odkazovat na hodnotu prostřednictvím datové vazby. Datová vazba funguje prostřednictvím syntaxe konkrétní horozšíření značek v XAML nebo objektu <xref:System.Windows.Data.Binding> v kódu. S datovou vazbou je určení konečné hodnoty vlastnosti odloženo až do doby spuštění, kdy je hodnota získána ze zdroje dat.

Následující příklad nastaví <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button>pro , pomocí vazby deklarované v XAML. Vazba používá zděděný <xref:System.Windows.Data.XmlDataProvider> kontext dat a zdroj dat (není zobrazen). Samotná vazba určuje vlastnost <xref:System.Windows.Data.Binding.XPath%2A> požadovaného zdroje v rámci zdroje dat.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Vazby jsou považovány za místní hodnotu, což znamená, že pokud nastavíte jinou místní hodnotu, odstraníte vazbu. Podrobnosti naleznete v [tématu Priorita hodnoty vlastnosti závislostí](dependency-property-value-precedence.md).

Vlastnosti závislostí <xref:System.Windows.DependencyObject> nebo třída nejsou nativně podporují <xref:System.ComponentModel.INotifyPropertyChanged> pro účely vytváření <xref:System.Windows.DependencyObject> oznámení o změnách hodnoty vlastnosti zdroj pro operace datové vazby. Další informace o tom, jak vytvořit vlastnosti pro použití v datové vazbě, které mohou vykazovat změny cíle datové vazby, naleznete v [tématu Přehled datové vazby](../data/data-binding-overview.md).

### <a name="styles"></a>Styly
Styly a šablony jsou dva hlavní motivující scénáře pro použití vlastností závislostí. Styly jsou užitečné zejména pro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]nastavení vlastností, které definují aplikaci . Styly jsou obvykle definovány jako prostředky v XAML. Styly interagují se systémem vlastností, protože obvykle obsahují "setters" pro určité vlastnosti, stejně jako "aktivační události", které mění hodnotu vlastnosti na základě hodnoty v reálném čase pro jinou vlastnost.

Následující příklad vytvoří jednoduchý styl (který by <xref:System.Windows.FrameworkElement.Resources%2A> byl definován uvnitř slovníku, není zobrazen), pak použije tento styl přímo na <xref:System.Windows.FrameworkElement.Style%2A> vlastnost pro <xref:System.Windows.Controls.Button>. Setter ve stylu nastaví <xref:System.Windows.Controls.Control.Background%2A> vlastnost pro <xref:System.Windows.Controls.Button> stylované na zelenou.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Další informace naleznete [v tématu Styling a Templating](../controls/styling-and-templating.md).

### <a name="animations"></a>Animace
Vlastnosti závislostí lze animovat. Při použití animace a je spuštěna, animovaná hodnota pracuje s vyšší prioritou než libovolná hodnota (například místní hodnota), která jinak vlastnost má.

Následující <xref:System.Windows.Controls.Control.Background%2A> příklad animuje <xref:System.Windows.Controls.Button> na <xref:System.Windows.Controls.Control.Background%2A> vlastnost (technicky je animovaný pomocí syntaxe <xref:System.Windows.Media.SolidColorBrush> elementu <xref:System.Windows.Controls.Control.Background%2A>vlastnosti <xref:System.Windows.Media.SolidColorBrush.Color%2A> k <xref:System.Windows.Media.SolidColorBrush> určení prázdné jako , pak vlastnost, která je vlastnost, která je přímo animovaný).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Další informace o animování vlastností naleznete v [tématu Přehled animací](../graphics-multimedia/animation-overview.md) a [Přehled scénářů](../graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Přepsání metadat
Určitá chování vlastnosti závislosti můžete změnit přepsáním metadat pro tuto vlastnost, když odvozujete z třídy, která původně registruje vlastnost závislosti. Přepsání metadat závisí <xref:System.Windows.DependencyProperty> na identifikátoru. Přepsání metadat nevyžaduje opětovné provedení vlastnosti. Změna metadat je zpracována nativně systémem vlastností; každá třída potenciálně obsahuje jednotlivá metadata pro všechny vlastnosti, které jsou zděděny ze základních tříd, na základě typu.

Následující příklad přepíše metadata vlastnosti <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>závislosti . Přepsání metadat vlastnosti této konkrétní závislosti je součástí vzoru implementace, který vytváří ovládací prvky, které mohou používat výchozí styly z motivů.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Další informace o přepsání nebo získání metadat vlastnosti naleznete v [tématu Metadata vlastností závislostí](dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Dědičnost hodnoty vlastnosti
Prvek může dědit hodnotu vlastnosti závislosti z nadřazené položky ve stromu objektů.

> [!NOTE]
> Chování dědičnosti hodnoty vlastnosti není globálně povoleno pro všechny vlastnosti závislostí, protože doba výpočtu dědičnosti má určitý dopad na výkon. Dědičnost hodnoty vlastnosti je obvykle povolena pouze pro vlastnosti, kde konkrétní scénář naznačuje, že dědičnost hodnoty vlastnosti je vhodná. Můžete určit, zda vlastnost závislost dědí pohledem na **informace o vlastnosti závislostí** pro tuto vlastnost závislosti v odkazu sdk.

Následující příklad ukazuje vazbu a <xref:System.Windows.FrameworkElement.DataContext%2A> nastaví vlastnost, která určuje zdroj vazby, která nebyla uvedena v předchozím příkladu vazby. Všechny následné vazby v podřízených objektech nemusí určit zdroj, <xref:System.Windows.FrameworkElement.DataContext%2A> mohou použít <xref:System.Windows.Controls.StackPanel> zděděnou hodnotu z v nadřazeném objektu. (Alternativně podřízený objekt může místo toho <xref:System.Windows.FrameworkElement.DataContext%2A> zvolit <xref:System.Windows.Data.Binding.Source%2A> přímo <xref:System.Windows.Data.Binding>určit jeho vlastní nebo v , a záměrně nepoužívat zděděnou hodnotu pro kontext dat jeho vazby.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Další informace naleznete v [tématu Dědičnost hodnoty nemovitosti](property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Integrace návrháře WPF
Vlastní ovládací prvek s vlastnostmi, které jsou implementovány jako vlastnosti závislostí obdrží odpovídající WPF Designer pro podporu sady Visual Studio. Jedním z příkladů je možnost upravovat přímé a připojené vlastnosti závislostí s okno **Vlastnosti.** Další informace naleznete [v tématu Přehled vytváření ovládacích prvku](../controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Priorita hodnoty vlastnosti závislostí
Když získáte hodnotu vlastnosti závislosti, potenciálně získáváte hodnotu, která byla nastavena na tuto vlastnost prostřednictvím některého z dalších vstupů založených na vlastnostech, které se účastní systému vlastností WPF. Priorita hodnoty vlastnosti závislostí existuje tak, aby různé scénáře pro získání vlastností jejich hodnoty mohou komunikovat předvídatelným způsobem.

Představte si následující příklad. Příklad obsahuje styl, který platí pro <xref:System.Windows.Controls.Control.Background%2A> všechna tlačítka a jejich vlastnosti, ale <xref:System.Windows.Controls.Control.Background%2A> pak také určuje jedno tlačítko s místně nastavenou hodnotou.

> [!NOTE]
> Dokumentace sady SDK používá při diskusi o vlastnostech závislostí občas termíny "místní hodnota" nebo "místně nastavená hodnota". Místně nastavená hodnota je hodnota vlastnosti, která je nastavena přímo na instanci objektu v kódu nebo jako atribut prvku v XAML.  
  
V zásadě pro první tlačítko vlastnost je nastavena dvakrát, ale platí pouze jednu hodnotu: hodnota s nejvyšší prioritou. Místně nastavená hodnota má nejvyšší prioritu (s výjimkou spuštěné animace, ale v tomto příkladu se nepoužije žádná animace) a proto se místo hodnoty nastavení stylu pro pozadí na prvním tlačítku používá místně nastavená hodnota. Druhé tlačítko nemá žádnou místní hodnotu (a žádná jiná hodnota s vyšší prioritou než setter stylu) a pozadí v tomto tlačítku tedy pochází ze setteru stylu.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Proč existuje priorita vlastnosti závislostí?
Obvykle byste nechtěli, aby styly vždy platily a zakrývaly i místně nastavenou hodnotu jednotlivého prvku (jinak by bylo obtížné použít styly nebo prvky obecně). Proto hodnoty, které pocházejí ze stylů pracovat na nižší precedens než místně nastavenou hodnotu. Podrobnější seznam vlastností závislostí a odkud může pocházet efektivní hodnota vlastnosti závislostí, naleznete v [tématu Priorita hodnoty vlastnosti závislostí](dependency-property-value-precedence.md).

> [!NOTE]
> Existuje několik vlastností definovaných na WPF prvky, které nejsou vlastnosti závislostí. Z velké části vlastnosti byly implementovány jako vlastnosti závislostí pouze v případě, že bylo třeba podporovat alespoň jeden ze scénářů povolených systémem vlastností: datové vazby, styling, animace, výchozí podpora hodnoty, dědičnost, připojené vlastnosti nebo zneplatnění.

## <a name="learning-more-about-dependency-properties"></a>Další informace o vlastnostech závislostí  

- Připojená vlastnost je typ vlastnosti, která podporuje specializovanou syntaxi v XAML. Připojená vlastnost často nemá 1:1 korespondence s common jazyk runtime (CLR) vlastnost a není nutně závislost vlastnost. Typickým účelem připojené vlastnosti je umožnit podřízeným prvkům vykazovat hodnoty vlastností nadřazenému prvku, i když nadřazený prvek a podřízený prvek nemají tuto vlastnost jako součást výpisů členů třídy. Jedním z primárních scénářů je umožnit podřízeným [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]prvkům informovat nadřazené prvky, jak by měly být prezentovány v ; například viz <xref:System.Windows.Controls.DockPanel.Dock%2A> nebo <xref:System.Windows.Controls.Canvas.Left%2A>. Podrobnosti naleznete [v tématu Přehled připojených vlastností](attached-properties-overview.md).

- Vývojáři komponent nebo vývojáři aplikací mohou chtít vytvořit vlastní vlastnost závislosti, aby povolili funkce, jako je například podpora datové vazby nebo stylů, nebo pro podporu zneplatnění a podpory nátlaku na hodnotu. Podrobnosti naleznete [v tématu Vlastní vlastnosti závislostí](custom-dependency-properties.md).

- Vlastnosti závislostí jsou veřejné vlastnosti, přístupné nebo alespoň zjistitelné libovolným volajícím, který má přístup k instanci. Další informace naleznete [v tématu Zabezpečení vlastností závislostí](dependency-property-security.md).

## <a name="see-also"></a>Viz také

- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Vlastnosti závislosti jen pro čtení](read-only-dependency-properties.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Architektura WPF](wpf-architecture.md)
