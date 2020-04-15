---
title: Přehled připojených vlastností
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 5086401f4616074d364c1d387b751116120d5969
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389004"
---
# <a name="attached-properties-overview"></a>Přehled připojených vlastností

Připojená vlastnost je koncept definovaný XAML. Připojená vlastnost je určena k použití jako typ globální vlastnosti, která je tahovitelná na libovolném objektu. V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]aplikace jsou připojené vlastnosti obvykle definovány jako specializovaná forma vlastnosti závislosti, která nemá konvenční vlastnost "obálka".

## <a name="prerequisites"></a>Požadavky<a name="prerequisites"></a>

Toto téma předpokládá, že rozumíte vlastnostem závislostí z pohledu příjemce existujících vlastností závislostí na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídách a že jste si přečetli přehled [vlastností závislostí](dependency-properties-overview.md). Chcete-li sledovat příklady v tomto tématu, měli byste také pochopit XAML a vědět, jak psát aplikace WPF.

## <a name="why-use-attached-properties"></a>Proč používat připojené vlastnosti<a name="attached_properties_usage"></a>

Jedním z účelů připojené vlastnosti je umožnit různým podřízeným prvkům určit jedinečné hodnoty pro vlastnost, která je ve skutečnosti definována v nadřazeném prvku. Konkrétní aplikace tohoto scénáře má podřízené prvky informovat nadřazený [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]prvek o tom, jak mají být prezentovány v . Jedním z <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> příkladů je vlastnost. Vlastnost <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je vytvořena jako připojená vlastnost, protože je určena k nastavení <xref:System.Windows.Controls.DockPanel>na prvky, které jsou obsaženy v aplikaci , nikoli na <xref:System.Windows.Controls.DockPanel> sobě. Třída <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.DependencyProperty> definuje statické pole <xref:System.Windows.Controls.DockPanel.DockProperty>s názvem a <xref:System.Windows.Controls.DockPanel.GetDock%2A> <xref:System.Windows.Controls.DockPanel.SetDock%2A> pak poskytuje a metody jako veřejné přístupové objekty pro připojené vlastnosti.

## <a name="attached-properties-in-xaml"></a>Připojené vlastnosti v XAML<a name="attached_properties_xaml"></a>

V XAML nastavíte připojené vlastnosti pomocí syntaxe *AttachedPropertyProvider*. *PropertyName*

Následuje příklad nastavení <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> v XAML:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Všimněte si, že použití je poněkud podobné statické vlastnosti; vždy odkazujete <xref:System.Windows.Controls.DockPanel> na typ, který vlastní a registruje připojenou vlastnost, spíše než odkazovat na jakoukoli instanci určenou názvem.

Také vzhledem k tomu, že připojená vlastnost v XAML je atribut, který nastavíte ve značkách, pouze operace sady má jakýkoli význam. Nelze přímo získat vlastnost v XAML, i když existují některé nepřímé mechanismy pro porovnávání hodnot, jako jsou aktivační události ve stylech (podrobnosti naleznete [v tématu Styling a Templating](../controls/styling-and-templating.md)).

### <a name="attached-property-implementation-in-wpf"></a>Implementace připojené vlastnosti v WPF

V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], většina připojených vlastností, které existují na WPF typy, které souvisejí s prezentací uvi jsou implementovány jako vlastnosti závislostí. Připojené vlastnosti jsou koncept XAML, zatímco vlastnosti závislostí jsou koncept WPF. Vzhledem k tomu, že připojené vlastnosti WPF jsou vlastnosti závislostí, podporují koncepty vlastností závislostí, jako jsou metadata vlastností, a výchozí hodnoty z metadat této vlastnosti.

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>Jak připojené vlastnosti jsou používány vlastnící typ<a name="howused"></a>

Přestože připojené vlastnosti jsou settable na libovolný objekt, to neznamená automaticky, že nastavení vlastnosti bude produkovat hmatatelný výsledek, nebo že hodnota bude někdy použit a jiný objekt. Obecně připojené vlastnosti jsou určeny tak, aby objekty pocházející z široké škály možných hierarchií tříd nebo logických vztahů mohou každý sestavovat společné informace typu, který definuje připojenou vlastnost. Typ, který definuje připojené vlastnosti obvykle následuje jeden z těchto modelů:

