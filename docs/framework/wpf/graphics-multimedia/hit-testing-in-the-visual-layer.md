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
ms.openlocfilehash: 28ae983923c985050ac589166023e483721028d3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452614"
---
# <a name="hit-testing-in-the-visual-layer"></a>Spuštění testování ve vizuální vrstvě
Toto téma poskytuje přehled funkcí testování přístupů poskytovaných vizuální vrstvou. Podpora testování přístupů umožňuje určit, zda hodnota geometrie nebo bodu spadá do vykresleného obsahu <xref:System.Windows.Media.Visual>, což umožňuje implementovat chování uživatelského rozhraní, jako je obdélník výběru pro výběr více objektů.  

<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>Scénáře testování přístupů  
 Třída <xref:System.Windows.UIElement> poskytuje metodu <xref:System.Windows.UIElement.InputHitTest%2A>, která umožňuje volání testu proti elementu pomocí dané hodnoty souřadnic. V mnoha případech <xref:System.Windows.UIElement.InputHitTest%2A> metoda poskytuje požadovanou funkci pro implementaci testování přístupů prvků. Existuje však několik scénářů, ve kterých může být nutné implementovat testování přístupů ve vizuální vrstvě.  
  
- Testování přístupů proti objektům, které nejsou<xref:System.Windows.UIElement>: to platí v případě, že jste dosáhli testování ne<xref:System.Windows.UIElement>ch objektů, jako jsou například objekty <xref:System.Windows.Media.DrawingVisual> nebo Graphics.  
  
- Testování přístupů pomocí geometrie: to platí v případě, že je nutné použít test pomocí objektu geometrie namísto hodnoty souřadnic bodu.  
  
- Testování přístupů u více objektů: to platí v případě, že je zapotřebí vyzkoušet test proti více objektům, jako jsou překrývající se objekty. Můžete získat výsledky pro všechny vizuály protínající geometrii nebo bod, nikoli jenom první z nich.  
  
- Ignorují se zásady testování přístupů <xref:System.Windows.UIElement>: to platí v případě, že potřebujete ignorovat zásady <xref:System.Windows.UIElement>ho testování přístupů, které berou v úvahu takové faktory, jako je to, jestli je element zakázaný nebo neviditelný.  
  
