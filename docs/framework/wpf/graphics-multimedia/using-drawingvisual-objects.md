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
ms.openlocfilehash: 4e6fc89b64f7b0acc1a0077708d567eb97e2868e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962833"
---
# <a name="using-drawingvisual-objects"></a>Použití objektů DrawingVisual
Toto téma poskytuje přehled o tom, jak používat <xref:System.Windows.Media.DrawingVisual> objekty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve vizuální vrstvě.  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>Objekt DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> Je zjednodušená třída pro kreslení, která se používá k vykreslování tvarů, obrázků nebo textu. Tato třída je považována za odlehčenou, protože neposkytuje rozložení nebo zpracování událostí, což zvyšuje výkon. Z tohoto důvodu jsou kresby ideální pro pozadí a kliparty.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual Host Container  
 Aby bylo možné použít <xref:System.Windows.Media.DrawingVisual> objekty, je nutné vytvořit kontejner hostitele pro objekty. Kontejnerový objekt hostitele musí být odvozen od <xref:System.Windows.FrameworkElement> třídy, která poskytuje podporu pro rozložení a zpracování událostí <xref:System.Windows.Media.DrawingVisual> , že třída chybí. Objekt kontejneru hostitele nezobrazí žádné viditelné vlastnosti, protože jeho hlavní účel je obsahovat podřízené objekty. Vlastnost kontejneru hostitele však musí být nastavena na <xref:System.Windows.Visibility.Visible>hodnotu; v opačném případě nebude žádný z jejích podřízených elementů viditelný. <xref:System.Windows.UIElement.Visibility%2A>  
  
 Když vytvoříte kontejnerový objekt hostitele pro vizuální objekty, je nutné uložit odkazy na vizuální objekty v <xref:System.Windows.Media.VisualCollection>. <xref:System.Windows.Media.VisualCollection.Add%2A> Použijte metodu pro přidání vizuálního objektu do kontejneru hostitele. V následujícím příkladu je vytvořen kontejnerový objekt hostitele a do něj <xref:System.Windows.Media.VisualCollection>jsou přidány tři vizuální objekty.  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> Kompletní vzorek kódu, ze kterého byl extrahován předchozí příklad kódu, naleznete v tématu [test volání pomocí DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Vytváření objektů DrawingVisual  
 Při vytváření <xref:System.Windows.Media.DrawingVisual> objektu nemá žádný obsah kresby. Můžete přidat text, grafiku nebo obrázkový obsah načtením objektu <xref:System.Windows.Media.DrawingContext> a jeho vykreslováním do něj. Objekt je vrácen <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> voláním metody <xref:System.Windows.Media.DrawingVisual> objektu. <xref:System.Windows.Media.DrawingContext>  
  
 Chcete-li nakreslit obdélník <xref:System.Windows.Media.DrawingContext>do, <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> použijte metodu <xref:System.Windows.Media.DrawingContext> objektu. Podobné metody existují pro kreslení dalších typů obsahu. Až dokončíte vykreslování obsahu do rozhraní <xref:System.Windows.Media.DrawingContext>, <xref:System.Windows.Media.DrawingContext.Close%2A> zavolejte metodu pro zavření <xref:System.Windows.Media.DrawingContext> a zachování obsahu.  
  
 V následujícím příkladu <xref:System.Windows.Media.DrawingVisual> je vytvořen objekt a obdélník je vykreslen do jeho <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>Vytváření přepsání pro členy FrameworkElement  
 Objekt kontejneru hostitele je zodpovědný za správu kolekce vizuálních objektů. To vyžaduje, aby kontejner hostitele implementoval přepsání členů pro odvozenou <xref:System.Windows.FrameworkElement> třídu.  
  
 Následující seznam popisuje dva členy, které je nutné přepsat:  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Vrátí podřízenou položku v zadaném indexu z kolekce podřízených elementů.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Získá počet vizuálních podřízených elementů v rámci tohoto elementu.  
  
 V následujícím příkladu jsou implementovány přepsání pro dva <xref:System.Windows.FrameworkElement> členy.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>Poskytování podpory testování přístupů  
 Kontejnerový objekt hostitele může poskytovat zpracování událostí i v případě, že se nezobrazí žádné viditelné vlastnosti, ale jeho <xref:System.Windows.UIElement.Visibility%2A> vlastnost musí být nastavena na <xref:System.Windows.Visibility.Visible>. To vám umožní vytvořit rutinu zpracování událostí pro kontejner hostitele, který může zachytávat události myši, jako je například verze levého tlačítka myši. Rutina zpracování událostí pak může implementovat testování přístupů vyvoláním <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody. <xref:System.Windows.Media.HitTestResultCallback> Parametr metody odkazuje na uživatelsky definovaný postup, který můžete použít k určení výsledné akce testu přístupů.  
  
 V následujícím příkladu je podpora testování přístupů implementována pro objekt kontejneru hostitele a jeho podřízené objekty.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
