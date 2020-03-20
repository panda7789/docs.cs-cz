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
ms.openlocfilehash: 9d67fbc0d9716c9df3935232c6c7e579b50d55bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148319"
---
# <a name="using-drawingvisual-objects"></a>Použití objektů DrawingVisual
Toto téma obsahuje přehled <xref:System.Windows.Media.DrawingVisual> o tom, jak používat objekty ve vizuální vrstvě. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
<a name="drawingvisual_object"></a>
## <a name="drawingvisual-object"></a>Objekt DrawingVisual  
 Jedná <xref:System.Windows.Media.DrawingVisual> se o zjednodušenou třídu výkresu, která slouží k vykreslení obrazců, obrázků nebo textu. Tato třída je považována za zjednodušenou, protože neposkytuje rozložení nebo zpracování událostí, což zlepšuje jeho výkon. Z tohoto důvodu jsou kresby ideální pro pozadí a kliparty.  
  
<a name="drawingvisual_host_container"></a>
## <a name="drawingvisual-host-container"></a>Kontejner hostitele výkresu  
 Chcete-li <xref:System.Windows.Media.DrawingVisual> použít objekty, musíte vytvořit hostitelský kontejner pro objekty. Objekt kontejneru hostitele musí <xref:System.Windows.FrameworkElement> být odvozen z třídy, která <xref:System.Windows.Media.DrawingVisual> poskytuje podporu rozložení a zpracování událostí, které třída postrádá. Objekt kontejneru hostitele nezobrazuje žádné viditelné vlastnosti, protože jeho hlavním účelem je obsahovat podřízené objekty. <xref:System.Windows.UIElement.Visibility%2A> Vlastnost hostitelského kontejneru však musí <xref:System.Windows.Visibility.Visible>být nastavena na ; v opačném případě nebude zobrazen žádný z podřízených prvků.  
  
 Při vytváření objektu kontejneru hostitele pro vizuální objekty je třeba <xref:System.Windows.Media.VisualCollection>uložit odkazy na vizuální objekty v . Pomocí <xref:System.Windows.Media.VisualCollection.Add%2A> metody můžete přidat vizuální objekt do hostitelského kontejneru. V následujícím příkladu je vytvořen objekt kontejneru hostitele a <xref:System.Windows.Media.VisualCollection>tři vizuální objekty jsou přidány do jeho .  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> Pro kompletní ukázku kódu, ze kterého byl extrahován předchozí příklad kódu, naleznete [v tématu Hit Test Using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).  
  
<a name="creating_drawingvisual_objects"></a>
## <a name="creating-drawingvisual-objects"></a>Vytváření objektů DrawingVisual  
 Když vytvoříte <xref:System.Windows.Media.DrawingVisual> objekt, nemá žádný obsah výkresu. Obsah textu, grafiky nebo obrázku můžete přidat <xref:System.Windows.Media.DrawingContext> tak, že načtete objekt a nakreslíte do něj. A <xref:System.Windows.Media.DrawingContext> je vrácena <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> voláním <xref:System.Windows.Media.DrawingVisual> metody objektu.  
  
 Chcete-li nakreslit <xref:System.Windows.Media.DrawingContext>obdélník <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> do , <xref:System.Windows.Media.DrawingContext> použijte metodu objektu. Podobné metody existují pro kreslení jiných typů obsahu. Po dokončení kreslení obsahu do <xref:System.Windows.Media.DrawingContext>, <xref:System.Windows.Media.DrawingContext.Close%2A> volání metody <xref:System.Windows.Media.DrawingContext> zavřít a zachovat obsah.  
  
 V následujícím příkladu <xref:System.Windows.Media.DrawingVisual> je vytvořen objekt a obdélník <xref:System.Windows.Media.DrawingContext>je nakreslena do jeho .  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>
## <a name="creating-overrides-for-frameworkelement-members"></a>Vytváření lokálních kontrol pro členy prvku FrameworkElement  
 Objekt kontejneru hostitele je zodpovědný za správu jeho kolekce vizuálníobjekty. To vyžaduje, aby hostitelský kontejner implementovat <xref:System.Windows.FrameworkElement> člen přepíše pro odvozené třídy.  
  
 Následující seznam popisuje dva členy, které je nutné přepsat:  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Vrátí podřízenou položku v zadaném indexu z kolekce podřízených prvků.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Získá počet vizuální podřízené prvky v rámci tohoto prvku.  
  
 V následujícím příkladu jsou implementovány lokální změny pro dva <xref:System.Windows.FrameworkElement> členy.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>
## <a name="providing-hit-testing-support"></a>Poskytování podpory testování přístupů  
 Objekt kontejneru hostitele může poskytnout zpracování událostí i v případě, <xref:System.Windows.UIElement.Visibility%2A> že nezobrazuje <xref:System.Windows.Visibility.Visible>žádné viditelné vlastnosti – jeho vlastnost však musí být nastavena na . To umožňuje vytvořit rutinu zpracování událostí pro kontejner hostitele, který může vytvořit soutisk událostí myši, jako je například uvolnění levého tlačítka myši. Rutina zpracování událostí pak můžete implementovat testování <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> přístupů vyvoláním metody. <xref:System.Windows.Media.HitTestResultCallback> Parametr metody odkazuje na uživatelem definovaný postup, který můžete použít k určení výsledné akce testu přístupů.  
  
 V následujícím příkladu je implementována podpora testování přístupů pro objekt kontejneru hostitele a jeho podřízené objekty.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
