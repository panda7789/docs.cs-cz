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
ms.openlocfilehash: fe54578407e881ec7d6782ec21100b29eded07a3
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44176673"
---
# <a name="hit-testing-in-the-visual-layer"></a>Spuštění testování ve vizuální vrstvě
Toto téma obsahuje základní informace o volání funkce testování k dispozici ve vizuální vrstvě. Volání podpory testování umožňuje určit, zda hodnota geometrie nebo bodu spadá do vykreslený obsah <xref:System.Windows.Media.Visual>, abyste mohli implementovat rozhraní chování uživatelů, jako je například obdélníku výběru vybrat více objektů.  
  
 
  
<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>Spuštění testovacích scénářů  
 <xref:System.Windows.UIElement> Třída poskytuje <xref:System.Windows.UIElement.InputHitTest%2A> metodu, která umožňuje spuštění testu oproti elementu s použitím dané hodnoty souřadnic. V mnoha případech <xref:System.Windows.UIElement.InputHitTest%2A> metoda poskytuje požadované funkce pro provádění přístupů testování prvků. Existují však několik scénářů, ve kterých budete muset implementovat přístupů testování ve vizuální vrstvě.  
  
-   Spuštění testování na jinou hodnotu než<xref:System.Windows.UIElement> objekty: To platí, pokud dosáhnete testování jinou hodnotu než<xref:System.Windows.UIElement> objekty, jako například <xref:System.Windows.Media.DrawingVisual> nebo grafických objektů.  
  
-   Spuštění testování pomocí geometrii: To platí, pokud je potřeba spuštění testu použitím geometrie objektu, nikoli hodnotu souřadnice bodu.  
  
-   Spuštění testování na více objektů: To platí, když budete chtít spuštění testu s více objekty, jako je překrývání objekty. Získat výsledky pro všechny vizuály protínající se operátory geometrie nebo bodu, nikoli pouze první z nich.  
  
-   Ignorování <xref:System.Windows.UIElement> přístupů k testování zásad: To platí, pokud chcete ignorovat <xref:System.Windows.UIElement> přístupů k testování zásad, který bere v úvahu faktory, jako Určuje, zda je prvek zakázaný nebo neviditelné.  
  
