---
title: Spuštění testování ve vizuální vrstvě
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit testing functionality [WPF]
- visual layer [WPF], hit testing functionality
ms.assetid: b1a64b61-14be-4d75-b89a-5c67bebb2c7b
ms.openlocfilehash: d4d304353e91147c57297dcc4525759ff1474b4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186407"
---
# <a name="hit-testing-in-the-visual-layer"></a>Spuštění testování ve vizuální vrstvě
Toto téma obsahuje přehled funkcí testování přístupů poskytovaných vizuální vrstvou. Podpora testování přístupů umožňuje určit, zda geometrie nebo bodová <xref:System.Windows.Media.Visual>hodnota spadá do vykresleného obsahu , což umožňuje implementovat chování uživatelského rozhraní, jako je například obdélník výběru pro výběr více objektů.  

<a name="hit_testing_scenarios"></a>
## <a name="hit-testing-scenarios"></a>Scénáře testování přístupů  
 Třída <xref:System.Windows.UIElement> poskytuje <xref:System.Windows.UIElement.InputHitTest%2A> metodu, která umožňuje přístupů test proti prvek pomocí dané hodnoty souřadnice. V mnoha případech <xref:System.Windows.UIElement.InputHitTest%2A> metoda poskytuje požadované funkce pro implementaci testování přístupů prvků. Existuje však několik scénářů, ve kterých budete muset implementovat testování přístupů ve vizuální vrstvě.  
  
- Přístupové položky<xref:System.Windows.UIElement> testování proti non-objekty: To<xref:System.Windows.UIElement> platí, <xref:System.Windows.Media.DrawingVisual> pokud jsou přístupů testování non-objekty, jako jsou nebo grafické objekty.  
  
- Testování přístupů pomocí geometrie: To platí, pokud potřebujete zasáhnout test pomocí objektu geometrie, nikoli souřadnicovou hodnotou bodu.  
  
- Přístupové položky testování proti více objektů: To platí, když potřebujete přístupů test proti více objektů, jako jsou překrývající se objekty. Můžete získat výsledky pro všechny vizuály protínající geometrii nebo bod, ne jen pro první.  
  
- Ignorování <xref:System.Windows.UIElement> zásady testování přístupů: To platí, když potřebujete ignorovat zásady testování přístupů, <xref:System.Windows.UIElement> které bere v úvahu takové faktory, jako je, zda je prvek zakázán nebo neviditelný.  
  
> [!NOTE]
> Kompletní ukázka kódu ilustrující testování přístupů ve vizuální vrstvě naleznete v [tématu Hit Test Using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual) and [Hit Test with Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).  
  
