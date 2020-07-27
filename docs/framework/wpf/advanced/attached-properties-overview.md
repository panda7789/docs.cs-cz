---
title: Přehled připojených vlastností
description: Seznamte se s připojenými vlastnostmi v Windows Presentation Foundation, což jsou globální vlastnosti nastavitelované na libovolný objekt.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 993f65024fcfc4f39a408c81af43b798360e6cf6
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168387"
---
# <a name="attached-properties-overview"></a>Přehled připojených vlastností

Připojená vlastnost je koncept definovaný v jazyce XAML. Připojená vlastnost je určena pro použití jako typ globální vlastnosti, která je nastavena pro libovolný objekt. V jsou [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] přidružené vlastnosti obvykle definovány jako specializované formy vlastnosti závislosti, která nemá vlastnost "Obálka".

## <a name="prerequisites"></a>Požadovaný<a name="prerequisites"></a>

V tomto článku se předpokládá, že rozumíte vlastnostem závislosti z perspektivy uživatele existujících vlastností závislosti u [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] tříd a přečetli jste [Přehled vlastností závislosti](dependency-properties-overview.md). Chcete-li postupovat podle příkladů v tomto článku, měli byste také pochopit XAML a vědět, jak psát aplikace WPF.

## <a name="why-use-attached-properties"></a>Proč použít připojené vlastnosti<a name="attached_properties_usage"></a>

Jedním z účel připojených vlastností je povolení různých podřízených prvků pro zadání jedinečných hodnot pro vlastnost, která je definována v nadřazeném elementu. Konkrétní aplikace tohoto scénáře mají podřízené prvky, které informují nadřazený prvek, jak mají být prezentovány v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . Jedním z příkladů je <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> vlastnost. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>Vlastnost je vytvořena jako připojená vlastnost, protože je určena k nastavení u elementů, které jsou obsaženy v rámci a <xref:System.Windows.Controls.DockPanel> nikoli <xref:System.Windows.Controls.DockPanel> samotné. <xref:System.Windows.Controls.DockPanel>Třída definuje statické <xref:System.Windows.DependencyProperty> pole s názvem <xref:System.Windows.Controls.DockPanel.DockProperty> a pak poskytuje <xref:System.Windows.Controls.DockPanel.GetDock%2A> <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody a jako veřejné přístupové objekty pro připojenou vlastnost.

## <a name="attached-properties-in-xaml"></a>Připojené vlastnosti v jazyce XAML<a name="attached_properties_xaml"></a>

V jazyce XAML jste nastavili připojené vlastnosti pomocí syntaxe *AttachedPropertyProvider*. Vlastnost *PropertyName*

Následuje příklad, jak lze nastavit <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> v jazyce XAML:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Použití je poněkud podobné statické vlastnosti; vždy odkazujete na typ <xref:System.Windows.Controls.DockPanel> , který vlastní a registruje připojenou vlastnost, a neodkazování na žádnou instanci určenou názvem.

Vzhledem k tomu, že připojená vlastnost v jazyce XAML je atributem, který jste nastavili v kódu, má jakákoli závažnost pouze operace set. V jazyce XAML nelze přímo získat vlastnost, i když existují některé nepřímé mechanismy pro porovnávání hodnot, jako jsou například triggery v stylech (podrobnosti naleznete v tématu [stylování a šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md)).

### <a name="attached-property-implementation-in-wpf"></a>Implementace připojené vlastnosti v subsystému WPF

V nástroji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jsou většina přidružených vlastností souvisejících s uživatelským rozhraním pro typy WPF implementována jako vlastnosti závislosti. Připojené vlastnosti jsou koncept XAML, zatímco vlastnosti závislosti jsou koncept WPF. Vzhledem k tomu, že připojené vlastnosti WPF jsou vlastnosti závislosti, podporují koncepty vlastností závislosti, jako jsou metadata vlastností, a výchozí hodnoty z metadat těchto vlastností.

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>Jak se používají připojené vlastnosti pomocí vlastnícího typu<a name="howused"></a>

I když jsou připojené vlastnosti nastavované u libovolného objektu, který není automaticky znamenat, že nastavení vlastnosti vytvoří hmotný výsledek nebo že hodnota bude někdy použita jiným objektem. Obecně jsou určené vlastnosti určeny tak, aby objekty přicházející z široké škály možných hierarchií tříd nebo logických vztahů mohly každou sestavu tvořit společné informace o typu, který definuje připojenou vlastnost. Typ definující připojenou vlastnost obvykle následuje jeden z těchto modelů:

