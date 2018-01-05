---
title: "Přehled vlastností závislostí"
description: "Vlastnost, kterou je zajištěna WPF vlastnost systému se označuje jako vlastnost závislosti. Tento přehled popisuje vlastnosti systému WPF a možností vlastnost závislosti."
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: article
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
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d90e47c400f24eb10f2d262f9cb0e757ff472f0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="dependency-properties-overview"></a>Přehled vlastností závislostí

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje sadu služeb, které slouží k rozšíření funkcí [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost. Souhrnně, tyto služby jsou obvykle označují jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému. Vlastnosti, které je založeno [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému se označuje jako vlastnost závislosti. Tento přehled popisuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému a možností vlastnost závislosti. To zahrnuje jak používat existující vlastností závislostí v jazyce XAML a v kódu. Tento přehled také zavádí specializované aspektů vlastností závislostí, jako je například metadata vlastnosti závislosti a jak vytvořit vlastní vlastnost závislosti v rámci vlastní třídy.

## <a name="prerequisites"></a>Požadavky
Toto téma předpokládá, že máte některé základní znalosti o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] a objektově orientované programování. Chcete-li v následujících příkladech v tomto tématu byste měli také porozumět [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a vědět, jak napsat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Další informace najdete v tématu [návod: Můj první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Závislost vlastnosti a vlastnosti CLR
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vlastnosti jsou obvykle zveřejněné jako [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnosti. Na základní úrovni může komunikovat přímo s těmito vlastnostmi a nikdy vědět, že jsou implementované jako vlastnost závislosti. Ale měli byste se seznámit s některé nebo všechny funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti systému, tak, aby můžete využít výhod těchto funkcí.

Účelem vlastností závislostí je poskytnout způsob, jak výpočtu hodnoty vlastnosti, na základě hodnoty ostatní vstupy. Tyto další vstupy mohou zahrnovat vlastnosti systému, například motivy a uživatelské předvolby, vlastnost za běhu rozhodnutí mechanismy, například datové vazby a animací nebo scénářů, více použití šablony, například prostředky a styly nebo známé hodnoty prostřednictvím vztahů nadřazenosti a podřízenosti s jinými prvky ve stromové struktuře elementu. Kromě toho lze vlastnost závislosti implementovat k zajištění nezávislý ověřování, výchozí hodnoty, zpětná volání, které sledují změny dalších vlastností a systém, který může coerce hodnot vlastností na základě informací o potenciálně modulu runtime. Odvozené třídy můžete také změnit některé specifické vlastnosti existující vlastnost přepsání metadat vlastností závislostí, nikoli skutečné použití existující vlastnosti nebo vytvořit nové vlastnosti přepsání.

Odkaz na sady SDK můžete identifikovat vlastností, které je vlastnost závislosti přítomností části informace o vlastnosti závislosti na stránce spravovaný odkaz pro danou vlastnost. Informace o vlastnosti závislosti část obsahuje odkaz <xref:System.Windows.DependencyProperty> identifikátor pole pro tuto vlastnost závislosti a také obsahuje seznam možností metadat, které jsou nastavené pro tuto vlastnost, informace o přepsání na třídě a další podrobnosti.

## <a name="dependency-properties-back-clr-properties"></a>Vlastnosti závislosti zpět vlastnosti CLR
Vlastnosti závislosti a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému rozšířit funkce vlastnost o typ, který zálohuje vlastnosti, jako alternativní implementace pro standardní vzor zálohování vlastnost s soukromé pole. Název tohoto typu je <xref:System.Windows.DependencyProperty>. Další důležité typ, který definuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systém <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject>definuje základní třídu, která můžete zaregistrovat a vlastní vlastnost závislosti.

Následuje souhrn terminologii používané v tomto [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] dokumentace když hovoříte o vlastnosti závislosti:

- **Vlastnosti závislosti:** vlastnosti, které je založeno <xref:System.Windows.DependencyProperty>.

- **Identifikátor vlastnosti závislosti:** A <xref:System.Windows.DependencyProperty> instance, kterou je jako návratová hodnota získali při registraci vlastnost závislosti a pak uloženy jako statický člen třídy. Tento identifikátor se používá jako parametr pro řadu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] které komunikují s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému.

- **CLR "obálky":** skutečnou získání a nastavení implementace pro vlastnost. Tyto implementace začlenit pomocí jeho identifikátoru vlastnosti závislosti <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> volání, a zajišťuje tak základní vlastnost s využitím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému.

V následujícím příkladu je definován `IsSpinning` vlastnost závislosti a ukazuje vztah <xref:System.Windows.DependencyProperty> identifikátor pro vlastnost, která se zálohuje.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Zásady vytváření názvů vlastnosti a jeho základní <xref:System.Windows.DependencyProperty> pole je důležité. Název pole, je vždy název vlastnosti, s příponou `Property` připojí. Další informace o touto konvencí a jeho důvodech najdete v tématu [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Nastavení hodnot vlastností
V kódu nebo v jazyce XAML, můžete nastavit vlastnosti.

### <a name="setting-property-values-in-xaml"></a>Nastavení hodnot vlastností v jazyce XAML 
Následující příklad XAML Určuje barvu pozadí tlačítka s jako červený. Tento příklad ukazuje případě jednoduché řetězcovou hodnotu pro atribut XAML je převést analyzátorem WPF XAML do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typu ( <xref:System.Windows.Media.Color>, prostřednictvím <xref:System.Windows.Media.SolidColorBrush>) v generovaného kódu.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML podporuje různé formy syntaxe pro nastavení vlastností. Které syntaxi pro konkrétní vlastnost, bude záviset na typ hodnoty, která vlastnost používá, a také dalších faktorech, jako je například přítomnost převaděče typů. Další informace o syntaxi jazyka XAML pro nastavení vlastnosti najdete v tématu [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) a [XAML syntaxe v podrobností](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).

Jako příklad syntaxe jiný atribut následující příklad XAML ukazuje další tlačítko pozadí. Tentokrát spíše než nastavení jednoduché plnou barvou, pozadí nastavena na bitovou kopii, s elementem představující této bitové kopie a zdroj této bitové kopie, zadaný jako atribut vnořený elementu. Toto je příklad syntaxe element vlastnosti.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Nastavení vlastností v kódu
 Nastavení hodnot vlastností závislostí v kódu je obvykle právě volání pro implementaci sady vystavené [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "obálku".

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Získání hodnoty vlastnosti je také v podstatě volání get "obálky" implementace:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Můžete také zavolat vlastnost systému [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> přímo. Je to obvykle nutné Pokud pomocí stávajících vlastností (obálky jsou pohodlnější a poskytují lepší ohrožení vlastnosti pro nástroje pro vývojáře), ale volání [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] přímo je vhodné pro určité scénáře.

Vlastnosti můžete také nastavit v jazyce XAML a potom získat přístup k později v kódu pomocí kódu. Podrobnosti najdete v tématu [kódu a XAML v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Vlastnost funkce poskytované službou vlastnost závislosti
Vlastnost závislosti poskytuje funkce, které rozšiřuje funkce vlastnosti a vlastnosti, který je zálohovaný díky pole. Často představuje každé takové funkce, nebo podporuje konkrétní funkce celkovým [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sadu funkcí:

- [Prostředky](#resources)

- [Datová vazba](#data-binding)

- [Styly](#styles)

- [Animace](#animations)

- [Metadata přepsání](#metadata-overrides)

- [Hodnota dědičnost vlastnosti](#property-value-inheritance)

- [Návrhář WPF integrace](#wpf-designer-integration)

### <a name="resources"></a>Prostředky
Pod položkou prostředek lze nastavit hodnotu vlastnosti závislosti. Prostředky se obvykle zadává jako `Resources` hodnotu vlastnosti kořenový element stránky nebo aplikace (Tato umístění povolit nejpohodlnější přístup k prostředku). Následující příklad ukazuje, jak definovat <xref:System.Windows.Media.SolidColorBrush> prostředků.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Jakmile je definován prostředek, můžete odkazovat na prostředek a použít k zajištění hodnotu vlastnosti:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Tento konkrétní prostředek je odkazováno jako [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) (v jazyce XAML WPF, můžete použít buď odkaz na statickou nebo dynamickou prostředků). Použít odkaz na dynamické prostředků, můžete musí být nastavení na vlastnost závislosti, takže je konkrétně odkaz využití dynamické prostředků, povolená ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému. Další informace najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).

> [!NOTE]
> Prostředky jsou považovány za místní hodnota, což znamená, že pokud jste nastavili jinou místní hodnotu, bude eliminovat odkaz na prostředek. Další informace najdete v tématu [přednost hodnota vlastnosti závislosti](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

### <a name="data-binding"></a>Datová vazba
Vlastnost závislosti můžete odkazovat hodnotu prostřednictvím datové vazby. Datové vazby funguje na syntaxi rozšíření konkrétní značek v jazyce XAML, nebo <xref:System.Windows.Data.Binding> objektu v kódu. S datovou vazbu, je do doby běhu, po kterém se hodnota získá ze zdroje dat odložení rozhodnutí hodnota konečné vlastnosti.

Následující příklad nastavuje <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button>, použití vazby deklarované v jazyce XAML. Vazba používá kontextu zděděné dat a <xref:System.Windows.Data.XmlDataProvider> zdroje dat (není vidět). Vazba, samotné určuje vlastnost požadovaný zdroj podle <xref:System.Windows.Data.Binding.XPath%2A> ve zdroji dat.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Vazby jsou považovány za místní hodnota, což znamená, že pokud jste nastavili jinou místní hodnotu, bude eliminovat vazby. Podrobnosti najdete v tématu [přednost hodnota vlastnosti závislosti](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

Vlastnosti závislosti nebo <xref:System.Windows.DependencyObject> třídy, proveďte nativně podporu <xref:System.ComponentModel.INotifyPropertyChanged> pro účely vytváření oznámení o změnách v <xref:System.Windows.DependencyObject> zdroje hodnota vlastnosti pro datové vazby operace. Další informace o tom, jak vytvořit vlastnosti pro použití v vazbu dat, která může hlásit změny na cíl, vazby dat najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).

### <a name="styles"></a>Styly
Styly a šablony jsou dvě ředitel motivačních scénářů pro použití vlastností závislostí. Styly jsou obzvláště užitečná pro nastavení vlastnosti, které definují aplikaci [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Styly jsou obvykle definovány jako prostředky v jazyce XAML. Styly komunikovat s systému vlastnost, protože obvykle obsahují "nastavení" pro konkrétní vlastnosti, stejně jako "aktivace", které změní hodnotu vlastnosti na základě hodnoty v reálném čase pro jinou vlastnost.

Následující příklad vytvoří velmi jednoduché styl (což by definované uvnitř <xref:System.Windows.FrameworkElement.Resources%2A> slovník, to není znázorněné), pak použijete tento styl přímo na <xref:System.Windows.FrameworkElement.Style%2A> vlastnost pro <xref:System.Windows.Controls.Button>. Metoda setter v rámci sady styl <xref:System.Windows.Controls.Control.Background%2A> vlastnost stylem <xref:System.Windows.Controls.Button> na zelenou.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Další informace najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).

### <a name="animations"></a>Animace
Můžete animované vlastností závislostí. Když animace se použije a běží, animovaný hodnota funguje s vyšší prioritou než hodnota (například místní hodnota), který má vlastnost jinak.

Animuje v následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> na <xref:System.Windows.Controls.Button> vlastnost (technicky <xref:System.Windows.Controls.Control.Background%2A> je animovaný pomocí syntaxe element vlastnost Pokud chcete zadat prázdný <xref:System.Windows.Media.SolidColorBrush> jako <xref:System.Windows.Controls.Control.Background%2A>, pak se <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost této <xref:System.Windows.Media.SolidColorBrush> je vlastnost, která je přímo animovaný).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Další informace o animace vlastnosti najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) a [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Metadata přepsání
Přepsáním metadata pro tuto vlastnost při odvozování od třídy, která původně zaregistruje vlastnost závislosti, můžete změnit určitého chování vlastnosti závislosti. Přepsání metadata spoléhá na <xref:System.Windows.DependencyProperty> identifikátor. Přepsání metadata nevyžaduje znovu implementace vlastnost. Změnu metadat je nativně zpracovávaných vlastnost systému; Každá třída obsahuje potenciálně jednotlivých metadata pro všechny vlastnosti, které se dědí z třídy base na základě-type.

Následující příklad přepíše metadata pro vlastnost závislosti <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. Přepsání tato metadata vlastnosti konkrétní závislost je součástí implementaci vzor, který vytvoří ovládacích prvků, které můžete použít výchozí styly z motivů.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Další informace o přepsání nebo získání metadat vlastností najdete v tématu [metadat vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Hodnota dědičnost vlastnosti
Element lze dědit, hodnota vlastnosti závislosti z nadřazené ve stromu objektů.

> [!NOTE]
> Chování dědičnosti hodnota vlastnosti není povoleno globálně pro všechny vlastnosti závislosti, protože výpočet dobu dědičnosti nemá vliv na výkon. Dědičnost hodnota vlastnosti je obvykle aktivní jenom pro vlastnosti, kde konkrétní scénář naznačuje, že dědičnost hodnota vlastnosti je vhodné. Můžete určit, zda vlastnost závislosti dědí prohlížením **informace o vlastnosti závislosti** oddíl pro tuto vlastnost závislostí v referenci sady SDK.

Následující příklad ukazuje, vazbu a nastaví <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost, která určuje zdroj vazby, která nebyla vidět předchozího příkladu vazby. Všechny následné vazeb v podřízené objekty není nutné určit zdroj, můžou používat je zděděná hodnota z <xref:System.Windows.FrameworkElement.DataContext%2A> v nadřízeném <xref:System.Windows.Controls.StackPanel> objektu. (Alternativně podřízený objekt může zvolit přímo zadat vlastní <xref:System.Windows.FrameworkElement.DataContext%2A> nebo <xref:System.Windows.Data.Binding.Source%2A> v <xref:System.Windows.Data.Binding>a pro data kontextu vazby jejího úmyslně nechcete použít je zděděná hodnota.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Další informace najdete v tématu [dědičnost hodnotu vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Integrace Návrháře WPF
Vlastní ovládací prvek s vlastnostmi, které jsou implementovány jako obdrží odpovídající vlastnosti závislosti [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] podporovat. Jedním z příkladů je možnost upravovat vlastnosti direct a připojené závislostí s **vlastnosti** okno. Další informace najdete v tématu [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Priorita hodnotu vlastnosti závislosti
Když získáte hodnota vlastnosti závislosti, jsou potenciálně získat hodnotu, která byla nastavena pro tuto vlastnost prostřednictvím některého z jiné vlastnosti na základě vstupních hodnot, které účastnit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému. Priorita hodnotu vlastnosti závislosti existuje tak, aby celou řadu scénářů jak získat vlastnosti jejich hodnoty můžete spolupracovat předvídatelnou způsobem.

Podívejte se na následující příklad. Příklad obsahuje styl, který se vztahuje na všechny tlačítka a jejich <xref:System.Windows.Controls.Control.Background%2A> vlastnosti, ale také určuje jeden tlačítko s místně nastavte <xref:System.Windows.Controls.Control.Background%2A> hodnotu.

> [!NOTE]
> Používá dokumentaci SDK podmínky "místní hodnota" nebo "místní nastavit hodnotu" občas, když hovoříte o vlastnosti závislosti. Místně nastavte hodnota je hodnotu vlastnosti, které jsou nastavené přímo v instanci objektu v kódu, nebo jako atribut na element v jazyce XAML.  
  
V zásadě pro první tlačítko, je vlastnost nastavena dvakrát, ale platí pouze jednu hodnotu: hodnota s nejvyšší prioritou. Místně nastavte hodnotu má nejvyšší prioritu (s výjimkou spuštěný animace, ale žádná animace platí v tomto příkladu) a proto nastavené místně hodnota se používá namísto hodnoty setter styl pozadí na první tlačítko. Na druhé tlačítko má žádná místní hodnota (a žádná hodnota s vyšší prioritou než setter styl) a proto pozadí na toto tlačítko pochází z nastavení chybového stylu.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Proč existuje závislost vlastnost přednost?
Obvykle nechtěli mít styly a vždy použít a skrývat i místně nastavte hodnoty jednotlivých elementu (jinak, by bylo velmi obtížné obecně pomocí stylů nebo elementy). Proto hodnoty, které pocházejí z styly fungovat na nižší předchůdců než místně nastavte hodnotu. Podrobnější seznam vlastností závislostí a kde platnou hodnotu pro vlastnost závislosti mohou pocházet z naleznete v [přednost hodnota vlastnosti závislosti](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

> [!NOTE]
> Existuje několik vlastnosti definované na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky, které nejsou vlastností závislostí. Celkového vlastnosti byly implementovány jako vlastnosti závislosti pouze v případě, že bylo musí zajišťovat podporu pro minimálně v jednom ze scénářů povoleno systémem vlastnost: datové vazby, stylů, animace, výchozí hodnota podpora, dědičnosti, přidružené vlastnosti, nebo zneplatnění.

## <a name="learning-more-about-dependency-properties"></a>Dozvědět další informace o vlastnosti závislosti  

- – Přidružená vlastnost je typ vlastnosti, která podporuje specializované syntaxe v jazyce XAML. – Přidružená vlastnost často nemá 1:1 korespondence s [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost, a není nutně vlastnost závislosti. Typické účel přidružená vlastnost je umožnit podřízené elementy: hodnoty vlastností sestavy pro nadřazený element, i v případě, že nadřazeného elementu a podřízený element není mít tuto vlastnost jako součást výpisech členové třídy. Jeden primární scénář je umožnit podřízené elementy nadřazeného informovat, jak by měla zobrazit v [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; příklad najdete v tématu <xref:System.Windows.Controls.DockPanel.Dock%2A> nebo <xref:System.Windows.Controls.Canvas.Left%2A>. Podrobnosti najdete v tématu [připojen přehled vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

- Vývojáři komponent nebo vývojáři aplikace chtít vytvořit své vlastní vlastnost závislosti, aby bylo možné povolit funkcí, jako je datová vazba nebo styly podporu nebo neplatnost a hodnota převod podporovat. Podrobnosti najdete v tématu [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).

- Vlastnosti závislosti obecně považovat jako veřejné vlastnosti přístupné nebo alespoň zjistitelný všechny volající, který má přístup k instanci. Další informace najdete v tématu [zabezpečení vlastnost závislosti](../../../../docs/framework/wpf/advanced/dependency-property-security.md).

## <a name="see-also"></a>Viz také
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Vlastnosti závislosti jen pro čtení](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
