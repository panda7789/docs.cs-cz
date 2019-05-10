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
ms.openlocfilehash: 2b3f659a5916aa63d510959583e8ae038085460c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655493"
---
# <a name="attached-events-overview"></a>Přehled připojených událostí
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Definuje komponentu jazyka a typu události, volá se, *přidružená událost*. Koncept přidružená událost umožňuje přidání obslužné rutiny při určité události libovolný prvek, nikoli element, který ve skutečnosti definuje nebo dědí události. V takovém případě objekt potenciálně vyvolání události ani cílové zpracování instance definuje nebo jinak "vlastní" události.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že jste četli [směrovat Přehled událostí](routed-events-overview.md) a [přehled XAML (WPF)](xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Syntaxe přidružená událost  
 Připojené události mají [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe a vzor kódování, kterou musí používat záložní kód za účelem podpory využití přidružená událost.  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe, přidružená událost je zadán nejen podle názvu události, ale podle jeho vlastnící typ a název události, oddělené tečkou (.). Protože název události je kvalifikován s názvem jeho vlastnícího typu, přidružená událost syntaxe umožňuje připojené události, které chcete připojit k libovolnému prvku, který se dá vytvořit instance.  
  
 Například tady je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe obslužné rutiny pro vlastní připojení `NeedsCleaning` – přidružená událost:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Poznámka: `aqua:` předpony; předpona, která je nezbytné v tomto případě protože přidružená událost je vlastní událost, která pochází z vlastní atribut xmlns pro mapovanou.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Jak WPF implementuje připojených událostí  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], připojených událostí je zajištěná <xref:System.Windows.RoutedEvent> pole a jsou směrovány prostřednictvím stromu, jakmile jsou generovány. Obvykle zdroj připojené události (objekt, který vyvolává událost) je zdrojem systému nebo službě, a objekt, který spouští kód, který vyvolává událost není proto s přímým přístupem součástí stromem prvků.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Scénáře pro připojené události  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], připojené události jsou k dispozici v určité oblasti funkcí níž se nachází úrovní abstrakce, jako například pro události ve statické povolené <xref:System.Windows.Input.Mouse> třídy nebo <xref:System.Windows.Controls.Validation> třídy. Třídy, které pracovat, nebo použít službu můžete buď použít událost v syntaxi přidružená událost, nebo můžete vybrat k poskytování připojených událostí jako směrovaných událostí, který je součástí jak třídu integruje možnosti služby.  
  
 I když [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definuje počet připojených událostí, scénáře, kde se používá nebo popisovač přidružená událost přímo jsou velmi omezená. Obecně platí, přidružená událost slouží účelu architekturu, ale pak předá nepřipojené (zajištěnou [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události "zabezpečenou obálku") směrované události.  
  
 Například základní přidružená událost <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> informace snadno půjde na každá <xref:System.Windows.UIElement> pomocí <xref:System.Windows.UIElement.MouseDown> zabývat <xref:System.Windows.UIElement> místo zabývajících se syntaxí přidružená událost buď v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kódu. Přidružená událost slouží účelu v architektuře, protože to umožňuje používat pro budoucí rozšíření vstupní zařízení. Hypotetický zařízení by stačí vyvolat <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> v pořadí pro simulaci vstup z myši a nebude potřeba k odvození z <xref:System.Windows.Input.Mouse> Uděláte to tak. Ale tento scénář zahrnuje kód zpracování události, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zpracování připojených událostí není relevantní pro tento scénář.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Zpracování připojených událostí v subsystému WPF  
 Proces pro zpracování připojených událostí a kód pro obslužnou rutinu, která bude zapisovat, je v podstatě stejný jako u směrované události.  
  
 Obecně platí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přidružená událost není příliš neliší od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] směrované události. Rozdíly jsou jak zdroj události a jeho zveřejnění třídou jako člen (který má vliv také [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe obslužné rutiny).  
  
 Nicméně, jako jste si předtím poznamenali, existující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] připojené události nejsou určené především pro zpracování v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Účelem události je častěji, povolte složené element hlášení stavu na nadřazený element v skládání, ve kterém případ události se obvykle vyvolá v kódu a také závisí na zpracování ve třídě příslušné nadřazené třídy. Pro instanci položky v rámci <xref:System.Windows.Controls.Primitives.Selector> očekává se zvýšení připojeného <xref:System.Windows.Controls.Primitives.Selector.Selected> událost, což je třída pak zpracovány <xref:System.Windows.Controls.Primitives.Selector> třídy a potenciálně převést pomocí <xref:System.Windows.Controls.Primitives.Selector> třídy do různých směrované události <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Další informace o směrované události a zpracování tříd naleznete v tématu [označení směrované události jako Handled a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definování připojených událostí jako směrovaných událostí  
 Pokud je odvozený od společného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] základní třídy, můžete implementovat vlastní připojené události zahrnutím určité vzor metody ve třídě a pomocí nástroje pro metody, které jsou už k dispozici na základní třídy.  
  
 Vzor je následujícím způsobem:  
  
- Metoda **přidat*EventName*obslužná rutina** se dvěma parametry. První parametr je instance, do kterého se přidá obslužnou rutinu události. Druhý parametr je obslužná rutina události pro přidání. Metoda musí být `public` a `static`, s žádnou návratovou hodnotu.  
  
- Metoda **odebrat*EventName*obslužná rutina** se dvěma parametry. První parametr je instance, ze kterého se odebere obslužnou rutinu události. Druhý parametr je obslužná rutina události k odebrání. Metoda musí být `public` a `static`, s žádnou návratovou hodnotu.  
  
 **Přidat*EventName*obslužná rutina** usnadňuje přístupové metody [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] při zpracování připojené obslužná rutina události, které atributy jsou deklarovány v elementu. **Přidat*EventName*obslužná rutina** a **odebrat*EventName*obslužné rutiny** metody také umožňují přístup ke kódu do úložiště obslužné rutiny události připojené události.  
  
 Toto je obecný vzor ještě není dostatečně přesný praktické implementace v rámci, protože každá [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] čtečky implementace může být různá schémata pro určení základní události v podpůrných jazyka a architektury. Toto je jedním z důvodů, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementuje připojených událostí jako směrovaných událostí; identifikátor pro událost (<xref:System.Windows.RoutedEvent>) je již definován [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém událostí. Směrování událostí je také rozšíření fyzická implementace na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] úrovni jazyka konceptu přidružená událost.  
  
 **Přidat*EventName*obslužná rutina** implementace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přidružená událost se skládá z volání funkce <xref:System.Windows.UIElement.AddHandler%2A> směrované události a obslužné rutiny jako argumenty.  
  
 Tato strategie implementace a směrované události systému obecně omezení zpracování pro připojené události buď <xref:System.Windows.UIElement> odvozené třídy nebo <xref:System.Windows.ContentElement> odvozené třídy, protože pouze tyto třídy mají <xref:System.Windows.UIElement.AddHandler%2A> implementace.  
  
 Například následující kód definuje `NeedsCleaning` přidružená událost ve třídě vlastníka `Aquarium`, použije [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] připojené události strategie deklarování připojených událostí jako směrovaných událostí.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Všimněte si, že metoda používá k navázání identifikátor pole přidružená událost <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>, ve skutečnosti stejnou metodu, která se použije k registraci nepřipojené směrované události. Připojené události a směrované události všech zaregistrováni do centralizované interní úložiště. Tato implementace úložiště událostí umožňuje "události jako rozhraní" koncepční úvahy, že je podrobněji popsána [směrovat Přehled událostí](routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Vyvolání WPF – přidružená událost  
 Obvykle nepotřebujete pro vyvolání existující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definované připojené události z vašeho kódu. Tyto události použijte obecné koncepční model "služba" a třídy služeb, jako <xref:System.Windows.Input.InputManager> zodpovídají za vyvolání události.  
  
 Nicméně pokud definujete vlastní přidružená událost na základě [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelu odvození připojených událostí na <xref:System.Windows.RoutedEvent>, můžete použít <xref:System.Windows.UIElement.RaiseEvent%2A> k vyvolání připojené události z libovolného <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement>. Vyvolání směrovaných událostí (připojené, nebo ne) vyžaduje deklaraci konkrétní element ve stromové struktuře prvek jako zdroj události; Tento zdroj se hlásí jako <xref:System.Windows.UIElement.RaiseEvent%2A> volajícího. Určení, které elementy se ohlásí jako zdroj ve stromové struktuře odpovídá vaší služby  
  
## <a name="see-also"></a>Viz také:

- [Přehled směrovaných událostí](routed-events-overview.md)
- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
- [XAML a vlastní třídy pro WPF](xaml-and-custom-classes-for-wpf.md)