- Typ, který definuje připojenou vlastnost, je navržen tak, aby mohl být nadřazeným prvkem prvků, které nastaví hodnoty pro připojenou vlastnost. Typ poté provede iteraci svých podřízených objektů prostřednictvím interní logiky proti některé struktuře stromové struktury objektů, získá hodnoty a bude nějakým způsobem pracovat na těchto hodnotách.

- Typ, který definuje připojenou vlastnost, bude použit jako podřízený prvek pro celou řadu možných nadřazených prvků a modelů obsahu.

- Typ definující připojenou vlastnost představuje službu. Další typy nastavují hodnoty pro připojenou vlastnost. Poté, když je prvek, který nastavuje vlastnost, vyhodnocen v kontextu služby, jsou hodnoty připojených vlastností získány prostřednictvím interní logiky třídy služby.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Příklad vlastnosti připojené k nadřazenému elementu

Nejběžnějším scénářem, kde WPF definuje připojenou vlastnost, je, když nadřazený prvek podporuje kolekci podřízených elementů a také implementuje chování, kde jsou konkrétního chování hlášeny jednotlivě pro každý podřízený element.

<xref:System.Windows.Controls.DockPanel>definuje <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> připojenou vlastnost a <xref:System.Windows.Controls.DockPanel> má kód na úrovni třídy jako součást logiky vykreslování (konkrétně <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> a <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A> ). <xref:System.Windows.Controls.DockPanel>Instance vždy zkontroluje, zda některý z jeho bezprostředních podřízených prvků nastavil hodnotu pro <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> . V takovém případě se tyto hodnoty stanou vstupem pro logiku vykreslování použitou pro tento konkrétní podřízený element. Vnořené <xref:System.Windows.Controls.DockPanel> instance každý z nich zachází s vlastními přímými podřízenými kolekcemi prvků, ale toto chování je specifické pro <xref:System.Windows.Controls.DockPanel> zpracování <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> hodnot. Je teoreticky možné mít připojené vlastnosti, které ovlivňují prvky přesahující bezprostřední nadřazený prvek. Pokud <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je připojená vlastnost nastavena u prvku, který nemá žádný <xref:System.Windows.Controls.DockPanel> nadřazený element, který by na něj pracoval, není vyvolána žádná chyba ani výjimka. To jednoduše znamená, že byla nastavena globální hodnota vlastnosti, ale nemá žádnou aktuální <xref:System.Windows.Controls.DockPanel> nadřazenou položku, která by mohla tyto informace spotřebovat.

## <a name="attached-properties-in-code"></a>Připojené vlastnosti v kódu<a name="attached_properties_code"></a>

Připojené vlastnosti v subsystému WPF nemají typické metody "obálky" CLR pro snadný přístup get/set. Je to proto, že připojená vlastnost není nutně součástí oboru názvů CLR pro instance, kde je nastavena vlastnost. Procesor XAML však musí být schopný nastavit tyto hodnoty při analýze XAML. Pro podporu efektivního použití připojené vlastnosti musí typ vlastníka připojené vlastnosti implementovat metody vyhrazeného přístupového objektu ve formuláři **Get_PropertyName_** a **Set_PropertyName_**. Tyto vyhrazené přístupové metody jsou také užitečné k získání nebo nastavení připojené vlastnosti v kódu. Z hlediska kódu je připojená vlastnost podobná zálohovacímu poli, které má přístupové objekty metod namísto přistupujících objektů vlastností, a toto pole pro zálohování může existovat na jakémkoli objektu, a nikoli proto, aby bylo nutné je konkrétně definovat.

Následující příklad ukazuje, jak lze nastavit připojenou vlastnost v kódu. V tomto příkladu `myCheckBox` je instancí <xref:System.Windows.Controls.CheckBox> třídy.

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

