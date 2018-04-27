---
title: Přehled připojených vlastností
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ceba94d80ca66ab228804ffff2a5b8f89a68d7c4
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="attached-properties-overview"></a>Přehled připojených vlastností
– Přidružená vlastnost je koncept definované XAML. – Přidružená vlastnost je určena pro použití jako typ globální vlastnost, která je nastavit na libovolný objekt. V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], připojené vlastnosti jsou obvykle definovány jako specializovaná forma vlastnost závislosti, který nemá vlastnost konvenční "obálku".  
  
   
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastností závislostí z perspektivy příjemce existující vlastností závislostí na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy a mít ke čtení [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Postup popsaný v příkladech v tomto tématu, by také pochopit XAML a vědět, jak napsat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
<a name="attached_properties_usage"></a>   
## <a name="why-use-attached-properties"></a>Proč používat přidružené vlastnosti  
 Jediný účel přidružená vlastnost je umožnit jiné podřízené elementy pro zadejte jedinečné hodnoty pro vlastnost, která je ve skutečnosti definována v nadřazeném elementu. Podřízené elementy informovat o tom, jak jsou uvedené v nadřazený element s určitou aplikací tohoto scénáře [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Jedním z příkladů je <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> vlastnost. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Vlastnost je vytvořen jako přidružená vlastnost, protože je určen k nastavit u elementů, které jsou obsaženy v rámci <xref:System.Windows.Controls.DockPanel>, spíš než na <xref:System.Windows.Controls.DockPanel> sám sebe. <xref:System.Windows.Controls.DockPanel> Třída definuje statických <xref:System.Windows.DependencyProperty> pole s názvem <xref:System.Windows.Controls.DockPanel.DockProperty>a pak poskytuje <xref:System.Windows.Controls.DockPanel.GetDock%2A> a <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody jako veřejné přístupových objektů pro připojená vlastnost.  
  
<a name="attached_properties_xaml"></a>   
## <a name="attached-properties-in-xaml"></a>Přidružené vlastnosti v jazyce XAML  
 V jazyce XAML, nastavte přidružené vlastnosti pomocí syntaxe *AttachedPropertyProvider*. *PropertyName*  
  
 Tady je příklad, jak můžete nastavit <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> v jazyce XAML:  
  
 [!code-xaml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]  
  
 Upozorňujeme, že využití je trochu podobné pomocí statické vlastnosti; Vždy odkazujte typ <xref:System.Windows.Controls.DockPanel> , vlastní a registruje přidružená vlastnost místo odkazující na jakoukoli instanci zadané podle názvu.  
  
 Navíc, protože přidružená vlastnost v jazyce XAML je atribut, který nastavíte v značek, má pouze operace nastavení jakékoli relevance. Nelze získat přímo vlastnosti v jazyce XAML, i když jsou některé nepřímých mechanismy pro porovnání hodnot, jako jsou aktivační události ve stylech (podrobnosti najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md)).  
  
### <a name="attached-property-implementation-in-wpf"></a>– Přidružená vlastnost implementace v grafickém subsystému WPF  
 V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], většina přidružené vlastnosti, které existují v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy, které jsou spojené s prezentací uživatelského rozhraní jsou implementované jako vlastnosti závislosti. Přidružené vlastnosti jsou koncept XAML, že jsou vlastnosti závislosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koncept. Protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přidružené vlastnosti jsou vlastnosti závislosti, podporují koncepty vlastnost závislosti například metadata vlastnosti a výchozí hodnoty z této vlastnosti metadat.  
  
<a name="howused"></a>   
## <a name="how-attached-properties-are-used-by-the-owning-type"></a>Jak typ vlastnící používají přidružené vlastnosti  
 I když jsou přidružené vlastnosti nastavit na libovolný objekt, který nemá význam automaticky, nastavení vlastnosti způsobí konkrétní výsledek, nebo že hodnota se někdy použije jiný objekt. Obecně platí přidružené vlastnosti jsou určeny tak, aby objekty pocházejících z široké škály hierarchie možné třídy nebo logické vztahy můžete každý sestavy běžných informací o typu, který definuje připojená vlastnost. Typ, který definuje připojená vlastnost obvykle zahrnuje jednu z těchto modelů:  
  
