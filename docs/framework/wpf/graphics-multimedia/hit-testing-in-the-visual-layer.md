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
ms.openlocfilehash: 60da11af51722e86a61c5e3298fafba2221f000b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558106"
---
# <a name="hit-testing-in-the-visual-layer"></a>Spuštění testování ve vizuální vrstvě
Toto téma poskytuje přehled o počtu testování funkce poskytované službou visual vrstvy. Přístupů testování podpory umožňuje určit, zda hodnota geometrie nebo bodu spadá do vykreslené obsah <xref:System.Windows.Media.Visual>, což umožňuje implementovat rozhraní chování uživatelů, jako je například obdélníku výběru vybrat více objektů.  
  
 
  
<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>Stiskněte tlačítko testovacích scénářů  
 <xref:System.Windows.UIElement> Třída poskytuje <xref:System.Windows.UIElement.InputHitTest%2A> metodu, která umožňuje průchodu testu u elementu s použitím dané hodnoty souřadnic. V mnoha případech <xref:System.Windows.UIElement.InputHitTest%2A> metoda poskytuje požadované funkce pro implementaci přístupů testování elementů. Existují však několik scénářů, ve kterých budete muset implementovat přístupů testování ve visual vrstvě.  
  
-   Testování s jinou hodnotu než průchodu<xref:System.Windows.UIElement> objekty: To platí, pokud jsou dosáhl testování jinou hodnotu než<xref:System.Windows.UIElement> objekty, jako například <xref:System.Windows.Media.DrawingVisual> nebo grafických objektů.  
  
-   Testování pomocí geometry průchodu: To platí, pokud potřebujete průchodu testu s použitím geometrický objekt spíše než hodnota souřadnice bodu.  
  
-   Testování proti více objektů průchodu: To platí, když potřebujete průchodu testu u více objektů, jako je například překrývající se objekty. Můžete získat výsledky pro všechny vizuály protínající se operátory geometrie nebo bodu, nikoli pouze první z nich.  
  
-   Ignoruje <xref:System.Windows.UIElement> vstupů do testování zásad: To platí, když potřebujete Ignorovat <xref:System.Windows.UIElement> vstupů do testování zásadu, která vezme v úvahu faktory, jako jestli element vypnutá nebo neviditelné.  
  