Podobně jako v případě jazyka XAML, pokud ještě `myCheckBox` nebyl přidán jako podřízený prvek `myDockPanel` čtvrtého řádku kódu, by pátý řádek kódu nevyvolávají výjimku, ale hodnota vlastnosti nebude pracovat s nadřazeným objektem, <xref:System.Windows.Controls.DockPanel> takže by nevedla žádné akce. Pouze <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> hodnota nastavená u podřízeného prvku v kombinaci s přítomností <xref:System.Windows.Controls.DockPanel> nadřazeného elementu způsobí efektivní chování ve vykreslené aplikaci. (V tomto případě můžete nastavit připojenou vlastnost a pak se připojit ke stromu. Nebo se můžete připojit ke stromu a potom nastavit připojenou vlastnost. Stejný výsledek poskytuje buď pořadí akcí.)

## <a name="attached-property-metadata"></a>Připojená metadata vlastnosti<a name="attached_properties_metadata"></a>

Při registraci vlastnosti <xref:System.Windows.FrameworkPropertyMetadata> je nastavena k určení vlastností vlastnosti, například zda vlastnost ovlivňuje vykreslování, měření a tak dále. Metadata pro připojenou vlastnost se obecně neliší od vlastnosti závislosti. Pokud zadáte výchozí hodnotu v přepsání pro připojená metadata vlastnosti, tato hodnota se změní na výchozí hodnotu implicitní připojená vlastnost v instancích přepisované třídy. Konkrétně je výchozí hodnota hlášena, pokud se některé procesy dotazují na hodnotu připojené vlastnosti prostřednictvím `Get` přístupového objektu metody pro danou vlastnost, zadáním instance třídy, kde jste zadali metadata, a hodnota pro tuto připojenou vlastnost nebyla nastavena jinak.

Pokud chcete povolit dědění hodnoty vlastností u vlastnosti, měli byste použít připojené vlastnosti místo nepřipojených vlastností závislosti. Podrobnosti najdete v tématu [Dědičnost hodnot vlastností](property-value-inheritance.md).

## <a name="custom-attached-properties"></a>Vlastní připojené vlastnosti<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>Kdy vytvořit připojenou vlastnost<a name="create_attached_properties"></a>

Můžete vytvořit připojenou vlastnost, pokud existuje důvod, že má být mechanismus nastavení vlastnosti dostupný pro jiné třídy než definující třídu. Nejběžnější scénář pro toto je rozložení. Příklady existujících vlastností rozložení jsou <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> , <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> . Scénář je zde povolený, protože prvky, které existují jako podřízené prvky pro prvky pro řízení rozložení, mohou vyjádřit požadavky na rozložení na své nadřazené prvky rozložení jednotlivě, přičemž každý nastaví hodnotu vlastnosti, kterou nadřazený objekt definoval jako připojenou vlastnost.

Dalším scénářem použití připojené vlastnosti je, když třída reprezentuje službu a chcete, aby třídy byly schopné integrovat službu transparentně.

Další možností je získat podporu návrháře WPF v aplikaci Visual Studio, jako je například úpravy okna **vlastností** . Další informace najdete v tématu [Přehled tvorby řízení](../controls/control-authoring-overview.md).

Jak už bylo uvedeno dříve, měli byste se zaregistrovat jako připojenou vlastnost, pokud chcete použít dědičnost hodnot vlastností.

### <a name="how-to-create-an-attached-property"></a>Vytvoření připojené vlastnosti<a name="how_do_i_create_attached_properties"></a>

Pokud vaše třída definuje připojenou vlastnost výhradně pro použití v jiných typech, pak třída nemusí odvozovat z <xref:System.Windows.DependencyObject> . Ale musíte odvozovat z, <xref:System.Windows.DependencyObject> Pokud budete postupovat podle celkového modelu WPF, který má přiřazenou vlastnost, ale také vlastnost závislosti.

Definujte připojenou vlastnost jako vlastnost závislosti deklarováním `public static readonly` pole typu <xref:System.Windows.DependencyProperty> . Toto pole definujete pomocí návratové hodnoty <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody. Název pole musí odpovídat názvu připojené vlastnosti připojenému k řetězci `Property` , aby bylo možné postupovat podle zavedeného vzoru WPF pojmenování identifikujících polí a vlastností, které představují. Připojený zprostředkovatel vlastností musí také poskytovat statické **Get_PropertyName_** a **Set_PropertyName_** metody jako přístupové objekty pro připojenou vlastnost; Pokud se to nepovede, výsledkem je, že systém vlastností nemůže použít vaši připojenou vlastnost.

