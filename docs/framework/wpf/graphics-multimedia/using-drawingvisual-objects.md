---
title: "Použití objektů DrawingVisual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ee46c41d6f0f42bbb9f50bd5862f6eb076b34bb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-drawingvisual-objects"></a>Použití objektů DrawingVisual
Toto téma obsahuje přehled o tom, jak používat <xref:System.Windows.Media.DrawingVisual> objekty v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual vrstvy.  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>Objekt DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> Představuje nenáročné, kreslení třídu, která se použije k vykreslení tvarů, Image nebo text. Tato třída se považuje za lightweight, protože neposkytuje rozložení nebo událostí zpracování, což zvyšuje jeho výkon. Z toho důvodu jsou ideální pro pozadí a vytvoříte čára.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>Kontejner DrawingVisual hostitele  
 Chcete-li použít <xref:System.Windows.Media.DrawingVisual> objekty, je nutné vytvořit kontejner hostitele pro objekty. Objekt kontejneru hostitele musí být odvozeny od <xref:System.Windows.FrameworkElement> třídy, která poskytuje, který podporuje rozložení a zpracování událostí <xref:System.Windows.Media.DrawingVisual> třídy chybí. Objekt kontejneru hostitele nezobrazuje žádné viditelné vlastnosti vzhledem k tomu, že jeho hlavním účelem je tak, aby obsahovala podřízené objekty. Ale <xref:System.Windows.UIElement.Visibility%2A> kontejneru hostitele musí být nastavena na <xref:System.Windows.Visibility.Visible>, jinak hodnota žádný z jejích podřízených elementů se nebude zobrazovat.  
  
 Když vytvoříte objekt kontejneru hostitele pro vizuální objekty, je třeba uložit vizuální objekt odkazy v <xref:System.Windows.Media.VisualCollection>. Použití <xref:System.Windows.Media.VisualCollection.Add%2A> metody přidat objekt visual ke kontejneru hostitele. V následujícím příkladu je vytvořen objekt kontejneru hostitele a tři vizuální objekty jsou přidány do jeho <xref:System.Windows.Media.VisualCollection>.  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  Ukázka dokončení kódu, ze kterého jste extrahovali v předchozím příkladu kódu, najdete v části [ukázka průchodu testu DrawingVisuals](http://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Vytváření objektů DrawingVisual  
 Při vytváření <xref:System.Windows.Media.DrawingVisual> objektu má žádné kreslení obsah. Text, grafiky nebo obsahu bitové kopie můžete přidat načtením objektu <xref:System.Windows.Media.DrawingContext> a kreslení do ní. A <xref:System.Windows.Media.DrawingContext> vrátí volání <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metodu <xref:System.Windows.Media.DrawingVisual> objektu.  
  
 Vytvořte obdélník do <xref:System.Windows.Media.DrawingContext>, použijte <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> metodu <xref:System.Windows.Media.DrawingContext> objektu. Existují podobné metody pro kreslení jiné typy obsahu. Po dokončení kreslení obsah do <xref:System.Windows.Media.DrawingContext>, volání <xref:System.Windows.Media.DrawingContext.Close%2A> metoda zavřete <xref:System.Windows.Media.DrawingContext> a zachovat obsah.  
  
 V následujícím příkladu <xref:System.Windows.Media.DrawingVisual> objekt se vytvoří a obdélníku vykreslením do jeho <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>Vytváření přepsání pro FrameworkElement členy  
 Objekt kontejneru hostitele je zodpovědný za správu jeho kolekce vizuální objekty. To vyžaduje, aby kontejneru hostitele implementovat člen přepsání odvozené <xref:System.Windows.FrameworkElement> třídy.  
  
 Následující seznam popisuje dva členy, které je nutné přepsat:  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Vrátí podřízené v zadaném indexu kolekce podřízených elementů.  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Získá číslo visual podřízených elementů v rámci tohoto elementu.  
  
 V následujícím příkladu jsou přepsání pro dva <xref:System.Windows.FrameworkElement> jsou implementované členy.  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>Zajištění podpory přístupů testování  
 Objekt kontejneru hostitele můžete zadat, událostí zpracování i v případě, že se nezobrazí žádné viditelné vlastnosti – však jeho <xref:System.Windows.UIElement.Visibility%2A> musí být nastavena na <xref:System.Windows.Visibility.Visible>. Můžete vytvořit událost zpracování rutiny pro hostitele kontejner, který můžete depeše události myši, jako je například verzi levé tlačítko. Rutiny zpracování událostí poté můžete implementovat, počtu testování vyvoláním <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda. Metody <xref:System.Windows.Media.HitTestResultCallback> parametr odkazuje na procedury definovaný uživatelem, která můžete použít k určení výsledné akce testu přístupů.  
  
 V následujícím příkladu se implementuje podle testování podporu pro objekt kontejneru hostitele a její podřízené položky.  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.DrawingVisual>  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Ve Visual vrstvě testování průchodu](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
