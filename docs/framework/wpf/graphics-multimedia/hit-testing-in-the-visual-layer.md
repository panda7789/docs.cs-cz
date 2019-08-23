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
ms.openlocfilehash: 92b7e8ffab001af4dba6c571fd06c64f2865b1e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962124"
---
# <a name="hit-testing-in-the-visual-layer"></a>Spuštění testování ve vizuální vrstvě
Toto téma poskytuje přehled funkcí testování přístupů poskytovaných vizuální vrstvou. Podpora testování přístupů umožňuje určit, zda hodnota geometrie nebo bodu spadá do vykresleného obsahu <xref:System.Windows.Media.Visual>, a umožňuje implementovat chování uživatelského rozhraní, jako je výběrový obdélník pro výběr více objektů.  

<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>Scénáře testování přístupů  
 <xref:System.Windows.UIElement> Třída<xref:System.Windows.UIElement.InputHitTest%2A> poskytuje metodu, která umožňuje volání testu proti elementu pomocí dané hodnoty souřadnic. V mnoha případech <xref:System.Windows.UIElement.InputHitTest%2A> metoda poskytuje požadovanou funkci pro implementaci testování přístupů prvků. Existuje však několik scénářů, ve kterých může být nutné implementovat testování přístupů ve vizuální vrstvě.  
  
- Testování přístupů proti<xref:System.Windows.UIElement> objektům, které nejsou objekty: To platí v případě, že jste dosáhli<xref:System.Windows.UIElement> testování bez objektů, <xref:System.Windows.Media.DrawingVisual> například nebo grafických objektů.  
  
- Testování přístupů pomocí geometrie: To platí v případě, že je nutné použít test pomocí objektu geometrie namísto hodnoty souřadnic bodu.  
  
- Testování přístupů pro více objektů: To platí, pokud potřebujete vyzkoušet test proti více objektům, jako jsou překrývající se objekty. Můžete získat výsledky pro všechny vizuály protínající geometrii nebo bod, nikoli jenom první z nich.  
  
- Ignorují se zásady testování přístupů:<xref:System.Windows.UIElement> To platí v <xref:System.Windows.UIElement> případě, že potřebujete ignorovat zásady testování přístupů, které berou v úvahu takové faktory, jako je to, zda je prvek zakázán nebo neviditelný.  
  