> [!NOTE]
> Vynecháte-li přistupující objekt get připojené vlastnosti, datová vazba u vlastnosti nebude fungovat v nástrojích pro návrh, jako je například Visual Studio a Blend pro Visual Studio.

#### <a name="the-get-accessor"></a>Přístupový objekt get

Podpis přístupového objektu **Get_PropertyName_** musí být:

`public static object GetPropertyName(object target)`

- `target`Objekt může být zadán jako konkrétnější typ v implementaci. Například <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> metoda typu parametru <xref:System.Windows.UIElement> , protože připojená vlastnost je určena pouze pro <xref:System.Windows.UIElement> instance.

- Návratová hodnota může být v implementaci zadána jako konkrétnější typ. Například <xref:System.Windows.Controls.DockPanel.GetDock%2A> Metoda je typu <xref:System.Windows.Controls.Dock> , protože hodnota může být nastavena pouze na tento výčet.

#### <a name="the-set-accessor"></a>Přístupový objekt set

Podpis přístupového objektu **Set_PropertyName_** musí být:

`public static void SetPropertyName(object target, object value)`

- `target`Objekt může být zadán jako konkrétnější typ v implementaci. Například <xref:System.Windows.Controls.DockPanel.SetDock%2A> Metoda je typu <xref:System.Windows.UIElement> , protože připojená vlastnost je určena pouze pro <xref:System.Windows.UIElement> instance.

- `value`Objekt může být zadán jako konkrétnější typ v implementaci. Například <xref:System.Windows.Controls.DockPanel.SetDock%2A> Metoda je typu <xref:System.Windows.Controls.Dock> , protože hodnota může být nastavena pouze na tento výčet. Pamatujte, že hodnota pro tuto metodu je vstup pocházející z zavaděče XAML, když narazí na připojenou vlastnost v použití přidružené vlastnosti v kódu. Tento vstup je hodnota zadaná jako hodnota atributu XAML v kódu. Proto pro typ, který používáte, musí být podporován převod typu, serializátor hodnoty nebo rozšíření značek, aby příslušný typ mohl být vytvořen z hodnoty atributu (což je nakonec pouze řetězec).

Následující příklad ukazuje registraci vlastnosti závislosti (pomocí <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody) a také **Get_PropertyName_** a přístupové objekty **Set_PropertyName_** . V tomto příkladu je název připojené vlastnosti `IsBubbleSource` . Proto musí být přistupující objekty pojmenovány `GetIsBubbleSource` a `SetIsBubbleSource` .

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>Atributy připojených vlastností

WPF definuje několik atributů rozhraní .NET, které mají poskytovat informace o připojených vlastnostech k procesům reflexe a typickým uživatelům informací o reflexi a vlastnostech, jako jsou například návrháři. Vzhledem k tomu, že připojené vlastnosti mají typ neomezeného rozsahu, návrháři potřebují způsob, jak vyhnout zahlcení uživatelů globálním seznamem všech připojených vlastností, které jsou definovány v konkrétní implementaci technologie využívající XAML. Atributy rozhraní .NET, které WPF definuje pro připojené vlastnosti, lze použít k určení rozsahu situací, kdy se má daná připojená vlastnost zobrazit v okně Vlastnosti. Můžete zvážit použití těchto atributů také pro vlastní připojené vlastnosti. Účel a syntax atributů rozhraní .NET jsou popsány na příslušných referenčních stránkách:

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>Další informace o připojených vlastnostech<a name="more"></a>

- Další informace o vytvoření připojené vlastnosti najdete v tématu [registrace připojené vlastnosti](how-to-register-an-attached-property.md).

- Pokročilejší scénáře použití vlastností závislosti a připojených vlastností najdete v tématu [vlastnosti vlastních závislostí](custom-dependency-properties.md).

- Vlastnost můžete také zaregistrovat jako připojenou vlastnost a jako vlastnost závislosti, ale pak pořád vystavovat implementace "obálku". V tomto případě lze vlastnost nastavit buď na daném prvku, nebo na jakémkoli prvku prostřednictvím syntaxe připojené vlastnosti XAML. Příkladem vlastnosti s vhodným scénářem pro standardní i připojené použití je <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType> .

## <a name="see-also"></a>Viz také

- <xref:System.Windows.DependencyProperty>
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Registrace přidružené vlastnosti](how-to-register-an-attached-property.md)