> [!NOTE]
> Kompletní vzorek kódu ilustrující testování přístupů ve vizuální vrstvě naleznete v tématu [test volání pomocí DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual) a [test volání s ukázkovou mezichodem v systému Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>Podpora testování přístupů  
 Účelem metod <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> ve třídě <xref:System.Windows.Media.VisualTreeHelper> je určit, zda je hodnota souřadnic nebo souřadnice bodu v rámci vykresleného obsahu daného objektu, například ovládacího prvku nebo grafického prvku. Například můžete použít testování volání k určení, zda kliknutí myší v ohraničujícím obdélníku objektu spadá do geometrie kružnice. Můžete také přepsat výchozí implementaci testování přístupů, abyste mohli provádět vlastní výpočty testů přístupů.  
  
 Následující ilustrace znázorňuje vztah mezi oblastí mimo obdélníkový objekt a jeho ohraničujícím obdélníkem.  
  
 ![Diagram platného regionu testu pozice](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagram platného regionu testu pozice  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>Testování přístupů a pořadí vykreslování  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vizuální vrstva podporuje testování přístupů proti všem objektům v bodě nebo geometrii, nikoli pouze k nejvyššímu objektu. Výsledky se vrátí v pořadí z. Ale vizuální objekt, který předáte jako parametr metodě <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>, určuje, která část vizuálního stromu bude dosaženo testu. Můžete vyzkoušet test proti celému vizuálnímu stromu nebo jakékoli jeho části.  
  
 Na následujícím obrázku je objekt kruhu na obou objektech čtverce i trojúhelníku. Pokud vás zajímá jenom testování přístupů, u vizuálního objektu, jehož hodnota z pořadí z je nejvyšší, můžete nastavit výčet testů vizuálního testu, který vrátí <xref:System.Windows.Media.HitTestResultBehavior.Stop> z <xref:System.Windows.Media.HitTestResultCallback>, aby se zastavil průchod testu přístupů po první položce.  
  
 ![Diagram pořadí z&#45;ve vizuálním stromu](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagram z-pořadí vizuálního stromu  
  
 Pokud chcete zobrazit výčet všech vizuálních objektů v určitém bodě nebo geometrii, vraťte <xref:System.Windows.Media.HitTestResultBehavior.Continue> z <xref:System.Windows.Media.HitTestResultCallback>. To znamená, že můžete vyzkoušet test pro vizuální objekty, které jsou pod jinými objekty, i když jsou zcela zakryté. Další informace najdete v ukázkovém kódu v části použití zpětného volání Výsledky testů.  
  
> [!NOTE]
> Je také možné, že je k dispozice vizuální objekt, který je transparentní.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Použití výchozího testování přístupů  
 Můžete určit, zda je bod v geometrii vizuálního objektu, pomocí metody <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> pro určení vizuálního objektu a hodnoty souřadnicového bodu pro testování. Parametr vizuálního objektu identifikuje výchozí bod ve vizuálním stromu pro hledání testu. Pokud je vizuální objekt nalezen ve vizuálním stromu, jehož geometrie obsahuje souřadnici, je nastavena na vlastnost <xref:System.Windows.Media.HitTestResult.VisualHit%2A> objektu <xref:System.Windows.Media.HitTestResult>. <xref:System.Windows.Media.HitTestResult> se pak vrátí z metody <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>. Pokud není bod součástí vizuálního podstromu, který jste provedli testováním, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> vrátí `null`.  
  
> [!NOTE]
> Výchozí testování přístupů vždy vrátí objekt nejvyšší úrovně v pořadí vykreslování. Pro identifikaci všech vizuálních objektů, i těch, které mohou být částečně nebo zcela zakryty, použijte zpětné volání výsledku testu volání.  
  
 Hodnota souřadnice, kterou předáte jako parametr Point pro metodu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>, musí být relativní vzhledem k prostoru souřadnic objektu vizuálu, u kterého jste provedli testování. Například pokud máte vnořené vizuální objekty definované na (100, 100) v prostoru souřadnic nadřazeného objektu, potom je možné otestovat podřízený vizuál na pozici (0, 0) v souřadnicovém prostoru nadřazeného objektu (100, 100).  
  
 Následující kód ukazuje, jak nastavit obslužné rutiny událostí myši pro objekt <xref:System.Windows.UIElement>, který slouží k zachycení událostí používaných pro testování přístupů.  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Vliv vizuálního stromu na testování přístupů  
 Výchozí bod ve vizuálním stromu určuje, které objekty jsou vraceny během výčtu testů přístupů objektů. Pokud máte více objektů, které chcete vyzkoušet, musí být vizuální objekt použitý jako výchozí bod ve vizuálním stromu společným nadřazeným prvkem všech objektů, které vás zajímají. Pokud jste například zaznamenali, že se má v následujícím diagramu testovat, jak element Button, tak vykreslování vizuálu, je nutné nastavit výchozí bod ve vizuálním stromu na společný nadřazený prvek obou. V tomto případě je element plátno společným nadřazeným prvkem elementu Button a vykreslováním vizuálu.  
  
 ![Diagram hierarchie vizuálního stromu](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagram hierarchie vizuálního stromu  
  
> [!NOTE]
> Vlastnost <xref:System.Windows.UIElement.IsHitTestVisible%2A> získává nebo nastavuje hodnotu, která deklaruje, zda může být objekt odvozený <xref:System.Windows.UIElement>vrácen jako výsledek testu volání z některé části vykresleného obsahu. To umožňuje selektivní změnu vizuálního stromu, aby bylo možné určit, které vizuální objekty jsou součástí testu volání.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Použití zpětného volání výsledků testu volání  
 Můžete vytvořit výčet všech vizuálních objektů ve vizuálním stromu, kde geometrie obsahuje zadanou hodnotu souřadnic. To vám umožňuje identifikovat všechny vizuální objekty, i ty, které mohou být částečně nebo zcela zakryty jinými vizuálními objekty. Chcete-li zobrazit výčet vizuálních objektů ve vizuálním stromu, použijte metodu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> s funkcí zpětného volání testu přístupů. Funkce zpětného volání testu volání je volána systémem, pokud je hodnota souřadnic, kterou zadáte, obsažena ve vizuálním objektu.  
  
 Během výčtu výsledků testů přístupů byste neměli provádět žádné operace, které upraví vizuální strom. Přidání nebo odebrání objektu ve vizuálním stromu během procházení může způsobit nepředvídatelné chování. Až se metoda <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> vrátí, můžete vizuální strom bezpečně upravit. Můžete chtít poskytnout datovou strukturu, například <xref:System.Collections.ArrayList>, k ukládání hodnot během výčtu výsledků testů přístupů.  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 Metoda zpětného volání testu volání definuje akce, které provedete při identifikaci testu volání u určitého vizuálního objektu ve vizuálním stromu. Po provedení těchto akcí vrátíte <xref:System.Windows.Media.HitTestResultBehavior> hodnotu, která určuje, jestli se má pokračovat ve výčtu všech ostatních vizuálních objektů, nebo ne.  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> Pořadí výčtu vizuálních objektů přístupů je podle pořadí z. Vizuální objekt na nejvyšší úrovni pořadí z je prvním objektem výčtu. Všechny ostatní vizuální objekty, které jsou ve výčtu, jsou zmenšeny na úrovni z. Toto pořadí výčtu odpovídá pořadí vykreslování vizuálů.  
  
 Výčty vizuálních objektů můžete kdykoli zastavit ve funkci zpětného volání testu volání vrácením <xref:System.Windows.Media.HitTestResultBehavior.Stop>.  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Použití zpětného volání filtru testu volání  
 Pomocí volitelného filtru testu přístupů můžete omezit objekty, které jsou předány do výsledků testu přístupů. To vám umožní ignorovat části vizuálního stromu, které nebudete zajímat o zpracování ve výsledcích testů přístupů. Chcete-li implementovat filtr testů přístupů, definujte funkci zpětného volání filtru testu a předejte ji jako hodnotu parametru při volání metody <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>.  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Pokud nechcete dodávat volitelnou funkci zpětného volání filtru testu, předejte `null` hodnotu jako parametr pro metodu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>.  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Vyřazení vizuálního stromu pomocí filtru testů přístupů](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Vyřazení vizuálního stromu  
  
 Funkce zpětného volání filtru testu umožňuje vytvořit výčet pomocí všech vizuálů, jejichž vykreslený obsah obsahuje souřadnice, které zadáte. Můžete ale chtít ignorovat určité větve vizuálního stromu, které nebudete mít na zpracování ve funkci zpětného volání výsledků testů přístupů. Návratová hodnota funkce zpětného volání filtru testu je určena pro typ akce, které by měly vybírat výčty vizuálních objektů. Například pokud vrátíte hodnotu, <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, můžete odebrat aktuální vizuální objekt a jeho podřízené položky z výčtu výsledků testů přístupů. To znamená, že funkce zpětného volání výsledků testu volání nebudou tyto objekty ve svém výčtu zobrazovat. Vyřazení vizuálního stromu objektů snižuje množství zpracování během průchodu výčtu výsledků testů přístupů. V následujícím příkladu kódu filtr přeskočí popisky a jejich následníky a zavoláním všech ostatních.  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> V případech, kdy zpětné volání výsledků testu volání není voláno, bude v některých případech voláno zpětné volání filtru testu přístupů.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Přepsání výchozího testování přístupů  
 Můžete přepsat výchozí podporu testování přístupů vizuálního objektu přepsáním metody <xref:System.Windows.Media.Visual.HitTestCore%2A>. To znamená, že při vyvolání metody <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> se zavolá přepsaná implementace <xref:System.Windows.Media.Visual.HitTestCore%2A>. Přepsaná metoda je volána, když test volání spadá do ohraničujícího obdélníku vizuálního objektu, a to i v případě, že souřadnice spadá mimo vykreslený obsah vizuálního objektu.  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Můžou nastat situace, kdy budete chtít vyzkoušet test proti ohraničujícímu obdélníku i vykreslenému obsahu vizuálního objektu. Použitím hodnoty parametru `PointHitTestParameters` v přepsané <xref:System.Windows.Media.Visual.HitTestCore%2A> metodě jako parametru pro <xref:System.Windows.Media.Visual.HitTestCore%2A>základní metody můžete provádět akce na základě přístupů ohraničujícího obdélníku vizuálního objektu a poté provést druhý test volání proti vykreslenému obsahu vizuálního objektu.  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [Test volání pomocí DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)
- [Test volání s ukázkovou meziprovozu Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [Ověření pozice objektu Geometry ve vizuálním objektu](how-to-hit-test-geometry-in-a-visual.md)
- [Ověřování pozice pomocí kontejneru hostitele Win32](how-to-hit-test-using-a-win32-host-container.md)