- Typ, který definuje připojené vlastnosti je navržen tak, aby může být nadřazený prvek prvků, které nastaví hodnoty pro připojené vlastnosti. Typ pak iterates jeho podřízené objekty prostřednictvím vnitřní logiky proti některé stromové struktury objektu, získá hodnoty a funguje na tyto hodnoty nějakým způsobem.

- Typ, který definuje připojené vlastnosti budou použity jako podřízený prvek pro řadu možných nadřazených prvků a obsahových modelů.

- Typ, který definuje připojené vlastnosti představuje službu. Jiné typy nastavují hodnoty připojené vlastnosti. Potom při elementu, který nastavuje vlastnost je vyhodnocena v kontextu služby, připojené hodnoty vlastností jsou získány prostřednictvím vnitřní logiky třídy služby.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Příklad nadřazené připojené vlastnosti

Nejtypičtější scénář, kde WPF definuje připojené vlastnosti je, když nadřazený prvek podporuje kolekci podřízený prvek a také implementuje chování, kde jsou specifika chování hlášeny jednotlivě pro každý podřízený prvek.

<xref:System.Windows.Controls.DockPanel>definuje připojenou <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> vlastnost a <xref:System.Windows.Controls.DockPanel> má kód na úrovni třídy jako <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> součást <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>jeho logiky vykreslování (konkrétně a). Instance <xref:System.Windows.Controls.DockPanel> bude vždy zkontrolovat, zda některý z jeho bezprostředně <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>podřízených prvků nastavili hodnotu pro . Pokud ano, tyto hodnoty stanou vstupem pro logiku vykreslování aplikovanou na tento konkrétní podřízený prvek. Vnořené <xref:System.Windows.Controls.DockPanel> instance každý zacházet s jejich vlastní kolekce bezprostředně podřízený prvek, ale toto chování je specifické pro implementaci, jak <xref:System.Windows.Controls.DockPanel> zpracovává <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> hodnoty. Teoreticky je možné mít připojené vlastnosti, které ovlivňují prvky mimo bezprostřední nadřazení. Pokud <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je připojená vlastnost nastavena na <xref:System.Windows.Controls.DockPanel> prvek, který nemá žádný nadřazený prvek, který by s ním mohl působit, je vyvolána žádná chyba nebo výjimka. To jednoduše znamená, že byla nastavena hodnota <xref:System.Windows.Controls.DockPanel> globální vlastnosti, ale nemá žádné aktuální nadřazené položky, které by mohly využívat informace.

## <a name="attached-properties-in-code"></a>Připojené vlastnosti v kódu<a name="attached_properties_code"></a>

Připojené vlastnosti v WPF nemají typické CLR "obálka" metody pro snadný přístup k získání /set. Důvodem je, že připojené vlastnosti není nutně součástí oboru názvů CLR pro instance, kde je vlastnost nastavena. Procesor XAML však musí být schopen nastavit tyto hodnoty při analýzě XAML. Pro podporu efektivní připojení využití vlastnosti, vlastník typ připojené vlastnosti musí implementovat vyhrazené přístupové metody ve formuláři **Get_PropertyName_** a **Set_PropertyName_**. Tyto vyhrazené přístupové metody jsou také užitečné získat nebo nastavit připojené vlastnosti v kódu. Z hlediska kódu připojené vlastnosti je podobný doprovodné pole, které má přístupové objekty metody namísto přístupové objekty vlastností a že záložní pole může existovat na libovolný objekt, spíše než je třeba konkrétně definovat.

Následující příklad ukazuje, jak můžete nastavit připojenou vlastnost v kódu. V tomto `myCheckBox` příkladu je <xref:System.Windows.Controls.CheckBox> instance třídy.

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

Podobně jako případ XAML, pokud `myCheckBox` již nebyly přidány `myDockPanel` jako podřízený prvek čtvrtý řádek kódu, pátý řádek kódu by nevyvolal výjimku, ale hodnota vlastnosti by neinteragoval s nadřazeným <xref:System.Windows.Controls.DockPanel> a proto by neprovedla nic. Pouze <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> hodnota nastavená na podřízený prvek v <xref:System.Windows.Controls.DockPanel> kombinaci s přítomností nadřazeného prvku způsobí efektivní chování v vykreslené aplikaci. (V tomto případě můžete nastavit připojenou vlastnost a připojit ji ke stromu. Nebo můžete připojit ke stromu a nastavit připojenou vlastnost. Buď pořadí akcí poskytuje stejný výsledek.)

