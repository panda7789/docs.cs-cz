---
title: Přehled vlastností závislosti
description: Vlastnost, která je založená na systému vlastností WPF se označuje jako vlastnost závislosti. Tento přehled popisuje vlastnosti systému WPF a možnosti vlastnost závislosti.
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
ms.openlocfilehash: 7a7a8cc13a48b453b157443039f11c548756b0fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588649"
---
# <a name="dependency-properties-overview"></a>Přehled vlastností závislosti

Windows Presentation Foundation (WPF) nabízí sadu služeb, které lze použít k rozšíření funkčnosti typu [vlastnost](../../../standard/base-types/common-type-system.md#Properties). Společně tyto služby jsou obvykle označovány jako vlastnost systému WPF. Vlastnost, která je založená na systému vlastností WPF se označuje jako vlastnost závislosti. Tento přehled popisuje vlastnosti systému WPF a možnosti vlastnost závislosti. Jedná se o tom, jak používat vlastnosti existujícího závislosti v XAML a kódu. Tento přehled zavádí také speciální aspekty vlastnosti závislosti, jako je například metadata vlastností závislosti a jak vytvářet vlastní vlastnosti závislosti v rámci vlastní třídy.

## <a name="prerequisites"></a>Požadavky
Toto téma předpokládá, že máte některé základní znalosti o systému typů rozhraní .NET a objektově orientované programování. Pokud chcete postupovat podle příkladů v tomto tématu, potřebujete také pochopit XAML a vědět, jak psát aplikace WPF. Další informace najdete v tématu [názorný postup: Moje první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Vlastnosti závislostí a vlastnosti CLR
 V WPF vlastnosti obvykle vystavena jako standardní .NET [vlastnosti](../../../standard/base-types/common-type-system.md#Properties). Na základní úrovni může komunikovat přímo s těmito vlastnostmi a nikdy vědět, že jsou implementovány jako vlastnost závislosti. Však můžete byste se měli seznámit některé nebo všechny funkce v systému vlastností WPF, takže můžete využít tyto funkce.

Účelem vlastnosti závislostí je poskytnout způsob, jak vypočítat hodnotu vlastnosti na základě hodnoty ostatní vstupy. Tyto další vstupy může obsahovat vlastnosti systému, jako jsou motivy a uživatelské předvolby, vlastnost just-in-time stanovení mechanismy, jako je vytváření datových vazeb a animace/scénářů, více použití šablon jako zdroje a styly nebo známé hodnoty Pomocí vztahů nadřazenosti a podřízenosti s jinými prvky ve stromu elementů. Kromě toho je možné implementovat vlastnosti závislosti a poskytuje samostatná ověřování, výchozí hodnoty, zpětná volání, které sledují změny jiných vlastností a systému, který může vynucení hodnoty vlastností na základě informací o potenciálně modulu runtime. Odvozené třídy můžete také změnit některé specifické vlastnosti existující vlastnosti přepsání metadat pro vlastnost závislosti, spíše než skutečná implementace vlastnosti existující a vytvářet nové vlastnosti přepsání.

V odkazu sady SDK můžete identifikovat, které je vlastnost závislosti přítomností informace o vlastnosti závislosti části na stránce pro spravované referenční materiály pro tuto vlastnost. Informace o vlastnosti závislosti část obsahuje odkaz <xref:System.Windows.DependencyProperty> identifikátor pole pro danou vlastnost závislosti a také obsahuje seznam možností metadat, které jsou nastavené pro tuto vlastnost, informací o přepsání třídy a další podrobnosti.

## <a name="dependency-properties-back-clr-properties"></a>Vlastnosti závislostí zpět vlastnosti CLR
Vlastnosti závislostí a v systému WPF vlastností rozšíření funkcí vlastnost tím, že poskytuje typ, který zálohuje vlastnosti, jako alternativní implementace pro standardní vzor vlastnost s privátní pole zálohování. Název tohoto typu je <xref:System.Windows.DependencyProperty>. Je jiný důležité typ, který definuje vlastnost systému WPF <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject> definuje základní třídu, která můžete zaregistrovat a vlastní vlastnosti závislosti.

Následuje seznam terminologii používané prostřednictvím vlastností závislosti:

- **Vlastnost závislosti:** Vlastnost, která je založená <xref:System.Windows.DependencyProperty>.

- **Identifikátor vlastnosti závislosti:** A <xref:System.Windows.DependencyProperty> instanci, která je získali jako návratovou hodnotu, při registraci vlastnost závislosti a pak uloženy jako statického člena třídy. Tento identifikátor slouží jako parametr pro celou řadu rozhraní API, která v systému WPF vlastností zasahovat.

- **CLR "zabezpečenou obálku":** Skutečný get a set pro vlastnost implementace. Tyto implementace zahrnují identifikátor vlastnosti závislosti pomocí ho <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> volání, tím zajišťuje základní pro danou vlastnost pomocí vlastnosti systému WPF.

Následující příklad definuje `IsSpinning` vlastnost závislosti a ukazuje vztah jednotlivých <xref:System.Windows.DependencyProperty> identifikátor na vlastnost, která ho.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Zásady vytváření názvů vlastnosti a její základní <xref:System.Windows.DependencyProperty> pole je důležité. Název pole je vždy název vlastnosti, s příponou `Property` připojí. Další informace o této konvence a důvody pro to, najdete v části [vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Nastavení hodnoty vlastností
Vlastnosti můžete nastavit v kódu nebo v XAML.

### <a name="setting-property-values-in-xaml"></a>Nastavení hodnot vlastností v XAML 
Následující příklad XAML Určuje barvu pozadí tlačítka červeně. Tento příklad ukazuje případ, kde jednoduché řetězcová hodnota pro atribut XAML je typ převést analyzátorem WPF XAML do WPF typu ( <xref:System.Windows.Media.Color>, prostřednictvím <xref:System.Windows.Media.SolidColorBrush>) v generovaném kódu.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML podporuje širokou škálu různými formami syntaxe pro nastavení vlastnosti. Které syntaxi pro určité vlastnosti závisí na hodnotový typ, který používá vlastnost, a také dalších faktorů, třeba přítomnost konvertor typu. Další informace o syntaxi XAML pro nastavení vlastnosti najdete v tématu [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) a [syntaxe XAML v podrobnosti o](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).

Následující příklad XAML jako příklad syntaxe bez atributu, ukazuje na pozadí jiné tlačítko. Tentokrát spíše než nastavení jednoduché plnou barvu, na pozadí je nastavena na obrázku, s elementem představující tuto image a zdroj této image zadaná jako atribut elementu vnořené. Toto je příklad syntax prvku vlastnosti.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Nastavení vlastností v kódu
 Nastavení hodnot vlastností závislosti v kódu je obvykle pouhé volání implementace sady vystavené [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "zabezpečenou obálku".

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Získání hodnoty vlastnosti je také v podstatě volání implementace "zabezpečenou obálku" get:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Můžete také volat v systému vlastností [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> přímo. To není obvykle nutné Pokud pomocí existujících vlastností (obálkami jsou pohodlnější a poskytují lepší vystavení vlastnosti pro nástroje pro vývojáře), ale volání [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] přímo je vhodné pro určité scénáře.

Vlastnosti můžete také nastavit v XAML a pak přistupuje později v kódu pomocí modelu code-behind. Podrobnosti najdete v tématu [použití modelu Code-Behind a XAML v subsystému WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Vlastnosti funkce poskytované službou vlastnost závislosti
Vlastnosti závislosti poskytuje funkce, který rozšiřuje funkce vlastnosti na rozdíl od vlastnost, která je založená na pole. Tato funkce často představuje nebo podporuje jednu následujícími specifickými funkcemi:

- [Prostředky](#resources)

- [Vytváření datových vazeb](#data-binding)

- [Styly](#styles)

- [Animace](#animations)

- [Přepsání metadat](#metadata-overrides)

- [Dědičnost hodnoty vlastnosti](#property-value-inheritance)

- [Integrace WPF Designer](#wpf-designer-integration)

### <a name="resources"></a>Prostředky
Hodnota vlastnosti závislostí lze nastavit pomocí odkazu na prostředek. Prostředky jsou obvykle určeny jako `Resources` hodnota vlastnosti kořenový element stránky nebo aplikace (Tato umístění povolit nejvíce usnadnil přístup k prostředku). Následující příklad ukazuje, jak definovat <xref:System.Windows.Media.SolidColorBrush> prostředků.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Jakmile je definován prostředek, můžete odkazovat na prostředek a použít k poskytnutí hodnoty vlastnosti:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Tento konkrétní prostředek se odkazuje jako [– rozšíření značek DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) (v WPF XAML, můžete použít odkaz statickou nebo dynamickou prostředků). Použít odkaz dynamický prostředek, bude musí být nastavení pro vlastnost závislosti, tak, aby byl speciálně dynamické referenční využití prostředků, který je povolený systém vlastnost WPF. Další informace najdete v tématu [prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).

> [!NOTE]
> Prostředky jsou považovány za místní hodnoty, což znamená, že pokud nastavíte jinou místní hodnotu, budou zmenšovat odkaz na prostředek. Další informace najdete v tématu [Priorita hodnot závislých vlastností](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

### <a name="data-binding"></a>Vytváření datových vazeb
Vlastnosti závislosti můžete vytvořit odkaz na hodnotu prostřednictvím datové vazby. Datové vazby funguje pomocí syntaxe rozšíření konkrétní značek v XAML, nebo <xref:System.Windows.Data.Binding> objekt v kódu. Pomocí datové vazby, je hodnota určení konečné vlastnost odložena až do běhu, po kterém se získá hodnota ze zdroje dat.

Následující příklad nastaví <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button>, použít vazbu deklarované v XAML. Vazba používá objekt context zděděná data a <xref:System.Windows.Data.XmlDataProvider> zdroje dat (nezobrazení). Vazba, samotný určuje vlastnost požadovaný zdroj podle <xref:System.Windows.Data.Binding.XPath%2A> v rámci datového zdroje.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Vazby jsou považovány za místní hodnoty, což znamená, že pokud nastavíte jiné místní hodnoty, bude odstranění vazby. Podrobnosti najdete v tématu [Priorita hodnot závislých vlastností](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

Vlastnosti závislosti nebo <xref:System.Windows.DependencyObject> třídy, proveďte nativně podporu <xref:System.ComponentModel.INotifyPropertyChanged> pro účely vytváření oznámení o změnách v <xref:System.Windows.DependencyObject> hodnota vlastnosti pro operace vazby dat zdroje. Další informace o tom, jak vytvořit vlastnosti pro použití při vytváření datových vazeb, které můžete nahlásit změny cíl vazby dat najdete v tématu [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).

### <a name="styles"></a>Styly
Styly a šablony jsou dvě hlavní motivačním scénářů pro použití vlastnosti závislosti. Styly jsou zvláště užitečné pro nastavení vlastnosti, které definují aplikaci [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Styly jsou obvykle definují jako prostředky v XAML. Styly interakci s vlastností systému, protože obvykle obsahují "setter" pro konkrétní vlastnosti, jakož i "triggery", které změní nastavení vlastnosti na základě hodnoty v reálném čase pro jiné vlastnosti.

Následující příklad vytvoří velmi jednoduchého stylu (by lze definovat uvnitř <xref:System.Windows.FrameworkElement.Resources%2A> slovníku. Tím se nezobrazují), pak použije tento styl přímo na <xref:System.Windows.FrameworkElement.Style%2A> vlastnost <xref:System.Windows.Controls.Button>. Metoda setter v rámci sady styl <xref:System.Windows.Controls.Control.Background%2A> vlastnost Stylizovaný <xref:System.Windows.Controls.Button> na zelenou.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Další informace najdete v tématu [styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md).

### <a name="animations"></a>Animace
Vlastnosti závislostí lze animovat. Při animaci se používá a běží, hodnotu animovaný funguje s vyšší prioritou než libovolnou hodnotu (například místní hodnoty), který má vlastnost jinak.

V následujícím příkladu animuje <xref:System.Windows.Controls.Control.Background%2A> na <xref:System.Windows.Controls.Button> vlastnost (technicky vzato <xref:System.Windows.Controls.Control.Background%2A> je animovaný pomocí syntax prvku vlastnosti k určení prázdnou hodnotu <xref:System.Windows.Media.SolidColorBrush> jako <xref:System.Windows.Controls.Control.Background%2A>, pak bude <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost, která <xref:System.Windows.Media.SolidColorBrush> je vlastnost, která je přímo animovat).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Další informace o animace vlastností najdete v tématu [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) a [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Přepsání metadat
Přepsání metadat pro vlastnosti, když odvozujete od třídy, která původně zaregistruje vlastnost závislosti, můžete změnit určitého chování, vlastnost závislosti. Přepsání metadat se může spolehnout <xref:System.Windows.DependencyProperty> identifikátor. Přepsání metadat nevyžaduje, aby vlastnost pokaždé znova implementovány. Změna metadat nativně zařizuje služba vlastnost systému; Každá třída potenciálně uchovává jednotlivé metadata pro všechny vlastnosti, které se dědí ze základní třídy, na základě-type.

Následující příklad přepisuje metadata pro vlastnost závislosti <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. Přepsání metadat vlastnosti této konkrétní závislost je součástí implementaci vzoru, který vytvoří ovládací prvky, které můžete použít výchozí styly motivů.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Další informace o přepsání nebo získání metadat vlastností najdete v tématu [Metadata vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Dědičnost hodnoty vlastnosti
Element může dědit hodnota závislosti vlastnosti z nadřazeného v rámci stromů objektů.

> [!NOTE]
> Chování dědičnosti vlastností hodnota není povolena globálně pro všechny vlastnosti závislosti, protože čas výpočtu dědičnosti má dopad na výkon. Dědičnost hodnoty vlastnosti je obvykle povolena pouze pro vlastnosti, kde konkrétní scénář naznačuje, že je vhodné dědičnost hodnoty vlastnosti. Můžete určit, zda vlastnost závislosti dědí pohledem **informace o vlastnosti závislosti** oddíl pro tuto vlastnost závislosti v odkazu sady SDK.

Následující příklad ukazuje vazbu a nastaví <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost, která určuje zdroj vazby, který se zobrazí v předchozím příkladu vazby. Všechny následné vazby v podřízené objekty není nutné jako zdroj, můžou používat zděděná hodnota z <xref:System.Windows.FrameworkElement.DataContext%2A> v nadřazeném prvku <xref:System.Windows.Controls.StackPanel> objektu. (Alternativně může místo toho zvolit přímo zadat svůj vlastní podřízený objekt <xref:System.Windows.FrameworkElement.DataContext%2A> nebo <xref:System.Windows.Data.Binding.Source%2A> v <xref:System.Windows.Data.Binding>a záměrně používat pro datový kontext vazby je zděděná hodnota.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Další informace najdete v tématu [dědičnost hodnoty vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Integrace Návrháře WPF
Vlastní ovládací prvek s vlastnostmi, které jsou implementovány jako vlastnosti závislosti budou dostávat příslušné [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] podporovat. Jedním z příkladů je schopnost upravovat vlastnosti závislosti s přímým přístupem a připojené pomocí **vlastnosti** okna. Další informace najdete v tématu [Přehled vytváření ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Priorita hodnot závislých vlastností
Když dostanete změní hodnota vlastnosti závislostí, potenciálně získávání hodnotu, která byla nastavena na dané vlastnosti prostřednictvím některého z jiných založené na vlastnosti vstupy, které jsou součástí vlastností systému WPF. Priorita hodnot závislých vlastností existuje tak, aby širokou škálu scénářů jak získat jejich hodnoty vlastnosti můžou pracovat předvídatelným způsobem.

Podívejte se na následující příklad. Příklad obsahuje styl, který se vztahuje na všechna tlačítka a jejich <xref:System.Windows.Controls.Control.Background%2A> vlastnosti, ale také určuje jedno tlačítko s místně nastavené <xref:System.Windows.Controls.Control.Background%2A> hodnotu.

> [!NOTE]
> Použití dokumentace ke službě SDK podmínky "místní hodnota" nebo "místní hodnotu" občas, když hovoříte o vlastnosti závislosti. Místně nastavené hodnotou je hodnota vlastnosti, která je nastavena přímo na instanci objektu v kódu, nebo jako atribut na prvek v XAML.  
  
V zásadě pro první tlačítko, je vlastnost nastavena, dvakrát, ale platí pouze jedna hodnota: hodnota s nejvyšší prioritou. Místně nastavené hodnoty má nejvyšší prioritu (s výjimkou průběžný animace, ale žádná animace platí v tomto příkladu) a tím nastavte místně použita hodnota místo hodnoty style setter pro pozadí na první tlačítko. Na druhé tlačítko má žádná místní hodnota (a jiná hodnota s vyšší prioritou než style setter) a tedy pochází pozadí na toto tlačítko z style setter.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Proč existuje Priorita vlastností závislostí?
Obvykle není vhodné styly vždycky používat a skrývat i místně nastavené hodnoty jednotlivých elementu (v opačném případě by bylo velmi obtížné obecně používat styly nebo elementy). Proto se hodnoty, které pocházejí z styly fungovat na nižší předchůdců než místně nastavené hodnoty. Podrobnější seznam vlastnosti závislosti a místo, odkud můžou pocházet platnou hodnotu pro vlastnost závislosti, naleznete v tématu [Priorita hodnot závislých vlastností](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

> [!NOTE]
> Existuje několik vlastností definovaných v WPF prvky, které nejsou vlastnosti závislosti. Vlastnosti byly implementovány jako vlastnosti závislosti pouze v případě, že došlo k musí zajišťovat podporu pro nejméně jednu z scénáře povolené ve vlastnosti systému: vytváření datových vazeb, styly, animace, výchozí hodnota podporu, dědičnost, přidružené vlastnosti, nebo zrušení.

## <a name="learning-more-about-dependency-properties"></a>Získání informací o vlastnosti závislosti  

- Připojená vlastnost je typu vlastnosti, která podporuje speciální syntaxe XAML. Připojená vlastnost často nemá 1:1 komunikaci [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost, a není nutně vlastnost závislosti. Typické účely připojené vlastnosti je umožňující podřízených prvků, které se hlásí hodnoty vlastností do nadřazeného elementu, i v případě, že nadřazeného elementu a podřízený prvek není mít tuto vlastnost jako součást Seznam členů třídy. Jeden primární scénářem je povolit podřízené prvky nadřazeného informovat, jak by se zobrazit v [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; příklad najdete v tématu <xref:System.Windows.Controls.DockPanel.Dock%2A> nebo <xref:System.Windows.Controls.Canvas.Left%2A>. Podrobnosti najdete v tématu [přehled připojených vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

- Vývojáři komponent nebo vývojáři aplikace chtít vytvořit své vlastní vlastnosti závislosti, aby bylo možné povolit možnosti, jako jsou datové vazby nebo styly podpory nebo neplatnost a hodnota vynucení podporovat. Podrobnosti najdete v tématu [vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).

- Vlastnosti závislosti by měla být obecně považují za veřejné vlastnosti, přístupné, nebo alespoň zjistitelné pomocí jakýkoli volající, který má přístup k instanci. Další informace najdete v tématu [zabezpečení vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-security.md).

## <a name="see-also"></a>Viz také:
- [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [Vlastnosti závislosti jen pro čtení](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)
- [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
