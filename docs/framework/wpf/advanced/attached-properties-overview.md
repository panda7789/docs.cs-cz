---
title: Přehled připojených vlastností
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: e4f2b88b075a7806d2ca4c4a1e2cf3f027e71f51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706229"
---
# <a name="attached-properties-overview"></a>Přehled připojených vlastností

Připojená vlastnost je definován pomocí XAML koncept. Připojená vlastnost je určena pro použití jako typ globální vlastností, která je nastavitelná při čekání na libovolný objekt. V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], připojené vlastnosti se obvykle definují jako specializovaná forma vlastnost závislosti, která nemá vlastnost konvenční "zabezpečenou obálku".

## Požadované součásti <a name="prerequisites"></a>

Toto téma předpokládá, že rozumíte vlastnosti závislosti z pohledu příjemce vlastnosti existujícího závislosti na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy a čtení [přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Pokud chcete postupovat podle příkladů v tomto tématu, potřebujete také pochopit XAML a vědět, jak psát aplikace WPF.

## Proč používat připojené vlastnosti <a name="attached_properties_usage"></a>

Jediný účel připojené vlastnosti je umožnit různé podřízené prvky, chcete-li určit jedinečné hodnoty pro vlastnost, která je ve skutečnosti definovány v nadřazeném elementu. Konkrétní aplikace tento scénář má informovat nadřazený element jak mají být uvedené v podřízených elementů [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Jedním z příkladů je <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> vlastnost. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Vlastnost je vytvořen jako připojené vlastnosti, protože je navržen pro nastavení u elementů, které jsou obsaženy v rámci <xref:System.Windows.Controls.DockPanel>, spíše než na <xref:System.Windows.Controls.DockPanel> samotný. <xref:System.Windows.Controls.DockPanel> Třída definuje statické <xref:System.Windows.DependencyProperty> pole s názvem <xref:System.Windows.Controls.DockPanel.DockProperty>a pak poskytuje <xref:System.Windows.Controls.DockPanel.GetDock%2A> a <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody jako veřejnou přistupující objekty pro připojené vlastnosti.

## Připojené vlastnosti v XAML <a name="attached_properties_xaml"></a>

V XAML, nastavte připojené vlastnosti pomocí syntaxe *AttachedPropertyProvider*. *Vlastnost PropertyName*

Následuje příklad, jak můžete nastavit <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> v XAML:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Všimněte si, že využití je poněkud podobně jako statická vlastnost; vždycky odkazovat typ <xref:System.Windows.Controls.DockPanel> , která vlastní a registruje připojená vlastnost, místo odkazování na jakoukoli instanci určená názvem.

Protože připojené vlastnosti v XAML je atribut, který můžete nastavit v označení, má pouze operaci set také všechny závažnosti. Nelze získat přímo vlastnost v XAML, i když jsou některé nepřímé mechanismy pro porovnání hodnot, jako jsou triggery ve stylech (podrobnosti najdete v tématu [styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)).

### <a name="attached-property-implementation-in-wpf"></a>Připojená vlastnost implementace v subsystému WPF

V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], většina připojené vlastnosti, které existují v WPF typy, které jsou spojené s prezentací uživatelského rozhraní jsou implementovány jako vlastnosti závislosti. Připojené vlastnosti jsou koncept XAML, zatímco vlastnosti závislosti koncept WPF. Vzhledem k tomu, že jsou vlastnosti WPF připojené vlastnosti závislosti, podporují vlastnost konceptů závislosti, jako jsou metadata vlastnosti a výchozí hodnoty z těchto vlastností metadat.

## Jak připojených vlastností jsou používány vlastnícího typu <a name="howused"></a>

I když jsou připojené vlastnosti nastavitelná při čekání na libovolný objekt, který nemusí znamenat automaticky, že nastavení vlastnosti vytvoří hmatatelnými výsledek nebo že hodnota se nikdy nepoužil jiným objektem. Obecně platí připojené vlastnosti jsou určeny tak, aby objekty z široké škály hierarchií tříd je to možné nebo logické vztahy můžete každou sestavu běžných informací o typ, který definuje připojená vlastnost. Typ, který definuje připojená vlastnost obvykle následuje jednu z těchto modelů:

-   Typ, který definuje připojená vlastnost je navržený tak, aby může být nadřazený element prvky, které nastaví hodnoty pro připojené vlastnosti. Typ pak iteruje jeho podřízených objektů prostřednictvím proti některé stromovou strukturu objekt interní logiku, získá hodnoty a funguje na tyto hodnoty způsobem.

-   Typ, který definuje připojená vlastnost se použije jako podřízený element pro širokou škálu možných nadřazené elementy a modely obsahu.

-   Představuje typ, který definuje vlastnost připojené služby. Další typy nastavení hodnot pro připojené vlastnosti. Potom když elementu, který se nastavit vlastnost je vyhodnocen v kontextu služby, hodnoty připojené vlastnosti jsou získávány prostřednictvím interní logiku, třídy služby.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Příklad definován nadřazený připojené vlastnosti

Nejobvyklejším scénářem, kde WPF definuje připojené vlastnosti je, pokud nadřazený element podporuje kolekci elementů podřízené a také implementuje chování kde specifika chování označené jednotlivě pro každý podřízený prvek.

<xref:System.Windows.Controls.DockPanel> definuje <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> přidružená vlastnost, a <xref:System.Windows.Controls.DockPanel> má kódu na úrovni třídy jako součást logiky jeho vykreslení (konkrétně <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> a <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). A <xref:System.Windows.Controls.DockPanel> instance bude vždy zkontrolujte, zda některý z jeho bezprostředně podřízené prvky nastavit hodnotu pro <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Pokud ano, tyto hodnoty budou vstup pro logiku vykreslování u této konkrétní podřízený element. Vnořené <xref:System.Windows.Controls.DockPanel> jednotlivých instancí zpracovávat své vlastní kolekce bezprostřední podřízený element, ale toto chování je specifický pro implementaci tím, jak <xref:System.Windows.Controls.DockPanel> procesy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> hodnoty. Je možné teoreticky připojili vlastností, které ovlivňují prvky nad rámec bezprostřední nadřazený objekt. Pokud <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> připojená vlastnost nastavená na element, který nemá žádné <xref:System.Windows.Controls.DockPanel> nadřazený element k provedení akce, žádné chyby nebo výjimky je vyvolána. To jednoduše znamená, že byla nastavena hodnota globální vlastnosti, ale nemá žádný aktuální <xref:System.Windows.Controls.DockPanel> nadřazeného objektu, který může používat informace.

## Připojené vlastnosti v kódu <a name="attached_properties_code"></a>

Připojené vlastnosti v objektu WPF nemají typické [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] metody "zabezpečenou obálku" pro snadné get/set přístup. Důvodem je, že připojená vlastnost není nutně součástí [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obor názvů pro instance, kde je vlastnost nastavena. Procesor XAML musí být však můžete nastavit tyto hodnoty, když analyzovaný XAML. Pro podporu využití efektivní připojená vlastnost, typ vlastníka připojené vlastnosti musí implementovat vyhrazené přístupové metody ve formě **Get_PropertyName_** a **Set_PropertyName_**. Tyto vyhrazené přístupové metody jsou také užitečná pro získání nebo nastavení připojené vlastnosti v kódu. Připojená vlastnost z hlediska kódu je podobný pomocné pole, který má přístupové objekty metoda místo přistupující objekty vlastnosti a že zálohovací položka může existovat na libovolný objekt a nikoli museli výslovně definované.

Následující příklad ukazuje, jak můžete nastavit připojené vlastnosti v kódu. V tomto příkladu `myCheckBox` je instance <xref:System.Windows.Controls.CheckBox> třídy.

[!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

Podobně jako XAML malá a velká, pokud `myCheckBox` Loader již byl přidán jako podřízený prvek `myDockPanel` třetí řádek kódu na čtvrtém řádku kódu by vyvolat výjimku, ale hodnota vlastnosti nemusí pracovat <xref:System.Windows.Controls.DockPanel> nadřazené. proto by Neprovádět žádnou akci. Pouze <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> hodnota nastavená na podřízený element v kombinaci s přítomnost <xref:System.Windows.Controls.DockPanel> nadřazeného elementu způsobí efektivní chování ve vygenerované aplikaci. (V takovém případě vám může nastavte přidruženou vlastnost a potom připojit ke stromu. Nebo může připojit ke stromu potom nastavte přidruženou vlastnost. Buď akce pořadí poskytuje stejný výsledek).

## Připojená vlastnost metadat <a name="attached_properties_metadata"></a>

Při registraci vlastnost, <xref:System.Windows.FrameworkPropertyMetadata> je nastaveno k určení vlastností vlastnosti, jako je například určuje, zda vlastnost ovlivňuje vykreslování, měření a tak dále. Metadata pro připojené vlastnosti se obvykle nijak neliší od na vlastnost závislosti. Pokud je v přepsání připojená vlastnost metadat, tato hodnota se změní výchozí hodnotu implicitní připojené vlastnosti na instancích přepsáním třídy zadat výchozí hodnotu. Konkrétně se výchozí hodnota bude nahlášena, pokud některé zpracování dotazů pro hodnotu vlastnosti připojené vlastnosti prostřednictvím `Get` metodu přistupujícího objektu pro tuto vlastnost zadání instance třídy, kde zadáte metadata a hodnotu pro tento připojená vlastnost byla jinak není nastavený.

Pokud chcete povolit dědičnost hodnoty vlastnosti na vlastnost, používejte připojené vlastnosti spíše než závislost nepřipojené vlastnosti. Podrobnosti najdete v tématu [dědičnost hodnoty vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

## Vlastní připojené vlastnosti <a name="custom"></a>

### Kdy vytvořit připojené vlastnosti <a name="create_attached_properties"></a>

Když je důvodem pro vlastnost nastavení mechanismus k dispozici pro jiné než definující třídy třídy můžete například vytvořit připojené vlastnosti. Nejběžnější scénář je rozložení. Příkladem existující vlastnosti rozložení jsou <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>, a <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>. Scénáře povolené zde je, že prvky, které existuje jako podřízené prvky k řízení rozložení prvky jsou schopni express požadavkům na rozložení pro jejich nadřazených prvků rozložení jednotlivě, každé nastavení hodnoty vlastnosti, které nadřazené definované jako připojené Vlastnost.

Jiné scénáře použití připojené vlastnosti je, pokud vaše třída reprezentuje službu a chcete, aby třídy bude schopná integrovat službu více transparentně.

Ještě další možností je získat podporu Návrhář WPF Visual Studio, jako například **vlastnosti** okno úpravy. Další informace najdete v tématu [Přehled vytváření ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

Jak jsme zmínili, byste měli zaregistrovat jako připojené vlastnosti Pokud budete chtít použít dědičnost hodnoty vlastnosti.

### Postup vytvoření připojené vlastnosti <a name="how_do_i_create_attached_properties"></a>

Pokud vaše třída definuje připojená vlastnost výhradně pro použití jiných typů, pak není nutné odvodit z třídy <xref:System.Windows.DependencyObject>. Ale musíte odvodit z <xref:System.Windows.DependencyObject> Pokud budete postupovat podle celkové model WPF s vaší připojená vlastnost také být vlastnost závislosti.

Připojená vlastnost definovat jako vlastnost závislosti deklarací `public static readonly` pole typu <xref:System.Windows.DependencyProperty>. Toto pole se definují pomocí návratová hodnota <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody. Název pole musí odpovídat názvu připojené vlastnosti, připojeným řetězcem `Property`, postupujte podle zavedené WPF vzor pojmenování identifikační pole a vlastnosti, které představují. Zprostředkovatel připojené vlastnosti musí poskytnout také statické **Get_PropertyName_** a **Set_PropertyName_** metody jako přístupové objekty pro připojené vlastnosti; Pokud tak neučiníte to povede vlastnost systém se nemůže použít připojené vlastnosti.

> [!NOTE]
> Pokud vynecháte připojené vlastnosti přistupující objekt get, datové vazby na vlastnost nebude fungovat v návrhové nástroje, jako je Visual Studio a Expression Blend.

#### <a name="the-get-accessor"></a>Přístupový objekt Get

Podpis pro **Get_PropertyName_** přístupový objekt musí být:

`public static object GetPropertyName(object target)`

-   `target` Objektu lze zadat jako konkrétnější typ ve vaší implementaci. Například <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> metoda typy parametrů jako <xref:System.Windows.UIElement>, protože připojená vlastnost je určena pouze nastavení na <xref:System.Windows.UIElement> instancí.

-   Návratová hodnota se dá nastavit jako konkrétnější typ ve vaší implementaci. Například <xref:System.Windows.Controls.DockPanel.GetDock%2A> metoda typů, se jako <xref:System.Windows.Controls.Dock>, protože hodnotu lze nastavit pouze na tento výčet.

#### <a name="the-set-accessor"></a>Přístupový objekt Set

Podpis pro **Set_PropertyName_** přístupový objekt musí být:

`public static void SetPropertyName(object target, object value)`

-   `target` Objektu lze zadat jako konkrétnější typ ve vaší implementaci. Například <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda typů, se jako <xref:System.Windows.UIElement>, protože připojená vlastnost je určena pouze nastavení na <xref:System.Windows.UIElement> instancí.

-   `value` Objektu lze zadat jako konkrétnější typ ve vaší implementaci. Například <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda typů, se jako <xref:System.Windows.Controls.Dock>, protože hodnotu lze nastavit pouze na tento výčet. Mějte na paměti, že hodnota pro tuto metodu je vstup pocházející z XAML zavaděč, pokud se setká s vaší připojená vlastnost využití připojené vlastnosti ve značce. Tento vstup je hodnota zadaná jako hodnota atributu XAML ve značkách. Proto musí být typ převodu, serializátor hodnoty nebo podpora rozšíření značek pro typ, který použijete, tak, aby příslušný typ lze vytvořit z hodnoty atributu (což v konečném důsledku je právě řetězec).

Následující příklad ukazuje registraci vlastnost závislosti (pomocí <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metoda), stejně jako **Get_PropertyName_** a **Set_PropertyName_** přistupující objekty. V tomto příkladu je název přidružené vlastnosti `IsBubbleSource`. Proto musí mít název přístupové objekty `GetIsBubbleSource` a `SetIsBubbleSource`.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>Atributy připojené vlastnosti

WPF definuje několik [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] , které jsou určeny k poskytnutí informací o přidružené vlastnosti reflexe procesy a Typičtí uživatelé reflexe a vlastnost informace, jako je návrháře. Vzhledem k tomu, že připojené vlastnosti typu neomezený obor, návrháři potřebovat způsob, jak abyste se vyhnuli náročný globálním seznamem všech připojených vlastností, které jsou definovány v implementaci určitou technologii, která používá XAML. [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] Této WPF definuje pro připojené vlastnosti lze použít k určení oboru v případech, kdy daný připojené vlastnosti mají být zobrazeny v okně Vlastnosti. Zvažte také použití těchto atributů pro vlastní připojené vlastnosti. Účel a syntaxi [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] je popsaný na odpovídající odkaz stránky:

-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## Další informace o přidružené vlastnosti <a name="more"></a>

-   Další informace o vytvoření připojené vlastnosti najdete v tématu [registrace připojené vlastnosti](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md).

-   Další pokročilé scénáře použití pro vlastnosti závislosti a připojených vlastností, naleznete v tématu [vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).

-   Můžete také registrovat vlastnost jako připojené vlastnosti a jako vlastnost závislosti, ale stále pak vystavit implementace "zabezpečenou obálku". V takovém případě vlastnost lze nastavit buď na tento element nebo na libovolný element prostřednictvím XAML připojené vlastnosti syntaxe. Je například vlastnost s odpovídající scénáře pro použití, standard a připojené <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.DependencyProperty>
- [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Registrace přidružené vlastnosti](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)