> [!NOTE]
>  Testování ve vizuální vrstvě kompletní kód ukázkové ilustrující průchodu, najdete v části [ukázka spuštění testu DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994) a [spuštění testu s ukázkou vzájemná spolupráce grafického subsystému Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>Spuštění testování podpory  
 Účelem <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody v <xref:System.Windows.Media.VisualTreeHelper> třídy je určit, zda je geometrie nebo bod souřadnic hodnota v rámci daného objektu, jako je například ovládací prvek nebo grafický element vykreslovaný obsah. Například můžete použít volání testování k určení, zda kliknutí myší v rámci ohraničující obdélník objektu spadá do geometrie kruh. Můžete také přepsat výchozí implementaci přístupů testování provádět výpočty vlastní pozice.  
  
 Následující ilustrace znázorňuje vztah mezi oblasti obdélníkový objektu a jeho ohraničující obdélník.  
  
 ![Diagram platná pozice oblasti](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagram platná pozice oblasti  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>Přístupů testování a pořadí Z-Order  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Vizuální vrstvy podporuje přístupů testování pro všechny objekty v rámci bodu nebo geometrie, ne jenom nejvyšším objektem. Výsledky jsou vráceny v pořadí vykreslování. Ale vizuální objekt, který můžete předat jako parametr <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda určuje, jaká část z vizuálního stromu, který bude spuštění testu. Možné spuštění testu oproti celý vizuální strom nebo jakékoli její části je.  
  
 Na následujícím obrázku je objekt circle nad čtverec i trojúhelník objekty. Pokud vás zajímá jenom v přístupů k testování vizuální objekt, jehož hodnota pořadí vykreslování je úplně nahoře, můžete nastavit vizuální pozice výčtu vrátit <xref:System.Windows.Media.HitTestResultBehavior.Stop> z <xref:System.Windows.Media.HitTestResultCallback> Zastavit procházení ověření pozice po první položky.  
  
 ![Diagram vykreslování&#45;pořadí vizuální strom](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagram pořadí vykreslování vizuální strom  
  
 Pokud chcete vytvořit výčet všech vizuálních objektů v rámci určitého bodu nebo geometrie, vrátí <xref:System.Windows.Media.HitTestResultBehavior.Continue> z <xref:System.Windows.Media.HitTestResultCallback>. To znamená, že můžete spuštění testu pro vizuální objekty, které jsou pod jinými objekty, i když jsou zcela zakryto. Zobrazit ukázkový kód v části "Pomocí spuštění testu výsledky zpětné volání" Další informace.  
  
> [!NOTE]
>  Vizuální objekty, které je transparentní můžou také narazit testování.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Použijte výchozí nastavení testování průchodu  
 Můžete určit, jestli je bod v rámci geometrie vizuální objekty s použitím <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda zadat vizuální objekty a bod koordinovat hodnota pro porovnání výsledků testů. Vizuální objekty parametr určuje počáteční bod ve vizuálním stromu pro hledání pozice. Pokud vizuální objekt nachází ve vizuálním stromu, jejichž geometrie obsahuje souřadnice, je nastavena na <xref:System.Windows.Media.HitTestResult.VisualHit%2A> vlastnost <xref:System.Windows.Media.HitTestResult> objektu. <xref:System.Windows.Media.HitTestResult> Je pak vrácen z <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody. Pokud je bod není obsažena s visual podstromě testování, jsou průchodu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> vrátí `null`.  
  
> [!NOTE]
>  Výchozí přístupů k testování vždy vrátí nejvyšším objektem v pořadí vykreslování. Za účelem zjištění všech vizuálních objektů, včetně těch, které může být částečně nebo zcela zakryto, použijte zpětné volání výsledek ověření pozice.  
  
 Souřadnice hodnotu předat jako parametr bodu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> musí být relativní vzhledem k souřadnicového prostoru visual dosáhnete testování proti objektu. Například pokud mít člověk vnořené vizuální objekty, které se definované na (100, 100) v souřadnicového prostoru nadřazené položky, stiskněte testování vizuálu podřízené po (0, 0) odpovídá na testování průchodu (100, 100) v souřadnicového prostoru nadřazeného objektu.  
  
 Následující kód ukazuje, jak nastavit myš obslužné rutiny událostí pro <xref:System.Windows.UIElement> objekt, který se používá k zachycení událostí používá pro testování průchodu.  
  
 [!code-csharp[HitTestingOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Jak ovlivňuje vizuálního stromu testování průchodu  
 Výchozí bod ve vizuálním stromu Určuje, které objekty jsou vráceny při ověření pozice výčtu objektů. Pokud máte více objektů, které chcete spuštění testu, musí být visual objekt použitý jako výchozí bod ve vizuálním stromu společného předchůdce všechny objekty, které vás zajímají. Pokud by vás zajímaly přístupů k testování button element a kreslení visual v následujícím diagramu, je třeba nastavit výchozí bod ve vizuálním stromu do společného předchůdce obou. V tomto případě je canvas element společného předchůdce prvku button a vykreslení vizuálu.  
  
 ![Diagram hierarchie vizuální strom](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagram hierarchie vizuální strom  
  
> [!NOTE]
>  <xref:System.Windows.UIElement.IsHitTestVisible%2A> Vlastnost získává nebo nastavuje hodnotu, která deklaruje, jestli <xref:System.Windows.UIElement>-odvozeného objektu může vracet jako výsledek ověření pozice z některé části vykresleného obsahu. To umožňuje selektivně alter vizuálního stromu, chcete-li zjistit, které vizuální objekty jsou součástí ověření pozice.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Pomocí zpětného volání výsledek ověření pozice  
 Můžete zobrazit výčet všech vizuálních objektů ve vizuálním stromu jehož geometrie obsahuje zadanou hodnotu souřadnice. To umožňuje identifikovat všechny vizuální objekty, a to i těch, které může být částečně nebo zcela zakryto jiné vizuální objekty. Výčet vizuální objekty v vizuálního stromu. použijte <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodu ověření pozice funkce zpětného volání. Funkce zpětného volání ověření pozice je volán systému při souřadnic hodnota, kterou zadáte je obsažen v objektu visual.  
  
 Během shodu testovat výčtu výsledků, byste neměli provádět všechny operace, která upravuje vizuálního stromu. Přidání nebo odebrání objektu z vizuálního stromu, zatímco ji procházet může způsobit nepředvídatelné chování. Můžete bezpečně upravovat vizuální strom za <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda vrátí hodnotu. Můžete chtít poskytnout datové struktury, jako například <xref:System.Collections.ArrayList>pro uložení hodnoty během ověření pozice výčtu výsledků.  
  
 [!code-csharp[HitTestingOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 Metoda zpětného volání ověření pozice definuje akce, které provedete, když ověření pozice je identifikován na konkrétní vizuální objekty ve vizuálním stromu. Po provedení akce, které se vrátit <xref:System.Windows.Media.HitTestResultBehavior> hodnotu, která určuje, jestli se má pokračovat výčet jiných vizuálních objektů, nebo ne.  
  
 [!code-csharp[HitTestingOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
>  Pořadí výčtu přístupů vizuálních objektů je podle pořadí vykreslování. Vizuální objekty na úrovni pořadí vykreslování úplně nahoře je první objekt výčtu. Vizuální objekty ve výčtu jsou v sestupném pořadí vykreslování úroveň. Toto pořadí výčtu odpovídá pořadí vykreslování vizuály.  
  
 Výčet vizuální objekty v každém okamžiku ve funkci zpětného volání ověření pozice lze zastavit tak, že vrací <xref:System.Windows.Media.HitTestResultBehavior.Stop>.  
  
 [!code-csharp[HitTestingOverview#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Pomocí filtru zpětného volání ověření pozice  
 Filtr volitelné pozice můžete omezit objekty, které jsou předány výsledky ověření pozice. To umožňuje ignorovat součástí vizuálního stromu, že zatím nejste zájem o zpracování ve výsledcích ověření pozice. K provedení ověření pozice filtr, definice funkce zpětného volání ověření pozice filtru a předat ji jako hodnotu parametru při volání <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.  
  
 [!code-csharp[HitTestingOverview#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Pokud nechcete zadat volitelný pozice funkce zpětného volání filtru, předat `null` hodnotu jako svůj parametr pro <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.  
  
 [!code-csharp[HitTestingOverview#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Vyřazování vizuálního stromu pomocí filtru ověření pozice](../../../../docs/framework/wpf/graphics-multimedia/media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Vyřazování vizuální strom  
  
 Funkce zpětného volání ověření pozice filtru můžete zobrazit výčet prostřednictvím všechny vizuály vykreslené obsahující souřadnice, které zadáte. Můžete však chtít ignorovat určité větve vizuálního stromu, že zatím nejste zájem o zpracování ve své funkci zpětného volání výsledky ověření pozice. Návratovou hodnotu funkce zpětného volání při ověření pozice filtr určuje, jaký typ akce výčtu vizuálních objektů by měl trvat. Pokud vrátí hodnotu, například <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, můžete odebrat aktuální vizuální objekt a jeho podřízené položky z výčtu výsledků ověření pozice. To znamená, že funkce zpětného volání výsledky ověření pozice neuvidí tyto objekty v její výčet. Vyřazování vizuální strom objektů snižuje objem zpracování se při průchodu výčtu výsledků ověření pozice. V následujícím příkladu kódu filtr přeskočí popisky a jejich následníků a stiskněte klávesu testy všechno ostatní.  
  
 [!code-csharp[HitTestingOverview#106](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
>  Ověření pozice volání filtru se někdy nazývá v případech, kde není volána, zpětné volání výsledky ověření pozice.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Přepsání výchozího testování průchodu  
 Můžete přepsat výchozí přístupů vizuální objekty podporu testování tak, že přepíšete <xref:System.Windows.Media.Visual.HitTestCore%2A> metody. To znamená, že při vyvolání <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody, přepsané implementace <xref:System.Windows.Media.Visual.HitTestCore%2A> je volána. Přepsané metody se volá při ověření pozice spadá do ohraničující obdélník vizuální objekty i v případě, že bod se souřadnicemi spadá mimo vykreslený obsah vizuální objekty.  
  
 [!code-csharp[HitTestingOverview#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Může nastat situace, kdy budete chtít spuštění testu oproti ohraničující obdélník a vykreslený obsah vizuální objekty. S použitím `PointHitTestParameters` hodnota parametru v vaše přepsané <xref:System.Windows.Media.Visual.HitTestCore%2A> metodu jako parametr základní metodě <xref:System.Windows.Media.Visual.HitTestCore%2A>, můžete provádět akce podle položek z ohraničující obdélník vizuální objekty a pak proveďte druhý pozice proti vykreslí obsah vizuální objekty.  
  
 [!code-csharp[HitTestingOverview#108](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 <xref:System.Windows.Media.HitTestResult>  
 <xref:System.Windows.Media.HitTestResultCallback>  
 <xref:System.Windows.Media.HitTestFilterCallback>  
 <xref:System.Windows.UIElement.IsHitTestVisible%2A>  
 [Spuštění testu použitím DrawingVisuals vzorku](https://go.microsoft.com/fwlink/?LinkID=159994)  
 [Spuštění testu s ukázkou Win32 vzájemné spolupráce](https://go.microsoft.com/fwlink/?LinkID=159995)  
 [Ověření pozice objektu Geometry ve vizuálním objektu](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)  
 [Ověřování pozice pomocí kontejneru hostitele Win32](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-a-win32-host-container.md)