-   Typ, který definuje připojená vlastnost je navržené tak, aby byl nadřazený element prvků, které se nastavit hodnoty pro vlastnost připojené. Typ pak opakuje jeho podřízených objektů prostřednictvím interní logická proti některé objekt stromová struktura, získá hodnoty a funguje na tyto hodnoty nějakým způsobem.  
  
-   Typ, který definuje připojená vlastnost se použije jako podřízený element pro celou řadu možných nadřazené elementy a obsahu modelů.  
  
-   Typ, který definuje připojená vlastnost představuje službu. Jiné typy nastavte hodnoty pro vlastnost připojené. Potom vyhodnocena elementu, který nastaví vlastnost v kontextu služby přidružená vlastnost hodnoty jsou získávány prostřednictvím interní logická třídy služeb.  
  
### <a name="an-example-of-a-parent-defined-attached-property"></a>Příkladem definované nadřazené přidružená vlastnost  
 Nejobvyklejším scénářem kde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definuje připojené vlastnost je pokud nadřazený element podporuje podřízené elementu kolekce a také implementuje chování kde jsou specifikace chování hlášené samostatně pro každou podřízený element.  
  
 <xref:System.Windows.Controls.DockPanel> definuje <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> přidružená vlastnost, a <xref:System.Windows.Controls.DockPanel> má kód úrovni třídy jako součást svou logikou vykreslování (konkrétně <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> a <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). A <xref:System.Windows.Controls.DockPanel> instance bude vždy zkontrolujte, zda všechny jeho okamžitou podřízených elementů nastavit hodnotu <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Pokud ano, tyto hodnoty se vstup pro logiku vykreslování u této konkrétní podřízený element. Vnořené <xref:System.Windows.Controls.DockPanel> instancí každé považovat vlastní okamžitou podřízené elementu kolekce, ale toto chování je specifický pro implementaci způsobem <xref:System.Windows.Controls.DockPanel> procesy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> hodnoty. Je možné teoreticky připojenými vlastnosti, které ovlivňují elementy mimo okamžitou nadřazené. Pokud <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je připojená vlastnost nastavená na element, který neobsahuje žádné <xref:System.Windows.Controls.DockPanel> se vyvolá nadřazeného elementu k provedení akce ho, žádné chyby nebo výjimky. To znamená stačí, aby byl nastaven hodnotu globální vlastnosti, ale nemá žádný aktuální <xref:System.Windows.Controls.DockPanel> nadřazeného objektu, který může využívat informace.  
  
