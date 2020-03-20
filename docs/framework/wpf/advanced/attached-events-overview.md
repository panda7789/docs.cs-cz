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
ms.openlocfilehash: e125c9a57090049f4319da96c7004f06606d0147
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141559"
---
# <a name="attached-events-overview"></a>Přehled připojených událostí

Extensible Application Markup Language (XAML) definuje jazykovou komponentu a typ události nazývané *připojená událost*. Koncept připojené události umožňuje přidat obslužnou rutinu pro konkrétní událost do libovolného prvku, nikoli do prvku, který ve skutečnosti definuje nebo dědí událost. V tomto případě ani objekt potenciálně vyvolání události ani cílové zpracování instance definuje nebo jinak "vlastní" událost.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že jste si přečetli [přehled směrovaných událostí](routed-events-overview.md) a [přehled XAML (WPF).](../../../desktop-wpf/fundamentals/xaml.md)  
  
<a name="Syntax"></a>
## <a name="attached-event-syntax"></a>Syntaxe připojené události  
 Připojené události mají syntaxi XAML a vzor kódování, který musí být použit záložním kódem pro podporu připojeného použití události.  
  
 V syntaxi XAML je připojená událost určena nejen názvem události, ale i vlastním typem plus názvem události odděleným tečkou (.). Vzhledem k tomu, že název události je kvalifikován názvem jeho vlastnícího typu, připojená syntaxe události umožňuje připojit všechny připojené události k libovolnému prvku, který lze vytvořit instanci.  
  
 Například následující je syntaxe XAML pro připojení obslužné rutiny pro vlastní `NeedsCleaning` připojené události:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Poznamenejte `aqua:` si předponu; předpona je v tomto případě nezbytná, protože připojená událost je vlastní událost, která pochází z vlastních mapovaných xmlns.  
  
<a name="WPFImplements"></a>
## <a name="how-wpf-implements-attached-events"></a>Jak WPF implementuje připojené události

V WPF připojené události jsou zálohovány <xref:System.Windows.RoutedEvent> pole a jsou směrovány přes strom po jejich vyvolání. Obvykle zdroj připojené události (objekt, který vyvolává událost) je zdroj systému nebo služby a objekt, který spouští kód, který vyvolává událost proto není přímou součástí stromu elementu.  
  
<a name="Scenarios"></a>
## <a name="scenarios-for-attached-events"></a>Scénáře pro připojené události  
 V WPF připojené události jsou k dispozici v určitých oblastech funkce, kde je abstrakce na úrovni služby, například pro události povolené statickou <xref:System.Windows.Input.Mouse> třídou nebo třídy. <xref:System.Windows.Controls.Validation> Třídy, které interagují nebo používají službu můžete použít událost v připojené události syntaxe, nebo si mohou zvolit povrch připojené události jako směrované události, která je součástí jak třída integruje možnosti služby.  
  
 Přestože WPF definuje počet připojených událostí, scénáře, kde budete používat nebo zpracovávat připojené události přímo jsou velmi omezené. Obecně platí, že připojená událost slouží účelu architektury, ale pak je předána nepřipojené (zálohované událost CLR "obálka") směrované události.  
  
 Například základní připojené události <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> lze snadněji zpracovat <xref:System.Windows.UIElement> na <xref:System.Windows.UIElement.MouseDown> dané <xref:System.Windows.UIElement> pomocí na to spíše než řešení připojené syntaxe události buď v XAML nebo kód. Připojená událost slouží účelu v architektuře, protože umožňuje budoucí rozšíření vstupních zařízení. Hypotetické zařízení by bylo <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> nutné pouze zvýšit, aby simuloval vstup <xref:System.Windows.Input.Mouse> myši a nebude muset odvodit z k tomu. Tento scénář však zahrnuje zpracování kódu událostí a zpracování XAML připojené události není relevantní pro tento scénář.  
  
