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
ms.openlocfilehash: 76ff60cfe26f9105d4504164802987115fc2a7e2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455473"
---
# <a name="attached-events-overview"></a>Přehled připojených událostí

Jazyk Extensible Application Markup Language (XAML) (XAML) definuje jazykovou komponentu a typ události, která se nazývá *připojená událost*. Koncept připojené události umožňuje přidat obslužnou rutinu pro konkrétní událost libovolnému prvku, nikoli prvku, který skutečně definuje nebo dědí událost. V takovém případě objekt potenciálně nevyvolal událost, ani instance zpracování cíle nedefinuje nebo jinak vlastní událost.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že jste si přečetli [Přehled směrované události](routed-events-overview.md) a [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Syntaxe připojené události  
 Připojené události mají syntaxi jazyka XAML a vzor kódu, který musí být použit v případě, že se používá záložní kód, aby bylo možné podporovat použití připojené události.  
  
 V syntaxi jazyka XAML je připojená událost určena nejen názvem události, ale podle jejího vlastnícího typu a názvu události oddělené tečkou (.). Vzhledem k tomu, že název události je kvalifikován s názvem jeho vlastnícího typu, připojená syntaxe události umožňuje připojit jakoukoli připojenou událost k jakémukoli prvku, který lze vytvořit z instance.  
  
 Například následuje syntaxe jazyka XAML pro připojení obslužné rutiny vlastní `NeedsCleaning` připojené události:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Všimněte si `aqua:` předpony; v tomto případě je nutná předpona, protože připojená událost je vlastní událost, která přichází z vlastního mapovaného xmlns.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Jak WPF implementuje připojené události

V subsystému WPF jsou připojené události zajištěny <xref:System.Windows.RoutedEvent> poli a jsou směrovány prostřednictvím stromu po jejich vyvolání. Zdroj připojené události (objekt, který vyvolává událost) obvykle představuje systém nebo zdroj služby a objekt, který spouští kód, který vyvolává událost, není proto přímo součástí stromu elementu.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Scénáře pro připojené události  
 V rámci WPF jsou připojené události přítomny v některých oblastech funkce, kde se nachází abstrakce na úrovni služby, například pro události, které jsou povolené třídou static <xref:System.Windows.Input.Mouse> nebo <xref:System.Windows.Controls.Validation> třídy. Třídy, které pracují se službou nebo používají službu, mohou buď používat událost v připojené syntaxi události, nebo mohou zvolit, že připojená událost bude připojena jako směrované událost, která je součástí způsobu, jakým třída integruje schopnosti služby.  
  
 I když WPF definuje množství připojených událostí, ve scénářích, kdy budete buď používat nebo zpracovávat připojenou událost přímo, velmi omezené. Obecně připojená událost slouží k účelu architektury, ale je poté předána na nepřipojenou (se zálohovaná s událostí CLR "obálk"), která je směrována.  
  
 Například základní připojené události <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> lze snadněji zpracovat v jakémkoli z daných <xref:System.Windows.UIElement> pomocí <xref:System.Windows.UIElement.MouseDown> na daném <xref:System.Windows.UIElement> spíše než při práci s připojenou syntaxí události v jazyce XAML nebo kódu. Připojená událost slouží k tomu účelu v architektuře, protože umožňuje budoucí rozšíření vstupních zařízení. Hypotetické zařízení by pro simulaci vstupu myši vyžadovalo, aby vyvolalo <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>, a proto by nemuseli odvozovat od <xref:System.Windows.Input.Mouse>. Nicméně tento scénář zahrnuje zpracování kódu událostí a zpracování XAML připojené události není relevantní pro tento scénář.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Zpracování připojené události v subsystému WPF  
 Proces pro zpracování připojené události a kód obslužné rutiny, který budete zapisovat, je v podstatě stejný jako u směrované události.  
  
 Obecně je připojená událost WPF nerozdílná od události směrovaného WPF. Rozdíly představují způsob, jakým je událost zdrojem, a způsob jejich zpřístupnění třídou jako člen (což má vliv na syntaxi obslužné rutiny XAML).  
  
 Jak již bylo uvedeno dříve, existující události připojené k WPF nejsou zejména určeny pro zpracování v WPF. Častým účelem události je povolit složený element, aby nahlásil stav nadřazenému prvku v skládání. v takovém případě je událost obvykle vyvolána v kódu a také spoléhá na zpracování tříd v příslušné nadřazené třídě. Například položky v rámci <xref:System.Windows.Controls.Primitives.Selector> mají vyvolat připojenou událost <xref:System.Windows.Controls.Primitives.Selector.Selected>, která je poté třída zpracována třídou <xref:System.Windows.Controls.Primitives.Selector> a následně může být převedena <xref:System.Windows.Controls.Primitives.Selector> třídou do jiné směrované události <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>. Další informace o směrovaných událostech a zpracování tříd naleznete v tématu [Označení směrovaných událostí jako zpracovaných a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definování vlastních připojených událostí jako směrovaných událostí  
 Pokud odvozete ze běžných základních tříd WPF, můžete implementovat vlastní připojené události, včetně určitých metod vzoru ve třídě a pomocí pomocných metod, které jsou již přítomny v základních třídách.  
  
 Vzor je následující:  
  
- Metoda __přidávají obslužnou rutinu*EventName*__ se dvěma parametry. První parametr je instance, ke které je přidána obslužná rutina události. Druhý parametr je obslužná rutina události, která se má přidat. Metoda musí být `public` a `static`bez návratové hodnoty.  
  
- Metoda __odebrání obslužné rutiny*EventName*__ se dvěma parametry. První parametr je instance, ze které je obslužná rutina události odebrána. Druhý parametr je obslužná rutina události, která se má odebrat. Metoda musí být `public` a `static`bez návratové hodnoty.  
  
 Metoda __Přidat přístupový objekt obslužné rutiny*EventName*__ usnadňuje zpracování XAML, když jsou připojené atributy obslužné rutiny události deklarovány u elementu. Metoda __Přidáníobslužné__ rutiny EventName a __odebrat obslužné rutiny*EventName*__ také umožňuje přístup kódu k úložišti obslužných rutin událostí pro připojenou událost.  
  
 Tento obecný vzor není zatím dostatečně přesný pro praktické implementace v rámci architektury, protože jakákoli konkrétní implementace čtečky XAML může mít různá schémata pro identifikaci základních událostí v podpůrném jazyce a architektuře. Toto je jeden z důvodů, proč WPF implementuje připojené události jako směrované události. identifikátor, který má být použit pro událost (<xref:System.Windows.RoutedEvent>), je již definován systémem událostí WPF. Směrování události je také rozšířením přirozené implementace v konceptu na úrovni jazyka XAML připojené události.  
  
 Implementace __obslužné rutiny*EventName*__ pro událost připojenou k WPF se skládá z volání <xref:System.Windows.UIElement.AddHandler%2A> s směrovanou událostí a obslužnou rutinou jako argumenty.  
  
 Tato strategie implementace a systém směrovaného systému událostí obecně omezují manipulaci s připojenými událostmi buď <xref:System.Windows.UIElement> odvozenými třídami, nebo <xref:System.Windows.ContentElement> odvozených tříd, protože pouze tyto třídy mají <xref:System.Windows.UIElement.AddHandler%2A> implementace.  
  
 Například následující kód definuje `NeedsCleaning` připojenou událost na třídě Owner `Aquarium`pomocí strategie události připojené k WPF, která deklaruje připojenou událost jako směrovanou událost.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Všimněte si, že metoda použitá pro vytvoření pole identifikátoru připojené události <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>je vlastně stejnou metodou, která se používá k registraci nepřipojené směrované události. Připojené události a směrované události jsou zaregistrované do centralizovaného interního úložiště. Tato implementace úložiště událostí umožňuje koncepční porozumění "událostem jako rozhraní", které je popsáno v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Vyvolává se událost připojená k WPF.  
 Obvykle není nutné vyvolat existující připojené události definované WPF z kódu. Tyto události následují jako Obecné koncepční modely služby a třídy služeb, jako je <xref:System.Windows.Input.InputManager>, jsou zodpovědné za vyvolání událostí.  
  
 Pokud však definujete vlastní připojenou událost založenou na modelu WPF, na kterých jsou připojené události na <xref:System.Windows.RoutedEvent>, můžete pomocí <xref:System.Windows.UIElement.RaiseEvent%2A> vyvolat připojenou událost z libovolného <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement>. Vyvolání směrované události (připojená nebo ne) vyžaduje deklaraci konkrétního prvku ve stromu elementu jako zdroj události; Tento zdroj je hlášen jako volající <xref:System.Windows.UIElement.RaiseEvent%2A>. Určení prvku, který je hlášen jako zdroj ve stromu, je zodpovědností vaší služby  
  
## <a name="see-also"></a>Viz také:

- [Přehled směrovaných událostí](routed-events-overview.md)
- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
- [XAML a vlastní třídy pro WPF](xaml-and-custom-classes-for-wpf.md)
