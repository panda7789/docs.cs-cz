---
title: Přehled připojených událostí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling attached events [WPF]
- defining attached events as routed events [WPF]
- attached events [WPF], scenarios for
- attached events vs. routed events [WPF]
- backing attached events with routed events [WPF]
- attached events [WPF], definition
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
ms.openlocfilehash: a3a2f711840ad7f6e28443dac3c18501cd4400e0
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401398"
---
# <a name="attached-events-overview"></a>Přehled připojených událostí
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]definuje komponentu jazyka a typ události, která se nazývá *připojená událost*. Koncept připojené události umožňuje přidat obslužnou rutinu pro konkrétní událost libovolnému prvku, nikoli prvku, který skutečně definuje nebo dědí událost. V takovém případě objekt potenciálně nevyvolal událost, ani instance zpracování cíle nedefinuje nebo jinak vlastní událost.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že jste si přečetli [Přehled směrované události](routed-events-overview.md) a [Přehled XAML (WPF)](xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Syntaxe připojené události  
 Připojené události mají [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxi a vzor kódování, který musí být použit v případě, že se jedná o použití připojeného kódu, aby bylo možné podporovat připojené události.  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxi je připojená událost zadána nejen pomocí jejího názvu události, ale pomocí jejího vlastnícího typu a názvu události oddělené tečkou (.). Vzhledem k tomu, že název události je kvalifikován s názvem jeho vlastnícího typu, připojená syntaxe události umožňuje připojit jakoukoli připojenou událost k jakémukoli prvku, který lze vytvořit z instance.  
  
 Následuje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad syntaxe pro připojení obslužné rutiny vlastní `NeedsCleaning` připojené události:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Všimněte si `aqua:` předpony. v takovém případě je nutná předpona, protože připojená událost je vlastní událost, která přichází z vlastního mapovaného xmlns.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Jak WPF implementuje připojené události  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], připojené události jsou zálohovány <xref:System.Windows.RoutedEvent> polem a jsou směrovány prostřednictvím stromu po jejich vyvolání. Zdroj připojené události (objekt, který vyvolává událost) obvykle představuje systém nebo zdroj služby a objekt, který spouští kód, který vyvolává událost, není proto přímo součástí stromu elementu.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Scénáře pro připojené události  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]jsou připojené události přítomny v některých oblastech funkce, kde je abstrakce na úrovni služby, například pro události, které jsou povoleny statickou <xref:System.Windows.Input.Mouse> třídou nebo <xref:System.Windows.Controls.Validation> třídou. Třídy, které pracují se službou nebo používají službu, mohou buď používat událost v připojené syntaxi události, nebo mohou zvolit, že připojená událost bude připojena jako směrované událost, která je součástí způsobu, jakým třída integruje schopnosti služby.  
  
 I [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] když definuje počet připojených událostí, ve scénářích, kdy budete buď používat nebo zpracovávat připojenou událost přímo, velmi omezené. Obecně připojená událost slouží k účelu architektury, ale je poté předána na nepřipojenou (se zálohovaná s událostí CLR "obálk"), která je směrována.  
  
 <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> Například základní připojená událost může být snáze zpracována na <xref:System.Windows.UIElement> jakémkoli základě pomocí <xref:System.Windows.UIElement.MouseDown> , a nikoli s <xref:System.Windows.UIElement> připojenou syntaxí události buď v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódu, nebo. Připojená událost slouží k tomu účelu v architektuře, protože umožňuje budoucí rozšíření vstupních zařízení. Hypotetické zařízení by se muselo vyvolávat <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> jenom pro simulaci vstupu myši a nemusí se odvozovat od <xref:System.Windows.Input.Mouse> tohoto důvodu. Tento scénář však zahrnuje zpracování kódu událostí a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zpracování připojené události není relevantní pro tento scénář.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Zpracování připojené události v subsystému WPF  
 Proces pro zpracování připojené události a kód obslužné rutiny, který budete zapisovat, je v podstatě stejný jako u směrované události.  
  
 Obecně platí, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] připojená událost se neliší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] od směrované události. Rozdíly představují způsob, jakým je událost zdrojem, a způsob jejich zpřístupnění třídou jako člen (což má vliv na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxi obslužné rutiny).  
  
 Jak již bylo uvedeno dříve, existující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] připojené události nejsou zejména určeny ke zpracování v. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Častým účelem události je povolit složený element, aby nahlásil stav nadřazenému prvku v skládání. v takovém případě je událost obvykle vyvolána v kódu a také spoléhá na zpracování tříd v příslušné nadřazené třídě. Například položky <xref:System.Windows.Controls.Primitives.Selector> v rámci mají vyvolat připojenou <xref:System.Windows.Controls.Primitives.Selector.Selected> událost, která je <xref:System.Windows.Controls.Primitives.Selector> pak třídou zpracována třídou a následně může být převedena <xref:System.Windows.Controls.Primitives.Selector> třídou na jinou směrovanou událost, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Další informace o směrovaných událostech a zpracování tříd naleznete v tématu [Označení směrovaných událostí jako zpracovaných a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definování vlastních připojených událostí jako směrovaných událostí  
 Pokud se odvozují ze společných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] základních tříd, můžete implementovat vlastní připojené události, včetně určitých metod vzoru ve třídě a pomocí pomocných metod, které jsou již přítomny v základních třídách.  
  
 Vzor je následující:  
  