<a name="attached_properties_code"></a>   
## <a name="attached-properties-in-code"></a>Přidružené vlastnosti v kódu  
 Přidružené vlastnosti v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nemají typické [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "obálky" metody get/set-snadný přístup. Důvodem je, že není přidružená vlastnost nutně součástí [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obor názvů pro instance, kde je vlastnost nastavena. Procesor XAML však musí být schopný a nastavte tyto hodnoty, když je analyzovat XAML. Pro podporu efektivní přidružená vlastnost využití, typ vlastníka připojená vlastnost musí implementovat vyhrazené přístupových metod vlastností ve formě `Get` *PropertyName* a `Set` *PropertyName*. Tyto vyhrazené přístupových metod jsou také užitečná pro získání nebo nastavení přidružená vlastnost v kódu. Z hlediska kód je přidružená vlastnost podobné poli zálohování, který má metoda přístupové objekty místo vlastnost přístupové objekty a že zálohování pole může existovat v libovolného objektu místo museli být konkrétně definován.  
  
 Následující příklad ukazuje, jak můžete nastavit přidružená vlastnost v kódu. V tomto příkladu `myCheckBox` je instance <xref:System.Windows.Controls.CheckBox> třídy.  
  
 [!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
 [!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]  
  
 Podobá se XAML případ `myCheckBox` kdyby již byla přidána jako podřízený element `myDockPanel` podle ve třetím řádku kódu by čtvrtý řádek kódu vyvolat výjimku, ale hodnota vlastnosti nebude pracovat s <xref:System.Windows.Controls.DockPanel> nadřazené proto se nic nestane. Pouze <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> hodnota nastavená pro podřízený element v kombinaci s přítomnost <xref:System.Windows.Controls.DockPanel> nadřazeného elementu způsobí, že efektivní chování v vykreslené aplikaci. (V takovém případě je může nastavit připojená vlastnost a potom přiřadit stromu. Nebo může připojit k stromu potom nastavte připojená vlastnost. Buď akce pořadí poskytuje stejného výsledku).  
  
<a name="attached_properties_metadata"></a>   
## <a name="attached-property-metadata"></a>Metadata přidružená vlastnost  
 Při registraci vlastnosti <xref:System.Windows.FrameworkPropertyMetadata> je nastaven na zadejte charakteristiky vlastnosti, například zda vlastnost ovlivňuje vykreslování, měření a tak dále. Metadata pro přidružená vlastnost je obecně nejsou jiné než u vlastnosti závislosti. Pokud zadáte výchozí hodnotu v přepsání pro metadata přidružená vlastnost, tato hodnota se změní výchozí hodnota implicitní přidružená vlastnost na instancí třídy přepsání. Konkrétně je výchozí hodnota uvádět v případě, že některé zpracování dotazů pro hodnotu přidružená vlastnost prostřednictvím `Get` metoda přistupujícího objektu pro tuto vlastnost určení instance třídy, kde zadáte metadata a hodnota pro tento – přidružená vlastnost byla jinak není nastavena.  
  
 Pokud chcete povolit dědičnost hodnotu vlastnosti na vlastnost, používejte připojené vlastnosti nikoli vlastnosti nepřipojené závislostí. Podrobnosti najdete v tématu [dědičnost hodnotu vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
<a name="custom"></a>   
## <a name="custom-attached-properties"></a>Přidružené vlastní vlastnosti  
  
<a name="create_attached_properties"></a>   
### <a name="when-to-create-an-attached-property"></a>Kdy vytvořit přidružená vlastnost  
 Můžete vytvořit přidružená vlastnost po důvod pomocí vlastnosti nastavení mechanismus k dispozici pro třídy jiného než definující třídu. Nejběžnější scénáře je rozložení. Příklady existující rozložení vlastnosti <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>, a <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>. Scénář povolené v tomto poli je, že prvky, které existují jako podřízené elementy pro rozložení řízení elementy dokážou jednotlivě express rozložení požadavky na jejich rozložení nadřazené elementy, každý nastavení hodnotu vlastnosti, nadřazený definovaný jako připojené Vlastnost.  
  
 Jiné scénáře použití přidružená vlastnost je, když vaše třída reprezentuje služby a chcete, aby třídy moct integrovat službu více transparentně.  
  
 Ještě další možností je přijímat [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] podporují, jako například **vlastnosti** okno úpravy. Další informace najdete v tématu [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Jak je uvedeno nahoře, byste měli zaregistrovat jako přidružená vlastnost Pokud chcete použít dědičnost hodnotu vlastnosti.  
  
<a name="how_do_i_create_attached_properties"></a>   
### <a name="how-to-create-an-attached-property"></a>Postup vytvoření přidružená vlastnost  
 Pokud vaše třída je definování přidružená vlastnost výhradně pro použití na jiné typy, pak nebude muset odvozena od třídy <xref:System.Windows.DependencyObject>. Ale nutné odvozovat od <xref:System.Windows.DependencyObject> Pokud budete postupovat podle celkovým [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] model toho, že přidružená vlastnost také být vlastnost závislosti.  
  
 Definujte přidružená vlastnost jako vlastnost závislosti deklarace `public` `static` `readonly` pole typu <xref:System.Windows.DependencyProperty>. V tomto poli se definují pomocí vrácenou hodnotu <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metoda. Název pole musí odpovídat názvu přidružená vlastnost, spolu s řetězec `Property`, dodržujte navázáno [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vzor pojmenovávání identifikace polí a vlastností, které představují. Zprostředkovatel přidružená vlastnost taky nutné zadat statické `Get` *PropertyName* a `Set` *PropertyName* metody jako přístupových objektů pro připojená vlastnost; neúspěšného se budou Výsledkem vlastnost systému se nepodařilo použít přidružená vlastnost.  
  
> [!NOTE]
>  Pokud vynecháte přistupující objekt get přidružená vlastnost, nebude fungovat datové vazby na vlastnost v nástrojích pro návrh, jako je například Visual Studio a Expression Blend.  
  
#### <a name="the-get-accessor"></a>Přistupující objekt Get  
 Podpis pro `Get` *PropertyName* přistupujícího objektu musí být:  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   `target` Objekt lze zadat jako typu konkrétnější v implementaci. Například <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> metoda typy parametr jako <xref:System.Windows.UIElement>, protože přidružená vlastnost je určena pouze nastavení na <xref:System.Windows.UIElement> instance.  
  
-   Návratovou hodnotu lze zadat jako typu konkrétnější v implementaci. Například <xref:System.Windows.Controls.DockPanel.GetDock%2A> metoda typy jej jako <xref:System.Windows.Controls.Dock>, protože hodnota můžete nastavit pouze na tento výčet.  
  
#### <a name="the-set-accessor"></a>Přistupující objekt Set  
 Podpis pro `Set` *PropertyName* přistupujícího objektu musí být:  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   `target` Objekt lze zadat jako typu konkrétnější v implementaci. Například <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda typy jej jako <xref:System.Windows.UIElement>, protože přidružená vlastnost je určena pouze nastavení na <xref:System.Windows.UIElement> instance.  
  
-   `value` Objekt lze zadat jako typu konkrétnější v implementaci. Například <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda typy jej jako <xref:System.Windows.Controls.Dock>, protože hodnota můžete nastavit pouze na tento výčet. Mějte na paměti, že hodnota pro tuto metodu je vstupní pocházejících z XAML zavaděč, pokud se setká s vaší přidružená vlastnost přidružená vlastnost využití v kódu. Tento vstup je hodnota zadaná jako hodnota atributu XAML v kódu. Proto musí existovat převod typů, hodnota serializátor nebo podporu rozšíření značek pro typ, který použijete, tak, aby příslušného typu lze vytvořit z hodnoty atributů (což je nakonec právě řetězec).  
  
 Následující příklad ukazuje vlastnost registrace závislosti (pomocí <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metoda), a taky `Get` *PropertyName* a `Set` *PropertyName* přístupové objekty . V příkladu je název přidružená vlastnost `IsBubbleSource`. Proto musí mít název přístupové objekty `GetIsBubbleSource` a `SetIsBubbleSource`.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
#### <a name="attached-property-attributes"></a>Atributy přidružená vlastnost  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definuje několik [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] který slouží k zadání informací o přidružené vlastnosti pro procesy reflexe a uživatelům typické reflexe a vlastnost informací, například Designer. Vzhledem k tomu, že přidružené vlastnosti typu neomezený obor, Designer potřebovat způsob, jak čtenáře uživatelé s globální seznam přidružené vlastnosti, které jsou definovány v konkrétní technologie implementace, která používá XAML. [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] , [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Definuje pro přidružené vlastnosti můžete použít k určení rozsahu situacích, kde se mají danou přidružená vlastnost v okně vlastností. Můžete uvažovat o použití těchto atributů pro vlastních připojené vlastností také. Účel a syntaxi [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] je popsaný na odpovídající odkaz na stránkách:  
  
-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>  
  
<a name="more"></a>   
## <a name="learning-more-about-attached-properties"></a>Více informací o přidružené vlastnosti  
  
-   Další informace o vytváření přidružená vlastnost najdete v tématu [zaregistrovat ve vlastnosti připojené](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md).  
  
-   Další pokročilé scénáře použití pro vlastnosti závislosti a přidružené vlastnosti, najdete v části [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
-   Můžete také registrovat vlastnost jako přidružená vlastnost a jako vlastnost závislosti, ale stále následně je zpřístupněte implementace "obálku". V takovém případě vlastnost lze nastavit buď na daný element nebo u libovolného elementu prostřednictvím XAML připojené vlastnost syntaxe. Je například vlastnost s scénářem vhodné pro použití, standard a připojené <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.DependencyProperty>  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Registrace přidružené vlastnosti](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)
