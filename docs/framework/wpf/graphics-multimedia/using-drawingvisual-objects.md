---
title: Použití objektů DrawingVisual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
ms.openlocfilehash: 799892424f92782d71b9a35e76d722d1725815ea
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861842"
---
# <a name="using-drawingvisual-objects"></a>Použití objektů DrawingVisual
Toto téma obsahuje přehled o tom, jak používat <xref:System.Windows.Media.DrawingVisual> objekty v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vizuální vrstvy.  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>Objektů DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> Představuje jednoduché kreslení třídu, která se použije k vykreslení obrazce, Image nebo text. Tato třída se považuje za jednoduché, protože neposkytuje rozložení nebo událostí zpracování, což zvyšuje výkon. Z tohoto důvodu jsou ideální pro pozadí a klipart kreslení.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual hostitele kontejneru  
 Chcete-li použít <xref:System.Windows.Media.DrawingVisual> objekty, je potřeba vytvořit hostitele kontejner pro objekty. Objekt kontejneru hostitele musí být odvozen od <xref:System.Windows.FrameworkElement> třídu, která poskytuje rozložení a zpracování událostí, které podporují <xref:System.Windows.Media.DrawingVisual> třídy chybí. Objekt kontejneru hostitele nezobrazuje viditelných vlastností, protože jejich hlavním účelem je tak, aby obsahovala podřízené objekty. Ale <xref:System.Windows.UIElement.Visibility%2A> vlastnost kontejneru hostitele musí být nastavena na <xref:System.Windows.Visibility.Visible>; v opačném případě žádný z jejích podřízených elementů se nebude zobrazovat.  
  
 Při vytváření objektu kontejneru hostitele pro vizuální objekty potřebujete ukládat odkazy na vizuální objekty v <xref:System.Windows.Media.VisualCollection>. Použití <xref:System.Windows.Media.VisualCollection.Add%2A> způsob, jak přidat vizuální objekt kontejneru hostitele. V následujícím příkladu je vytvořen objekt kontejneru hostitele a tři vizuální objekty jsou přidány do jeho <xref:System.Windows.Media.VisualCollection>.  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  Kompletní kód ukázku, ze které byla extrahována v předchozím příkladu kódu najdete v tématu [ukázka spuštění testu DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Vytváření objektů DrawingVisual  
 Když vytvoříte <xref:System.Windows.Media.DrawingVisual> objektu, nemá žádný obsah. Načtením objektu můžete přidat text, grafiku nebo obsahu bitové kopie <xref:System.Windows.Media.DrawingContext> a kreslení do něj. A <xref:System.Windows.Media.DrawingContext> je vrácený voláním <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metodu <xref:System.Windows.Media.DrawingVisual> objektu.  
  
 Chcete-li nakreslit obdélník do <xref:System.Windows.Media.DrawingContext>, použít <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> metodu <xref:System.Windows.Media.DrawingContext> objektu. Podobné metody existují pro vytvoření jiných typů obsahu. Po dokončení vykreslení obsahu <xref:System.Windows.Media.DrawingContext>, volání <xref:System.Windows.Media.DrawingContext.Close%2A> metoda zavřete <xref:System.Windows.Media.DrawingContext> a zachovat obsah.  
  
 V následujícím příkladu <xref:System.Windows.Media.DrawingVisual> objekt je vytvořen a vykreslení obdélníku do jeho <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>Vytváření přepsání pro objekt FrameworkElement členy  
 Objekt kontejneru hostitele zodpovídá za správu jeho kolekcí vizuálních objektů. To vyžaduje, aby kontejneru hostitele implementovat přepsání členů pro odvozený <xref:System.Windows.FrameworkElement> třídy.  
  
 Následující seznam popisuje dva členy, které je nutné přepsat:  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Vrací podřízenou položku v zadaném indexu z kolekce podřízených elementů.  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Získá počet visual podřízených elementů v rámci tohoto elementu.  
  
 V následujícím příkladu, přepíše dvou <xref:System.Windows.FrameworkElement> členy jsou implementovány.  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>Poskytuje podporu přístupů testování  
 Hostitelský objekt kontejneru můžete zadat, událostí zpracování i v případě, že nejsou zobrazeny žádné viditelné vlastnosti, ale jeho <xref:System.Windows.UIElement.Visibility%2A> musí být vlastnost nastavena na <xref:System.Windows.Visibility.Visible>. To umožňuje vytvořit událost zpracování rutiny pro hostitele kontejneru, který může zachytávat události myši, jako je například uvolnění levého tlačítka myši. Rutiny zpracování událostí pak mohou implementovat, přístupů testování vyvoláním <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody. Metody <xref:System.Windows.Media.HitTestResultCallback> parametr odkazuje na procedury definovaný uživatelem, který můžete použít k určení výsledné akce ověření pozice.  
  
 V následujícím příkladu je implementováno přístupů k testování podporu pro hostitelský objekt kontejneru a jeho podřízené položky.  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.DrawingVisual>  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Ověřování pozice ve vizuální vrstvě](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