- Metoda **přidávají obslužnou rutinu*EventName***  se dvěma parametry. První parametr je instance, ke které je přidána obslužná rutina události. Druhý parametr je obslužná rutina události, která se má přidat. Metoda musí být `public` a `static`, bez návratové hodnoty.  
  
- Metoda **odebrání obslužné rutiny*EventName***  se dvěma parametry. První parametr je instance, ze které je obslužná rutina události odebrána. Druhý parametr je obslužná rutina události, která se má odebrat. Metoda musí být `public` a `static`, bez návratové hodnoty.  
  
 Metoda **Přidat přístupový objekt obslužné rutiny*EventName***  usnadňuje zpracování, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] když jsou připojené atributy obslužné rutiny události deklarovány u elementu. Metoda **Přidání obslužné** rutiny *EventName* a **odebrat obslužné rutiny*EventName***  také umožňuje přístup kódu k úložišti obslužných rutin událostí pro připojenou událost.  
  
 Tento obecný vzor není zatím dostatečně přesný pro praktické implementace v rámci architektury, protože jakákoli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace čtecího modulu může mít různá schémata pro identifikaci základních událostí v podpůrném jazyce a architektuře. Toto je jeden z důvodů, který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementuje připojené události jako směrované události. identifikátor, který má být použit pro událost<xref:System.Windows.RoutedEvent>(), [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je již definován systémem událostí. Směrování události je také rozšířením přirozené implementace v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] konceptu na úrovni jazyka připojené události.  
  
 Implementace **obslužné rutiny*EventName***  pro <xref:System.Windows.UIElement.AddHandler%2A> připojenouudálostseskládázvolánímetodyssměrovanouudálostíaobslužnérutiny[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako argumentů.  
  
 Tato strategie implementace a systém směrovaného systému událostí obecně omezují manipulaci s připojenými událostmi <xref:System.Windows.UIElement> buď na odvozené <xref:System.Windows.ContentElement> třídy, nebo na odvozené třídy, protože <xref:System.Windows.UIElement.AddHandler%2A> pouze tyto třídy mají implementace.  
  
 Například následující kód definuje `NeedsCleaning` připojenou událost třídy `Aquarium`Owner pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strategie připojené události pro deklaraci připojené události jako směrované události.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Všimněte si, že metoda použitá pro vytvoření pole <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>identifikátoru připojené události je vlastně stejnou metodou, která se používá k registraci nepřipojené směrované události. Připojené události a směrované události jsou zaregistrované do centralizovaného interního úložiště. Tato implementace úložiště událostí umožňuje koncepční porozumění "událostem jako rozhraní", které je popsáno v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Vyvolává se událost připojená k WPF.  
 Obvykle není nutné vyvolat existující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definované připojené události z kódu. Tyto události následují jako Obecné koncepční model "služba" a třídy <xref:System.Windows.Input.InputManager> služeb, jako jsou zodpovědné za vyvolání událostí.  
  
 Pokud však definujete vlastní připojenou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událost na základě modelu založených na <xref:System.Windows.RoutedEvent>jednotlivých připojených událostech, můžete použít <xref:System.Windows.UIElement.RaiseEvent%2A> k vyvolání připojené události z libovolného <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement>. Vyvolání směrované události (připojená nebo ne) vyžaduje deklaraci konkrétního prvku ve stromu elementu jako zdroj události; Tento zdroj je hlášen jako <xref:System.Windows.UIElement.RaiseEvent%2A> volající. Určení prvku, který je hlášen jako zdroj ve stromu, je zodpovědností vaší služby  
  
## <a name="see-also"></a>Viz také:

- [Přehled směrovaných událostí](routed-events-overview.md)
- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
- [XAML a vlastní třídy pro WPF](xaml-and-custom-classes-for-wpf.md)