## <a name="attached-property-metadata"></a>Metadata připojené vlastnosti<a name="attached_properties_metadata"></a>

Při registraci vlastnosti je <xref:System.Windows.FrameworkPropertyMetadata> nastavena na určení charakteristiky vlastnosti, například zda vlastnost ovlivňuje vykreslování, měření a tak dále. Metadata pro připojenou vlastnost se obecně neliší od vlastnosti závislosti. Pokud zadáte výchozí hodnotu v přepsání metadat připojené vlastnosti, stane se tato hodnota výchozí hodnotou implicitní připojené vlastnosti na instancích přepsání třídy. Konkrétně výchozí hodnota je hlášena, pokud některé dotazy procesu pro `Get` hodnotu připojené vlastnosti prostřednictvím přístupového objektu metody pro tuto vlastnost, určení instance třídy, kde jste zadali metadata a hodnota pro tuto připojenou vlastnost jinak nebyla nastavena.

Pokud chcete povolit dědičnost hodnoty vlastnosti na vlastnost, měli byste použít připojené vlastnosti spíše než nepřipojené vlastnosti závislostí. Podrobnosti naleznete v [tématu Dědičnost hodnoty nemovitosti](property-value-inheritance.md).

## <a name="custom-attached-properties"></a>Vlastní připojené vlastnosti<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>Kdy vytvořit připojenou vlastnost<a name="create_attached_properties"></a>

Můžete vytvořit připojené vlastnosti, pokud existuje důvod mít mechanismus nastavení vlastnosti k dispozici pro třídy než definující třídy. Nejběžnější scénář pro toto je rozložení. Příklady existujících vlastností <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>rozložení <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>jsou <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, a . Scénář povolen zde je, že prvky, které existují jako podřízené prvky prvky ovládací rozložení jsou schopny vyjádřit požadavky na rozložení jejich rozložení nadřazené prvky jednotlivě, každý nastavení hodnoty vlastnosti, která nadřazený definován jako připojené vlastnosti.

Jiný scénář pro použití připojené vlastnosti je, když vaše třída představuje službu a chcete třídy, které mají být možné integrovat službu transparentněji.

Dalším scénářem je příjem podpory návrháře WPF sady Visual Studio, jako je například úpravy okna **Vlastnosti.** Další informace naleznete [v tématu Přehled vytváření ovládacích prvku](../controls/control-authoring-overview.md).

Jak již bylo zmíněno dříve, měli byste se zaregistrovat jako připojená vlastnost, pokud chcete použít dědičnost hodnoty vlastnosti.

### <a name="how-to-create-an-attached-property"></a>Jak vytvořit připojenou vlastnost<a name="how_do_i_create_attached_properties"></a>

Pokud vaše třída definuje připojené vlastnosti výhradně pro použití na jiné typy, <xref:System.Windows.DependencyObject>pak třída nemusí odvodit z . Ale je třeba odvodit z <xref:System.Windows.DependencyObject> pokud budete postupovat podle celkového modelu WPF s připojené vlastnosti také závislost vlastnost.

Definujte připojenou vlastnost jako vlastnost závislosti `public static readonly` deklarováním pole typu <xref:System.Windows.DependencyProperty>. Toto pole definujete pomocí vrácené hodnoty <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody. Název pole se musí shodovat s připojeným názvem vlastnosti, připojeným k řetězci `Property`, aby se řídil zavedeným vzorem WPF, který pojmenovává identifikační pole oproti vlastnostem, které představují. Poskytovatel připojené vlastnosti musí také poskytnout statické **Get_PropertyName_** a **Set_PropertyName_** metody jako přístupové objekty pro připojené vlastnosti; Pokud tak neučiníte, bude mít systém vlastností možnost používat připojenou vlastnost.

