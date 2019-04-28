---
title: 'Postupy: Výběr rukopisu pomocí vlastního ovládacího prvku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
ms.openlocfilehash: 5c9b2f3d64e4cbb309772d6a1d9fa88f589df84c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768396"
---
# <a name="how-to-select-ink-from-a-custom-control"></a>Postupy: Výběr rukopisu pomocí vlastního ovládacího prvku
Tak, že přidáte <xref:System.Windows.Ink.IncrementalLassoHitTester> do vlastního ovládacího prvku, můžete povolit ovládacího prvku tak, aby uživatel může vybrat inkoustu pomocí nástroje laso, podobně jako <xref:System.Windows.Controls.InkCanvas> výběr inkoustu pomocí nepravidelné oblasti.  
  
 Tento příklad předpokládá, že máte zkušenosti s vytvářením vlastní ovládací prvek inkoustu povolena.  Vytvoření vlastního ovládacího prvku, který přijímá vstup rukopisu, najdete v tématu [vytvoření ovládacího prvku vstupu inkoustu](creating-an-ink-input-control.md).  
  
## <a name="example"></a>Příklad  
 Když uživatel nakreslí nepravidelné oblasti, <xref:System.Windows.Ink.IncrementalLassoHitTester> předpovídá, které tahy bude v rámci hranice laso cesty, až uživatel vykoná laso.  Strokes, které jsou určeny za hranice laso cesty můžete představit jako vybraná.  Zároveň může stát nevybrané vybraných tahů.  Pokud uživatel změní směr při kreslení laso, například <xref:System.Windows.Ink.IncrementalLassoHitTester> může zrušit některá tahů.  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester> Vyvolá <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> událost, která umožňuje reagovat, když uživatel je vykreslení laso vlastního ovládacího prvku.  Můžete například změnit vzhled tahy a uživatel vybere zruší výběr nakresleného je.  
  
## <a name="managing-the-ink-mode"></a>Správa režimu inkoustu  
 Je pro uživatele užitečné, pokud se zobrazí laso jinak než inkoustu ovládacího prvku. K dosažení tohoto vlastního ovládacího prvku musí udržovat přehled o, zda uživatel je psaní nebo výběr rukopisu. Nejjednodušší způsob je deklarovat výčet pomocí dvou hodnot: jednu k označení, že uživatel píše inkoustu a druhý k označení, že uživatel je výběr rukopisu.  
  
 [!code-csharp[HowToSelectInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 V dalším kroku přidejte dva <xref:System.Windows.Ink.DrawingAttributes> do třídy: jednu použijte, pokud uživatel zapíše rukopisu, z nich se má použít, když uživatel vybere rukopisu.  V konstruktoru, inicializovat <xref:System.Windows.Ink.DrawingAttributes> a oba připojit <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> události, které mají stejný ovladač událostí. Nastavte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> vlastnost <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> inkoustu <xref:System.Windows.Ink.DrawingAttributes>.  
  
 [!code-csharp[HowToSelectInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 Přidáte vlastnost, která zpřístupní režim výběru. Když uživatel změní režim výběru, nastavte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> vlastnost <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> na příslušné <xref:System.Windows.Ink.DrawingAttributes> objektu a pak znovu připojit <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> vlastnost <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#5](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 Zveřejnit <xref:System.Windows.Ink.DrawingAttributes> jako vlastnosti tak, že aplikace může určit vzhled inkoustových tahů a výběr tahů.  
  
 [!code-csharp[HowToSelectInk#6](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 Pokud vlastnost <xref:System.Windows.Ink.DrawingAttributes> objektem, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> musí být znovu připojit k <xref:System.Windows.Controls.InkPresenter>.  V obslužné rutině události pro <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> událost, znovu připojit <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> k <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#7](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>Použití IncrementalLassoHitTester  
 Vytváření a inicializace <xref:System.Windows.Ink.StrokeCollection> , který obsahuje vybraných tahů.  
  
 [!code-csharp[HowToSelectInk#8](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 Když uživatel začne kreslit tah, ink nebo laso, zrušte výběr všech vybraných tahů. Potom, pokud uživatel je kreslení nepravidelné oblasti, vytvořte <xref:System.Windows.Ink.IncrementalLassoHitTester> voláním <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, přihlaste se k odběru <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> událostí a volání <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>. Tento kód může být samostatné metodě a volat z <xref:System.Windows.UIElement.OnStylusDown%2A> a <xref:System.Windows.UIElement.OnMouseDown%2A> metody.  
  
 [!code-csharp[HowToSelectInk#9](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 Přidat body stylus k <xref:System.Windows.Ink.IncrementalLassoHitTester> zatímco uživatel nakreslí laso.  Toto volání z <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, a <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> metody.  
  
 [!code-csharp[HowToSelectInk#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 Zpracování <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> události reagovat, když uživatel vybere a zruší výběr nakresleného tahů.  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> Třída nemá <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> a <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> vlastnosti, které získávají strokes, které byly vybrané a zrušení výběru, v uvedeném pořadí.  
  
 [!code-csharp[HowToSelectInk#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 Po dokončení vykreslení laso uživatel zrušit odběr <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> událostí a volání <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.  
  
 [!code-csharp[HowToSelectInk#12](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>Vložení všechny najednou.  
 Následující příklad je vlastní ovládací prvek, který umožňuje uživateli výběr inkoustu pomocí nepravidelné oblasti.  
  
 [!code-csharp[HowToSelectInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Ink.IncrementalLassoHitTester>
- <xref:System.Windows.Ink.StrokeCollection>
- <xref:System.Windows.Input.StylusPointCollection>
- [Vytvoření ovládacího prvku vstupu rukopisu](creating-an-ink-input-control.md)
