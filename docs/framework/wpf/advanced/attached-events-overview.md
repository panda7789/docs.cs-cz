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
ms.openlocfilehash: ae6d426d671c8bf034ebd86e768352914585d969
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541736"
---
# <a name="attached-events-overview"></a>Přehled připojených událostí
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Definuje součást jazyk a typ události volána *přidružená událost*. Koncept přidružená událost umožňuje přidat obslužnou rutinu události pro libovolný element místo na element, který ve skutečnosti definuje nebo dědí události. V takovém případě ani objekt potenciálně vyvolá událost ani cílový zpracování instance definuje nebo jinak "vlastní" události.  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že jste četli [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md) a [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Syntaxe přidružená událost  
 Máte přidružené události [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe a kódování vzor, který se musí použít kód zálohování za účelem podpory využití přidružená událost.  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxi, která je přidružená událost zadán nejen její název události, ale typ vlastnícím plus název události, oddělené tečkou (.). Vzhledem k tomu, že název události je kvalifikovaný pomocí názvu jeho vlastnícím typu, umožňuje syntaxe přidružená událost připojené události, které chcete připojit k libovolný element, který se dá vytvořit instance.  
  
 Například následující je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe pro obslužnou rutinu pro vlastní připojení `NeedsCleaning` přidružená událost:  
  
 [!code-xaml[WPFAquariumSln#AE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Poznámka: `aqua:` předpony; předponu je nutné v tomto případě protože vlastní událost, která pochází z vlastní namapované xmlns je přidružená událost.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Jak WPF implementuje přidružené události  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], připojené události jsou zajišťované <xref:System.Windows.RoutedEvent> pole a směrování v stromu po jsou vyvolány. Obvykle zdroj přidružená událost (objekt, který vyvolává událost) je zdroj systému nebo služby a objekt, který spouští kód, který vyvolá událost, není proto přímé součástí stromu elementu.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Scénáře pro přidružené události  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], připojené události se nacházejí v určité oblasti funkcí níž se nachází abstrakce úrovni služby, například pro události povoleno statickou <xref:System.Windows.Input.Mouse> – třída nebo <xref:System.Windows.Controls.Validation> třídy. Třídy, které interakci s nebo používat službu můžete buď použít událost v syntaxi přidružená událost, nebo můžete zvolit prezentovat přidružená událost jako směrované události, který je součástí jak třída umožňuje integraci funkcí služby.  
  
 I když [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definuje počet přidružené události, scénáře, kde bude použití nebo obslužná rutina přidružená událost přímo jsou hodně omezené. Obecně platí, přidružená událost slouží účelu architekturu, ale je předán nepřipojené (zálohovaný s [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událostí "obálky") směrované události.  
  
 Například základní přidružená událost <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> může více snadno zpracovat všechny zadané <xref:System.Windows.UIElement> pomocí <xref:System.Windows.UIElement.MouseDown> na který <xref:System.Windows.UIElement> místo týkajících se syntaxí přidružená událost buď v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kódu. – Přidružená událost slouží účelu v architektuře, protože umožňuje pro budoucí rozšíření vstupní zařízení. Hypotetický zařízení potřebovat pouze ke zvýšení <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> v pořadí k simulaci vstup z myši a nebude potřeba k odvozování z <xref:System.Windows.Input.Mouse> Uděláte to tak. Však tento scénář zahrnuje kód zpracování události, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zpracování přidružená událost se nevztahuje na tomto scénáři.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Zpracování přidružená událost v grafickém subsystému WPF  
 Proces pro zpracování přidružená událost a kód obslužné rutiny, která budete psát, je v podstatě stejný jako u směrované události.  
  
 Obecně platí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přidružená událost není příliš neliší od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] směrované události. Rozdíly jsou jak událost pochází a jak je zveřejněný prostřednictvím třídy jako člena (která ovlivní také [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe obslužné rutiny).  
  
 Však jako si předtím poznamenali, existující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přidružené události nejsou určené hlavně pro zpracování v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Účelem události častěji, je umožnit kompletní složený element k hlášení stavu na nadřazený element v skládání, ve kterém se obvykle vyvolá v kódu případ události a také závisí na třídu zpracování v příslušné nadřazené třídy. Pro instanci položky v rámci <xref:System.Windows.Controls.Primitives.Selector> očekává se, že vyvolat připojený <xref:System.Windows.Controls.Primitives.Selector.Selected> zpracovává událost, která je pak třída <xref:System.Windows.Controls.Primitives.Selector> třídy a pak pomocí potenciálně převedeny <xref:System.Windows.Controls.Primitives.Selector> třída do různých směrované události <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Další informace o směrované události a třída zpracování najdete v tématu [označení směrované události jako Handled a třída zpracování](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definování vlastní přidružené události jako směrované události  
 Pokud jsou odvozování z běžné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] základní třídy, včetně některých vzor metody ve třídě můžete implementovat vlastní přidružené události a pomocí nástroje metody, které jsou již k dispozici základní třídy.  
  
 Vzor vypadá takto:  
  
-   Metoda `Add*Handler` s dva parametry. První parametr musí identifikovat událost a identifikovaných událostí se musí shodovat s názvy * v název metody. Druhý parametr je obslužná rutina přidat. Metoda musí být veřejné a statické s žádnou návratovou hodnotu.  
  
-   Metoda `Remove*Handler` s dva parametry. První parametr musí identifikovat událost a identifikovaných událostí se musí shodovat s názvy * v název metody. Druhý parametr je obslužná rutina odebrat. Metoda musí být veřejné a statické s žádnou návratovou hodnotu.  
  
 `Add*Handler` Usnadňuje metoda přistupujícího objektu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] při zpracování připojené obslužné rutiny události, které atributy jsou deklarované v elementu. `Add*Handler` a `Remove*Handler` metody zároveň povolit kódu přístup k úložišti obslužné rutiny události pro přidružená událost.  
  
 Tento vzor obecné ještě není dostatečně přesné pro praktické implementace v rozhraní, protože všechny zadané [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] čtečky implementace může mít různé schémata pro identifikaci základní události v podpůrné jazyk a architektura. Toto je jedna z důvodů, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události implementuje připojené jako směrované události; identifikátor pro událost (<xref:System.Windows.RoutedEvent>) je již definován [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostí systému. Směrování událost je také přirozené implementaci rozšíření na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] úroveň jazyka konceptu přidružená událost.  
  
 `Add*Handler` Implementace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přidružená událost se skládá z volání <xref:System.Windows.UIElement.AddHandler%2A> s směrované události a obslužné rutiny jako argumenty.  
  
 Tato strategie implementace a směrované události systému obecně omezit zpracování pro přidružené události buď <xref:System.Windows.UIElement> odvozených tříd nebo <xref:System.Windows.ContentElement> odvozených tříd, protože jenom ty třídy mají <xref:System.Windows.UIElement.AddHandler%2A> implementace.  
  
 Například následující kód definuje `NeedsCleaning` přidružená událost k třídě vlastníka `Aquarium`pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] připojené události strategie deklarace přidružená událost jako směrované události.  
  
 [!code-csharp[WPFAquariumSln#AECode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Všimněte si, že metoda používá k navázání pole identifikátor přidružená událost <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>, je ve skutečnosti stejnou metodu, která se použije k registraci nepřipojené směrované události. Přidružené události a směrované události všechny jsou registrovány k centralizované interní úložiště. Tato implementace událostí úložiště umožňuje "událostí jako rozhraní" koncepční úvahy, že je podrobněji [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Vyvolání WPF přidružená událost  
 Není nutné obvykle vygeneroval existující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definované přidružené události z vašeho kódu. Tyto události postupujte podle obecných "služba" konceptuálního modelu a třídy služeb, jako <xref:System.Windows.Input.InputManager> jsou zodpovědní za vyvolání události.  
  
 Ale pokud definujete vlastní přidružená událost na základě [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] model založenou na přidružené události <xref:System.Windows.RoutedEvent>, můžete použít <xref:System.Windows.UIElement.RaiseEvent%2A> pro vyvolání připojené události z libovolného <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement>. Vyvolání směrované události (připojený, nebo ne) vyžaduje, že deklarujete určitý element ve stromové struktuře element jako zdroj událostí; Tento zdroj se hlásí jako <xref:System.Windows.UIElement.RaiseEvent%2A> volajícího. Určení, který element hlášení jako zdroj ve stromu je vaše služba odpovědnosti  
  
## <a name="see-also"></a>Viz také  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Podrobná syntaxe XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [XAML a vlastní třídy pro WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