> [!NOTE]
> Pokud vynecháte přistupující objekt get připojené vlastnosti, datová vazba na vlastnost nebude fungovat v nástrojích návrhu, jako je například Visual Studio a Blend pro Visual Studio.

#### <a name="the-get-accessor"></a>Získat přístupový or

Podpis Get_PropertyName_ přistupujícího **zařízení** musí být:

`public static object GetPropertyName(object target)`

- Objekt `target` lze zadat jako konkrétnější typ v implementaci. Například <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> metoda zadá parametr <xref:System.Windows.UIElement>jako , protože připojená vlastnost je <xref:System.Windows.UIElement> určena pouze k nastavení na instancích.

- Vrácená hodnota může být zadána jako konkrétnější typ v implementaci. Například <xref:System.Windows.Controls.DockPanel.GetDock%2A> metoda zadá <xref:System.Windows.Controls.Dock>jako , protože hodnota může být nastavena pouze na tento výčet.

#### <a name="the-set-accessor"></a>Přístupový bod sady

Podpis Set_PropertyName_ přistupujícího **oru** musí být:

`public static void SetPropertyName(object target, object value)`

- Objekt `target` lze zadat jako konkrétnější typ v implementaci. Například <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda zadá <xref:System.Windows.UIElement>jako , protože připojené vlastnosti je <xref:System.Windows.UIElement> určena pouze k nastavení na instance.

- Objekt `value` lze zadat jako konkrétnější typ v implementaci. Například <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda zadá <xref:System.Windows.Controls.Dock>jako , protože hodnota může být nastavena pouze na tento výčet. Nezapomeňte, že hodnota pro tuto metodu je vstup pocházející z zavaděče XAML, když narazí na připojené vlastnosti v připojené vlastnosti použití v přirážky. Tento vstup je hodnota zadaná jako hodnota atributu XAML ve značkách. Proto musí být převod typu, serializátor hodnoty nebo podpora rozšíření značek pro typ, který používáte, tak, aby příslušný typ lze vytvořit z hodnoty atributu (což je nakonec jen řetězec).

Následující příklad ukazuje registraci vlastnosti <xref:System.Windows.DependencyProperty.RegisterAttached%2A> závislosti (pomocí metody), stejně jako **Get_PropertyName_** a **Set_PropertyName_** přístupové objekty. V příkladu je `IsBubbleSource`název připojené vlastnosti . Proto musí být pojmenovány `GetIsBubbleSource` přístupové řeholní hod a `SetIsBubbleSource`.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>Připojené atributy vlastností

WPF definuje několik atributů .NET, které jsou určeny k poskytování informací o připojených vlastnostech procesu reflexe a typickým uživatelům reflexe a informací o vlastnostech, jako jsou návrháři. Vzhledem k tomu, že připojené vlastnosti mají typ neomezený rozsah, návrháři potřebují způsob, jak se vyhnout zahlcení uživatelů s globálním seznamem všech připojených vlastností, které jsou definovány v konkrétní implementaci technologie, která používá XAML. Atributy .NET, které WPF definuje pro připojené vlastnosti, lze použít k oboru situací, kdy by měla být daná připojená vlastnost zobrazena v okně vlastností. Můžete zvážit použití těchto atributů pro vlastní připojené vlastnosti také. Účel a syntaxe atributů .NET je popsána na příslušných referenčních stránkách:

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>Další informace o připojených vlastnostech<a name="more"></a>

- Další informace o vytvoření připojené vlastnosti naleznete v [tématu Registrace připojené vlastnosti](how-to-register-an-attached-property.md).

- Pokročilejší scénáře použití vlastností závislostí a připojených vlastností naleznete [v tématu Vlastnosti vlastních závislostí](custom-dependency-properties.md).

- Můžete také zaregistrovat vlastnost jako připojené vlastnosti a jako vlastnost závislosti, ale pak stále vystavit "obálky" implementace. V tomto případě vlastnost lze nastavit buď na tento prvek nebo na libovolný prvek prostřednictvím syntaxe připojené vlastnosti XAML. Příkladem vlastnosti s příslušným scénářem pro standardní i <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>připojené použití je .

## <a name="see-also"></a>Viz také

- <xref:System.Windows.DependencyProperty>
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Registrace přidružené vlastnosti](how-to-register-an-attached-property.md)