<a name="hit_testing_support"></a>
## <a name="hit-testing-support"></a>Podpora testování přístupů  
 Účelem <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metod ve <xref:System.Windows.Media.VisualTreeHelper> třídě je určit, zda geometrie nebo bod souřadnice hodnota je v rámci vykreslení obsahu daného objektu, jako je například ovládací prvek nebo grafický prvek. Můžete například použít testování přístupů k určení, zda klepnutí myší v ohraničujícím obdélníku objektu spadá do geometrie kruhu. Můžete také přepsat výchozí implementaci testování přístupů k provedení vlastních výpočtů testu přístupů.  
  
 Následující obrázek znázorňuje vztah mezi oblastí neobdélníkového objektu a jeho ohraničujícím obdélníkem.  
  
 ![Diagram platné oblasti testu přístupů](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagram platné oblasti testu přístupů  
  
<a name="hit_testing_and_z-order"></a>
## <a name="hit-testing-and-z-order"></a>Testování přístupů a pořadí vykreslující  
 Vizuální [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vrstva podporuje testování přístupů proti všem objektům pod bodem nebo geometrií, nejen proti objektu zcela nahoře. Výsledky jsou vráceny v pořadí vykreslášti. Vizuální objekt, který předáte jako parametr <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodě, však určuje, která část vizuálního stromu, která bude testována přístupem. Můžete zasáhnout test proti celý vizuální strom, nebo jeho část.  
  
 Na následujícím obrázku je objekt kruhu nad čtvercovými i trojúhelníkovými objekty. Pokud vás zajímá pouze testování přístupů vizuální objekt, jehož hodnota pořadí vykreslování <xref:System.Windows.Media.HitTestResultBehavior.Stop> je <xref:System.Windows.Media.HitTestResultCallback> nejvyšší, můžete nastavit výčet testu vizuální hohodu, aby se vrátil z testu přístupů po první položce.  
  
 ![Diagram pořadí z&#45;vizuálního stromu](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagram pořadí vykreslujícího vizuálního stromu  
  
 Pokud chcete vytvořit výčet všech vizuálních objektů pod určitým <xref:System.Windows.Media.HitTestResultBehavior.Continue> bodem <xref:System.Windows.Media.HitTestResultCallback>nebo geometrií, vraťte se z . To znamená, že můžete zasáhnout test pro vizuální objekty, které jsou pod jinými objekty, i když jsou zcela zakryté. Další informace naleznete v ukázkovém kódu v části "Použití zpětného volání výsledků testu přístupů".  
  
> [!NOTE]
> Vizuální objekt, který je transparentní lze také přístupů test.  
  
<a name="using_default_hit_testing"></a>
## <a name="using-default-hit-testing"></a>Použití výchozího testování přístupů  
 Můžete určit, zda je bod v geometrii vizuálního <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> objektu, pomocí metody k určení vizuálního objektu a hodnoty souřadnic bodu, proti které se má testovat. Parametr vizuálního objektu identifikuje počáteční bod ve vizuálním stromu pro hledání testu přístupů. Pokud je vizuální objekt nalezen ve vizuálním stromu, jehož <xref:System.Windows.Media.HitTestResult.VisualHit%2A> geometrie <xref:System.Windows.Media.HitTestResult> obsahuje souřadnice, je nastaven na vlastnost objektu. Potom <xref:System.Windows.Media.HitTestResult> je vrácena <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> z metody. Pokud bod není obsažen s vizuální podstrom, který <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> jsou `null`hit testování, vrátí .  
  
> [!NOTE]
> Výchozí testování přístupů vždy vrátí nejvyšší objekt v pořadí vykreslující. Chcete-li identifikovat všechny vizuální objekty, i ty, které mohou být částečně nebo zcela zakryté, použijte zpětné volání výsledků testu přístupů.  
  
 Hodnota souřadnic, kterou předáte jako parametr bodu pro metodu, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> musí být relativní vzhledem k souřadnicovému prostoru vizuálního objektu, proti kterém jste narazili na testování. Například pokud jste vnořené vizuální objekty definované na (100, 100) v nadřazené souřadnicové prostoru, pak přístupů testování podřízené vizuál na (0, 0) je ekvivalentní testování přístupů na (100, 100) v nadřazené souřadnicové prostoru.  
  
 Následující kód ukazuje, jak nastavit obslužné rutiny událostí myši pro <xref:System.Windows.UIElement> objekt, který se používá k zachycení událostí používaných pro testování přístupů.  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Jak vizuální strom ovlivňuje testování přístupů  
 Počáteční bod ve vizuálním stromu určuje, které objekty jsou vráceny během výčtu test přístupů objektů. Pokud máte více objektů, které chcete zasáhnout test, vizuální objekt použitý jako výchozí bod ve vizuálním stromu musí být společným předchůdcem všech objektů, které vás zajímají. Například pokud jste měli zájem o testování jak prvek tlačítka a kreslení vizuál v následujícím diagramu, budete muset nastavit počáteční bod ve vizuálním stromu společného předchůdce obou. V tomto případě je prvek plátna společným předchůdcem prvku tlačítka i vizuálu výkresu.  
  
 ![Diagram hierarchie vizuálního stromu](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagram hierarchie vizuálního stromu  
  
> [!NOTE]
> Vlastnost <xref:System.Windows.UIElement.IsHitTestVisible%2A> získá nebo nastaví hodnotu, <xref:System.Windows.UIElement>která deklaruje, zda odvozený objekt může být případně vrácena jako výsledek testu přístupů z některé části jeho vykresleného obsahu. To umožňuje selektivně změnit vizuální strom k určení, které vizuální objekty jsou zapojeny do testu přístupů.  
  
<a name="using_a_hit_test_result_callback"></a>
## <a name="using-a-hit-test-result-callback"></a>Použití zpětného volání výsledku testu přístupů  
 Můžete vytvořit výčet všech vizuálních objektů ve vizuálním stromu, jehož geometrie obsahuje zadanou hodnotu souřadnic. To umožňuje identifikovat všechny vizuální objekty, i ty, které mohou být částečně nebo zcela zakryty jinými vizuálními objekty. Chcete-li vytvořit výčet vizuálníobjekty <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> ve vizuálním stromu, použijte metodu s funkcí zpětného volání testu přístupů. Funkce zpětného volání testu přístupů je volána systémem, pokud je zadaná hodnota souřadnic obsažena ve vizuálním objektu.  
  
 Během výčtu výsledků testu přístupů byste neměli provádět žádné operace, které upravuje vizuální strom. Přidání nebo odebrání objektu z vizuálního stromu během jeho procházení může mít za následek nepředvídatelné chování. Po vrácení <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody můžete bezpečně upravit vizuální strom. Můžete chtít poskytnout strukturu dat, jako <xref:System.Collections.ArrayList>je například , pro uložení hodnot během výčtu výsledků testu přístupů.  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 Metoda zpětného volání testu přístupů definuje akce, které provedete, když je test přístupů identifikován na konkrétním vizuálním objektu ve vizuálním stromu. Po provedení akcí vrátíte <xref:System.Windows.Media.HitTestResultBehavior> hodnotu, která určuje, zda chcete pokračovat ve výčtu jiných vizuálních objektů nebo ne.  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> Pořadí výčtu přístupů vizuální objekty je pořadí vykreslování. Vizuální objekt na nejvyšší úrovni pořadí vykreslovaného objektu je první objekt ve výčtu. Všechny ostatní vizuální objekty ve výčtu jsou na úrovni snížení pořadí vykreslovaných. Toto pořadí výčtu odpovídá pořadí vykreslování vizuálů.  
  
 Výčet vizuálních objektů můžete kdykoli zastavit ve funkci zpětného volání <xref:System.Windows.Media.HitTestResultBehavior.Stop>testu přístupů vrácením .  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>
## <a name="using-a-hit-test-filter-callback"></a>Použití zpětného volání filtru testu přístupů  
 Můžete použít volitelný filtr testu přístupů k omezení objektů, které jsou předány výsledky testu přístupů. To umožňuje ignorovat části vizuálního stromu, které nemáte zájem o zpracování ve výsledcích testu přístupů. Chcete-li implementovat filtr testu přístupů, definujte funkci zpětného volání filtru <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> testu přístupů a předejte ji jako hodnotu parametru při volání metody.  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Pokud nechcete zadat volitelnou funkci zpětného volání filtru `null` testu přístupů, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> předejte hodnotu jako parametr pro metodu.  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Prořezávání vizuálního stromu pomocí testovacího filtru přístupů](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Prořezávání vizuálního stromu  
  
 Funkce zpětného volání filtru testu přístupů umožňuje vytvořit výčet všech vizuálů, jejichž vykreslený obsah obsahuje zadané souřadnice. Můžete však chtít ignorovat určité větve vizuálního stromu, které nemáte zájem o zpracování ve funkci zpětného volání výsledků testu přístupů. Vrácená hodnota funkce zpětného volání filtru testu přístupů určuje, jaký typ akce by měl výčet vizuálních objektů provést. Například pokud vrátíte hodnotu , <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>můžete odebrat aktuální vizuální objekt a jeho podřízené objekty z výčtu výsledků testu přístupů. To znamená, že funkce zpětného volání výsledků testu přístupů neuvidí tyto objekty ve svém výčtu. Prořezávání vizuální strom objektů snižuje množství zpracování během průchodu výsledků testu přístupů. V následujícím příkladu kódu filtr přeskočí popisky a jejich potomky a přístupů testuje vše ostatní.  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> Návrat filtru test přístupů bude někdy volána v případech, kdy není volána zpětná volání výsledků testu přístupů.  
  
<a name="overriding_default_hit_testing"></a>
## <a name="overriding-default-hit-testing"></a>Přepsání výchozího testování přístupů  
 Výchozí podporu testování přístupů vizuálního objektu můžete <xref:System.Windows.Media.Visual.HitTestCore%2A> přepsat přepsáním metody. To znamená, že <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> při vyvolání metody <xref:System.Windows.Media.Visual.HitTestCore%2A> je volána vaše přepsané implementace. Přepnutá metoda je volána, když test přístupů spadá do ohraničovacího obdélníku vizuálního objektu, i když souřadnice spadá mimo vykreslený obsah vizuálního objektu.  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Může nastat někdy, kdy chcete přístupů test proti ohraničující obdélník a vykreslený obsah vizuální objekt. Pomocí hodnoty `PointHitTestParameters` parametru v <xref:System.Windows.Media.Visual.HitTestCore%2A> přepsané metodě jako <xref:System.Windows.Media.Visual.HitTestCore%2A>parametr u základní metody můžete provádět akce na základě přístupu ohraničujícího obdélníku vizuálního objektu a potom provést druhý test přístupů proti vykreslení obsahu vizuálního objektu.  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [Test přístupů pomocí ukázky výkresových obrazovek](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)
- [Test přístupů s ukázkou spolupráce win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [Spuštění geometrie testu ve vizuálním objektu](how-to-hit-test-geometry-in-a-visual.md)
- [Ověřování pozice pomocí kontejneru hostitele Win32](how-to-hit-test-using-a-win32-host-container.md)