> [!NOTE]
> Kompletní vzorek kódu ilustrující testování přístupů ve vizuální vrstvě naleznete v tématu [test volání pomocí DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994) a [test volání s ukázkovou mezichodem v systému Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>Podpora testování přístupů  
 Účelem <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metod<xref:System.Windows.Media.VisualTreeHelper> ve třídě je určit, zda je hodnota geometrie nebo souřadnice bodu v rámci vykresleného obsahu daného objektu, jako je například ovládací prvek nebo grafický prvek. Například můžete použít testování volání k určení, zda kliknutí myší v ohraničujícím obdélníku objektu spadá do geometrie kružnice. Můžete také přepsat výchozí implementaci testování přístupů, abyste mohli provádět vlastní výpočty testů přístupů.  
  
 Následující ilustrace znázorňuje vztah mezi oblastí mimo obdélníkový objekt a jeho ohraničujícím obdélníkem.  
  
 ![Diagram of valid hit test region](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagram platného regionu testu pozice  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>Testování přístupů a pořadí vykreslování  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Vizuální vrstva podporuje testování přístupů proti všem objektům v bodě nebo geometrii, nikoli pouze k nejvyššímu objektu. Výsledky se vrátí v pořadí z. Ale vizuální objekt, který předáte jako parametr <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodě, určuje, která část vizuálního stromu bude dosaženo testu. Můžete vyzkoušet test proti celému vizuálnímu stromu nebo jakékoli jeho části.  
  
 Na následujícím obrázku je objekt kruhu na obou objektech čtverce i trojúhelníku. Pokud vás zajímá jenom testování přístupů, u vizuálního objektu, jehož hodnota z pořadí z je nejvyšší, můžete nastavit výčet testů vizuálního testu, který se <xref:System.Windows.Media.HitTestResultBehavior.Stop> má vrátit <xref:System.Windows.Media.HitTestResultCallback> z, aby se zastavil test průchodu po první položce.  
  
 ![Diagram pořadí z&#45;ve vizuálním stromu](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagram z-pořadí vizuálního stromu  
  
 Pokud chcete zobrazit výčet všech vizuálních objektů v určitém bodě nebo geometrii, <xref:System.Windows.Media.HitTestResultBehavior.Continue> vraťte se <xref:System.Windows.Media.HitTestResultCallback>z. To znamená, že můžete vyzkoušet test pro vizuální objekty, které jsou pod jinými objekty, i když jsou zcela zakryté. Další informace najdete v ukázkovém kódu v části použití zpětného volání Výsledky testů.  
  
> [!NOTE]
> Je také možné, že je k dispozice vizuální objekt, který je transparentní.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Použití výchozího testování přístupů  
 Můžete určit, zda je bod v geometrii vizuálního objektu, pomocí <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody pro určení vizuálního objektu a hodnoty souřadnicového bodu pro testování. Parametr vizuálního objektu identifikuje výchozí bod ve vizuálním stromu pro hledání testu. Pokud je vizuální objekt nalezen ve vizuálním stromu, jehož geometrie obsahuje souřadnici, je nastavena na <xref:System.Windows.Media.HitTestResult.VisualHit%2A> vlastnost <xref:System.Windows.Media.HitTestResult> objektu. Pak se vrátí <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> z metody. <xref:System.Windows.Media.HitTestResult> Pokud není bod součástí vizuálního podstromu, který jste provedli testování, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> vrátí. `null`  
  
> [!NOTE]
> Výchozí testování přístupů vždy vrátí objekt nejvyšší úrovně v pořadí vykreslování. Pro identifikaci všech vizuálních objektů, i těch, které mohou být částečně nebo zcela zakryty, použijte zpětné volání výsledku testu volání.  
  
 Hodnota souřadnice, kterou předáte jako parametr bodu pro metodu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> , musí být relativní vzhledem k prostoru souřadnic objektu vizuálu, ke kterému se chcete testovat. Například pokud máte vnořené vizuální objekty definované na (100, 100) v prostoru souřadnic nadřazeného objektu, potom je možné otestovat podřízený vizuál na pozici (0, 0) v souřadnicovém prostoru nadřazeného objektu (100, 100).  
  
 Následující kód ukazuje, jak nastavit obslužné rutiny událostí myši pro <xref:System.Windows.UIElement> objekt, který se používá k zachycení událostí používaných pro testování přístupů.  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Vliv vizuálního stromu na testování přístupů  
 Výchozí bod ve vizuálním stromu určuje, které objekty jsou vraceny během výčtu testů přístupů objektů. Pokud máte více objektů, které chcete vyzkoušet, musí být vizuální objekt použitý jako výchozí bod ve vizuálním stromu společným nadřazeným prvkem všech objektů, které vás zajímají. Pokud jste například zaznamenali, že se má v následujícím diagramu testovat, jak element Button, tak vykreslování vizuálu, je nutné nastavit výchozí bod ve vizuálním stromu na společný nadřazený prvek obou. V tomto případě je element plátno společným nadřazeným prvkem elementu Button a vykreslováním vizuálu.  
  
 ![Diagram hierarchie vizuálního stromu](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagram hierarchie vizuálního stromu  
  
> [!NOTE]
> Vlastnost získává nebo nastavuje hodnotu, která deklaruje, <xref:System.Windows.UIElement>zda může být objekt odvozený z některé části vykresleného obsahu vrácen jako výsledek testu volání. <xref:System.Windows.UIElement.IsHitTestVisible%2A> To umožňuje selektivní změnu vizuálního stromu, aby bylo možné určit, které vizuální objekty jsou součástí testu volání.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Použití zpětného volání výsledků testu volání  
 Můžete vytvořit výčet všech vizuálních objektů ve vizuálním stromu, kde geometrie obsahuje zadanou hodnotu souřadnic. To vám umožňuje identifikovat všechny vizuální objekty, i ty, které mohou být částečně nebo zcela zakryty jinými vizuálními objekty. Pro zobrazení výčtu vizuálních objektů ve vizuálním stromu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> použijte metodu s funkcí zpětného volání testu přístupů. Funkce zpětného volání testu volání je volána systémem, pokud je hodnota souřadnic, kterou zadáte, obsažena ve vizuálním objektu.  
  
 Během výčtu výsledků testů přístupů byste neměli provádět žádné operace, které upraví vizuální strom. Přidání nebo odebrání objektu ve vizuálním stromu během procházení může způsobit nepředvídatelné chování. Vizuální strom můžete po <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> návratu metody bezpečně upravit. Je možné, že budete chtít poskytnout datovou strukturu, <xref:System.Collections.ArrayList>jako je například, k uložení hodnot během výčtu výsledků testů přístupů.  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 Metoda zpětného volání testu volání definuje akce, které provedete při identifikaci testu volání u určitého vizuálního objektu ve vizuálním stromu. Po provedení těchto akcí vrátíte <xref:System.Windows.Media.HitTestResultBehavior> hodnotu, která určuje, zda se má pokračovat ve výčtu všech dalších vizuálních objektů nebo nikoli.  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> Pořadí výčtu vizuálních objektů přístupů je podle pořadí z. Vizuální objekt na nejvyšší úrovni pořadí z je prvním objektem výčtu. Všechny ostatní vizuální objekty, které jsou ve výčtu, jsou zmenšeny na úrovni z. Toto pořadí výčtu odpovídá pořadí vykreslování vizuálů.  
  
 Výčty vizuálních objektů můžete kdykoli zastavit ve funkci zpětného volání testu volání vrácením <xref:System.Windows.Media.HitTestResultBehavior.Stop>.  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Použití zpětného volání filtru testu volání  
 Pomocí volitelného filtru testu přístupů můžete omezit objekty, které jsou předány do výsledků testu přístupů. To vám umožní ignorovat části vizuálního stromu, které nebudete zajímat o zpracování ve výsledcích testů přístupů. Chcete-li implementovat filtr testů přístupů, definujte funkci zpětného volání filtru testu a předejte ji jako hodnotu parametru při volání <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Pokud nechcete dodat volitelnou funkci zpětného volání filtru testu, předejte `null` hodnotu jako parametr <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> pro metodu.  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Vyřazení vizuálního stromu pomocí filtru testů přístupů](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Vyřazení vizuálního stromu  
  
 Funkce zpětného volání filtru testu umožňuje vytvořit výčet pomocí všech vizuálů, jejichž vykreslený obsah obsahuje souřadnice, které zadáte. Můžete ale chtít ignorovat určité větve vizuálního stromu, které nebudete mít na zpracování ve funkci zpětného volání výsledků testů přístupů. Návratová hodnota funkce zpětného volání filtru testu je určena pro typ akce, které by měly vybírat výčty vizuálních objektů. Například pokud vrátíte hodnotu <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, můžete odebrat aktuální vizuální objekt a jeho podřízené položky z výčtu výsledků testů přístupů. To znamená, že funkce zpětného volání výsledků testu volání nebudou tyto objekty ve svém výčtu zobrazovat. Vyřazení vizuálního stromu objektů snižuje množství zpracování během průchodu výčtu výsledků testů přístupů. V následujícím příkladu kódu filtr přeskočí popisky a jejich následníky a zavoláním všech ostatních.  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> V případech, kdy zpětné volání výsledků testu volání není voláno, bude v některých případech voláno zpětné volání filtru testu přístupů.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Přepsání výchozího testování přístupů  
 Můžete přepsat výchozí podporu testování přístupů vizuálního objektu přepsáním <xref:System.Windows.Media.Visual.HitTestCore%2A> metody. To znamená, že při vyvolání <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody <xref:System.Windows.Media.Visual.HitTestCore%2A> je volána přepsaná implementace. Přepsaná metoda je volána, když test volání spadá do ohraničujícího obdélníku vizuálního objektu, a to i v případě, že souřadnice spadá mimo vykreslený obsah vizuálního objektu.  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Můžou nastat situace, kdy budete chtít vyzkoušet test proti ohraničujícímu obdélníku i vykreslenému obsahu vizuálního objektu. Použitím `PointHitTestParameters` hodnoty parametru v přepsané <xref:System.Windows.Media.Visual.HitTestCore%2A> metodě jako parametru základní metody <xref:System.Windows.Media.Visual.HitTestCore%2A>můžete provádět akce založené na dosažení ohraničujícího obdélníku vizuálního objektu a poté provést druhý test volání proti vykreslený obsah vizuálního objektu  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [Test volání pomocí DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994)
- [Test volání s ukázkovou meziprovozu Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Ověření pozice objektu Geometry ve vizuálním objektu](how-to-hit-test-geometry-in-a-visual.md)
- [Ověřování pozice pomocí kontejneru hostitele Win32](how-to-hit-test-using-a-win32-host-container.md)