<a name="Handling"></a>
## <a name="handling-an-attached-event-in-wpf"></a>Zpracování připojené události v WPF  
 Proces zpracování připojené události a kódu obslužné rutiny, který budete psát, je v podstatě stejný jako pro směrovou událost.  
  
 Obecně wpf připojené události se příliš neliší od WPF směrované události. Rozdíly jsou způsob, jakým je událost získávána a jak je vystavena třídou jako člen (což také ovlivňuje syntaxi obslužné rutiny XAML).  
  
 Nicméně, jak již bylo uvedeno dříve, existující WPF připojené události nejsou určeny zejména pro zpracování v WPF. Častěji účelem události je umožnit složený prvek ohlásit stav nadřazeného prvku v skládání, v takovém případě je událost obvykle vyvolána v kódu a také spoléhá na zpracování třídy v příslušné nadřazené třídě. Například položky <xref:System.Windows.Controls.Primitives.Selector> v rámci <xref:System.Windows.Controls.Primitives.Selector.Selected> se očekává, že zvýšit připojené události, která je pak třída <xref:System.Windows.Controls.Primitives.Selector> zpracována třídy a pak potenciálně <xref:System.Windows.Controls.Primitives.Selector> převedeny třídy do jiné směrované události . <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Další informace o směrovaných událostech a zpracování tříd naleznete v [tématu Označení směrovaných událostí jako zpracovaných a Zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definování vlastních připojených událostí jako směrovaných událostí  
 Pokud jste odvozené z běžných WPF základní třídy, můžete implementovat vlastní připojené události zahrnutím určité metody vzoru ve vaší třídě a pomocí metod nástrojů, které jsou již k dispozici na základní třídy.  
  
 Vzor je následující:  
  
- Metoda __Add*EventName*Handler__ se dvěma parametry. První parametr je instance, ke které je přidána obslužná rutina události. Druhý parametr je obslužná rutina události, kterou chcete přidat. Metoda musí `public` být `static`a , bez vrácené hodnoty.  
  
- Metoda __Remove*EventName*Handler__ se dvěma parametry. První parametr je instance, ze které je odebrána obslužná rutina události. Druhý parametr je obslužná rutina události odebrat. Metoda musí `public` být `static`a , bez vrácené hodnoty.  
  
 __Přiřazovací objekt Add*EventName*Handler__ usnadňuje zpracování XAML, když jsou na prvku deklarovány připojené atributy obslužné rutiny události. Metody __Add*EventName*Handler__ a Remove __*EventName*Handler__ také umožňují přístup kódu k úložišti obslužné rutiny události pro připojenou událost.  
  
 Tento obecný vzor ještě není dostatečně přesný pro praktickou implementaci v rámci, protože jakákoli daná implementace čtečky XAML může mít různá schémata pro identifikaci základních událostí v podpůrném jazyce a architektuře. To je jeden z důvodů, proč WPF implementuje připojené události jako směrované události; identifikátor, který má být<xref:System.Windows.RoutedEvent>pro událost ( ) již definován systémem událostí WPF. Směrování události je také přirozené rozšíření implementace na úrovni jazyka XAML konceptpřipojené události.  
  
 Implementace __Add*EventName*Handler__ pro připojenou událost WPF <xref:System.Windows.UIElement.AddHandler%2A> se skládá z volání s směrovou událostí a obslužnou rutinou jako argumenty.  
  
 Tato strategie implementace a směrovaný systém událostí obecně omezit <xref:System.Windows.UIElement> zpracování pro <xref:System.Windows.ContentElement> připojené události odvozené třídy <xref:System.Windows.UIElement.AddHandler%2A> nebo odvozené třídy, protože pouze tyto třídy mají implementace.  
  
 Například následující kód definuje `NeedsCleaning` připojenou událost ve `Aquarium`třídě vlastníka pomocí strategie připojené události WPF deklarování připojené události jako směrované události.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Všimněte si, že metoda použitá k <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>vytvoření připojeného pole identifikátoru události , je ve skutečnosti stejná metoda, která se používá k registraci nepřipojené směrované události. Připojené události a směrované události jsou všechny registrovány do centralizovaného interního úložiště. Tato implementace úložiště událostí umožňuje koncepční úvahu "události jako rozhraní", která je popsána v [přehledu směrovaných událostí](routed-events-overview.md).  
  
<a name="Raising"></a>
## <a name="raising-a-wpf-attached-event"></a>Vyvolání připojené události WPF  
 Obvykle není nutné vyvolat existující WPF definované připojené události z kódu. Tyto události postupujte podle obecného konceptuálního <xref:System.Windows.Input.InputManager> modelu "služby" a třídy služeb, jako jsou zodpovědné za vyvolání událostí.  
  
 Pokud však definujete vlastní připojenou událost založenou na modelu WPF, <xref:System.Windows.RoutedEvent>na které <xref:System.Windows.UIElement.RaiseEvent%2A> je založen připojených <xref:System.Windows.UIElement> událostí <xref:System.Windows.ContentElement>, můžete použít k navodění připojené události z libovolného nebo . Vyvolání směrované události (připojené nebo nepřipojené) vyžaduje, abyste deklarovali určitý prvek ve stromu prvků jako zdroj události; tento zdroj je <xref:System.Windows.UIElement.RaiseEvent%2A> hlášen jako volající. Určení prvku, který je vykázán jako zdroj ve stromu, je odpovědností vaší služby  
  
## <a name="see-also"></a>Viz také

- [Přehled směrovaných událostí](routed-events-overview.md)
- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
- [XAML a vlastní třídy pro WPF](xaml-and-custom-classes-for-wpf.md)