> [!NOTE]
>  Ukázka kompletní kód ilustrující testování ve vrstvě visual průchodu, najdete v části [ukázka průchodu testu DrawingVisuals](http://go.microsoft.com/fwlink/?LinkID=159994) a [stiskněte tlačítko Test s ukázkou vzájemná spolupráce Win32](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>Stiskněte tlačítko testování podpory  
 Účelem <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody v <xref:System.Windows.Media.VisualTreeHelper> třída je určit, zda je hodnota souřadnic geometrie nebo bodu v rámci vykreslené obsah daného objektu, například na ovládací prvek nebo grafický element. Například můžete použít přístupů testování k určení zda klikněte na tlačítko myši, v rámci ohraničující obdélník objekt spadá do geometrie kruh. Můžete také přepsat výchozí implementaci přístupů testování k provedení vlastní vlastní test zásahu výpočty.  
  
 Následující obrázek znázorňuje vztahy mezi obdélníkový objekt oblasti a jeho ohraničující obdélník.  
  
 ![Diagram přístupů testovací oblasti](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagram platné oblasti ověření pozice  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>Testování přístupů a pořadí Z-Order  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Visual vrstvy podporuje přístupů testování u všech objektů v rámci bodu nebo geometry, nikoli pouze objekt nejvyšší. Výsledky jsou vráceny v pořadí z-order. Ale visual objekt, který můžete předat jako parametr <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda určuje, jaká část visual stromové struktury, která se setkají otestovat. Můžete zahájit test proti celý vizuálním stromu, nebo jakékoli její části je.  
  
 Na následujícím obrázku objekt kroužek je nad hranaté i trojúhelníček objekty. Pokud vás zajímá jenom podle testování vizuální objekt, jehož hodnota pořadí z-order je nejvyšší, můžete nastavit visual přístupů testu výčtu vrátit <xref:System.Windows.Media.HitTestResultBehavior.Stop> z <xref:System.Windows.Media.HitTestResultCallback> zastavit traversal ověření pozice po první položka.  
  
 ![Diagram vykreslování&#45;pořadí vizuálním stromu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagram pořadí vykreslování vizuálním stromu  
  
 Pokud chcete vytvořit výčet všech vizuální objekty v rámci konkrétní bodu nebo geometry, vrátí <xref:System.Windows.Media.HitTestResultBehavior.Continue> z <xref:System.Windows.Media.HitTestResultCallback>. To znamená, že test pro vizuální objekty, které jsou pod jiné objekty, můžete přístupů, i když jsou zcela skryt. Najdete ukázkový kód v části "Použití stiskněte tlačítko Test výsledky zpětného volání" Další informace.  
  
> [!NOTE]
>  Vizuální objekt, který je transparentní, může být také dosáhl otestovat.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Použijte výchozí nastavení testování průchodu  
 Zjistíte, zda bod je v rámci geometrie vizuální objekt pomocí <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda k určení vizuální objekt a bod koordinaci testovanou hodnotu. Parametr visual objektu identifikuje výchozí bod v vizuálním stromu pro ověření pozice hledání. Pokud vizuální objekt nachází ve vizuálním stromu, jejichž geometrie obsahuje souřadnice, je nastavený na <xref:System.Windows.Media.HitTestResult.VisualHit%2A> vlastnost <xref:System.Windows.Media.HitTestResult> objektu. <xref:System.Windows.Media.HitTestResult> Je pak vrácen z <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda. Pokud je bod není obsažen s visual podstromu testování, jsou průchodu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> vrátí `null`.  
  
> [!NOTE]
>  Stiskněte klávesu výchozí testování vždy vrátí objekt nejvyšší v pořadí. Za účelem zjištění všech vizuální objekty, i ty, které mohou být částečně nebo zcela skryté, použijte zpětné volání výsledek ověření pozice.  
  
 Souřadnice hodnotu předejte jako parametr bod pro <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda musí být relativní vzhledem k souřadnicového prostoru visual objektu testování proti jsou průchodu. Například pokud mít člověk vnořené vizuální objekty, které se definované na (100, 100) v poli nadřazeného objektu souřadnicového prostoru, pak testování průchodu podřízené visual v (0, 0) odpovídá na testování průchodu (100, 100) v poli nadřazeného objektu souřadnicového prostoru.  
  
 Následující kód ukazuje, jak nastavit myši obslužných rutin událostí pro <xref:System.Windows.UIElement> objekt, který se používá k zaznamenání události použité pro testování průchodu.  
  
 [!code-csharp[HitTestingOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Jak ovlivňuje vizuálním stromu testování průchodu  
 Počáteční bod ve vizuální strojové struktuře Určuje, které objekty jsou vráceny při ověření pozice výčtu objektů. Pokud máte více objektů, které chcete zahájit test, musí být visual objekt použitý jako výchozí bod v vizuálním stromu běžné nadřazeného všechny objekty, které vás zajímají. Pokud byste byli zájem o vstupů do testování button element a kreslení visual v následujícím diagramu, je třeba nastavit výchozí bod v vizuálním stromu pro běžné nadřazeného obou. V takovém případě je canvas element běžné nadřazeného prvku tlačítko a kreslení visual.  
  
 ![Diagram hierarchie vizuálním stromu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagram hierarchie vizuálním stromu  
  
> [!NOTE]
>  <xref:System.Windows.UIElement.IsHitTestVisible%2A> Vlastnost získá nebo nastaví hodnotu, která uvádí, zda <xref:System.Windows.UIElement>-odvozené objekt mohou být vráceny pravděpodobně v důsledku toho test zásahu z některá část jeho vykreslené obsah. To umožňuje selektivně alter vizuálním stromu určit visual objektů, které se účastní testu přístupů.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Pomocí zpětného volání výsledek ověření pozice  
 Můžete vytvořit výčet všech vizuální objekty ve vizuálním stromu, jejichž geometrie obsahuje zadanou hodnotu souřadnice. To umožňuje identifikovat všechny vizuální objekty, a to i těch, které mohou být částečně nebo zcela skryté jiné visual objekty. Výčet vizuální objekty ve vizuálním stromu použití <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda s přístupů testovací funkci zpětného volání. Funkce zpětného volání ověření pozice je volána v systému, když souřadnic hodnota, kterou zadáte, je součástí vizuální objekt.  
  
 Při shodě test výčtu výsledků, nesmí provádět všechny operace, která upraví vizuálním stromu. Přidávání ani odebírání objekt z vizuálním stromu, pokud ji provázán může způsobit nepředvídatelné chování. Můžete upravit bezpečně vizuálním stromu po <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda vrátí. Můžete chtít zadejte datová struktura, jako třeba <xref:System.Collections.ArrayList>, k ukládání hodnot během výčtu výsledků ověření pozice.  
  
 [!code-csharp[HitTestingOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 Metoda zpětného volání ověření pozice definuje akce, které můžete provést při testu přístupů je označený pro daný objekt visual ve vizuálním stromu. Po provedení akce, které se vrátíte <xref:System.Windows.Media.HitTestResultBehavior> hodnotu, která určuje, jestli pokračovat výčet jiné vizuální objekty, nebo ne.  
  
 [!code-csharp[HitTestingOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
>  Pořadí výčet přístupů vizuální objekty, je pořadí z-order. Vizuální objekt na úrovni nejvyšší pořadí z-order je první objekt ve výčtu. Vizuální objekty uvedené jsou v sestupném pořadí z-order úroveň. Toto pořadí výčtu odpovídá pořadí vykreslování ve vizuálech.  
  
 Výčet vizuální objekty v funkce zpětného volání ověření pozice kdykoli můžete zastavit vrácením <xref:System.Windows.Media.HitTestResultBehavior.Stop>.  
  
 [!code-csharp[HitTestingOverview#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Pomocí filtru zpětného volání ověření pozice  
 Filtr volitelné ověření pozice můžete omezit objekty, které se budou předávat výsledky testů přístupů. To umožňuje ignorovat částí vizuálním stromu, že nejste zájem o zpracování v si výsledky testu přístupů. Implementace filtru ověření pozice, definovat funkci zpětného volání ověření pozice filtru a předejte ji jako hodnotu parametru při volání <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda.  
  
 [!code-csharp[HitTestingOverview#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Pokud nechcete zadat funkce zpětného volání filtru volitelné ověření pozice, předávání `null` hodnotu jako jeho parametr pro <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda.  
  
 [!code-csharp[HitTestingOverview#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Vyřazování vizuálním stromu pomocí filtru ověření pozice](../../../../docs/framework/wpf/graphics-multimedia/media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Vyřazování vizuálním stromu  
  
 Funkce zpětného volání filtru přístupů test umožňuje výčet prostřednictvím všech vizuálních prvků, jejichž vykreslené obsah obsahuje souřadnice, které zadáte. Můžete však ignorovat některé větve vizuálním stromu, že nejste zájem o zpracování v funkce zpětného volání výsledky ověření pozice. Návratová hodnota funkce zpětného volání ověření pozice filtru určuje, jaký typ akce výčet vizuální objekty provést. Pokud vrátí hodnotu, například <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, aktuální vizuální objekt a její podřízené položky můžete odebrat z výčtu výsledků ověření pozice. To znamená, že funkce zpětného volání výsledky ověření pozice nebude tyto objekty v její výčet. Vyřazování vizuálním stromu objektů snižuje objem zpracování se při průchodu výčtu výsledků ověření pozice. V následujícím příkladu kódu filtr přeskočí popisky a jejich následníků a stiskněte klávesu testy nic jiného.  
  
 [!code-csharp[HitTestingOverview#106](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
>  Zpětné volání filtru ověření pozice se někdy nazývá v případech, kde není volán zpětného volání výsledky ověření pozice.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Přepsání výchozího testování průchodu  
 Můžete přepsat vstupů do výchozí vizuální objekt testování podporu přepsáním <xref:System.Windows.Media.Visual.HitTestCore%2A> metoda. To znamená, že při vyvolání <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda, vaši implementaci přepsaného <xref:System.Windows.Media.Visual.HitTestCore%2A> je volána. Přepsaná metoda je volána, když testu přístupů spadá do ohraničující obdélník objekt visual i v případě, že souřadnice spadá mimo vykreslené obsah vizuální objekt.  
  
 [!code-csharp[HitTestingOverview#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Může nastat situace, kdy budete chtít zahájit test proti ohraničující obdélník i vykreslené obsah vizuální objekt. Pomocí `PointHitTestParameters` hodnota parametru v vaší přepsané <xref:System.Windows.Media.Visual.HitTestCore%2A> metoda jako parametr pro základní metody <xref:System.Windows.Media.Visual.HitTestCore%2A>, můžete provádět akce založené na každý přístup ohraničující obdélník vizuální objekt a poté proveďte druhý test přístupů proti vykreslení obsahu visual objektu.  
  
 [!code-csharp[HitTestingOverview#108](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 <xref:System.Windows.Media.HitTestResult>  
 <xref:System.Windows.Media.HitTestResultCallback>  
 <xref:System.Windows.Media.HitTestFilterCallback>  
 <xref:System.Windows.UIElement.IsHitTestVisible%2A>  
 [Stiskněte tlačítko testu s použitím DrawingVisuals vzorku](http://go.microsoft.com/fwlink/?LinkID=159994)  
 [Stiskněte tlačítko Test s ukázkou součinnosti Win32](http://go.microsoft.com/fwlink/?LinkID=159995)  
 [Ověření pozice objektu Geometry ve vizuálním objektu](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)  
 [Ověřování pozice pomocí kontejneru hostitele Win32](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-a-win32-host-container.md)
