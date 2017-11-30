---
title: "Postupy: Výběr inkoustu pomocí vlastního ovládacího prvku"
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
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd9693209cc35ecd3c0473133b7c21639a239ff5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-select-ink-from-a-custom-control"></a>Postupy: Výběr inkoustu pomocí vlastního ovládacího prvku
Přidáním <xref:System.Windows.Ink.IncrementalLassoHitTester> do vlastního ovládacího prvku, můžete povolit vlastního ovládacího prvku tak, aby uživatel může vybrat rukopisu s nástrojem laso, podobně jako <xref:System.Windows.Controls.InkCanvas> vybere rukopisu s nepravidelné oblasti.  
  
 Tento příklad předpokládá, že jste obeznámeni s vytvoření vlastního ovládacího prvku rukopisu povolena.  Pokud chcete vytvořit vlastní ovládací prvek, který přijímá vstup rukopisu, najdete v části [vytváření rukopisu vstupního ovládacího prvku](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  
  
## <a name="example"></a>Příklad  
 Když uživatel nakreslí nepravidelné oblasti, <xref:System.Windows.Ink.IncrementalLassoHitTester> předpovídá, které tahy bude v rámci hranice laso cesta po dokončení laso uživatele.  Tahy, která jsou určena jako v rámci hranice laso cestu můžete představit jako vybraná.  Vybrané tahy se může stát také nezaškrtnuté.  Pokud uživatel otočí směr při vykreslování laso, například <xref:System.Windows.Ink.IncrementalLassoHitTester> může zrušit výběr některé tahy.  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester> Vyvolá <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> událost, která umožňuje vlastního ovládacího prvku reagovat, když uživatel je kreslení laso.  Můžete například změnit vzhled tahy, se uživatel vybere a zruší výběr nakresleného je.  
  
## <a name="managing-the-ink-mode"></a>Správa režimu rukopisu  
 Je užitečné pro uživatele Pokud jinak než rukopisu ve vlastní ovládací prvek se zobrazuje laso. K tomu, vlastní ovládací prvek musí udržovat přehled o zda uživatel je zápis nebo výběr rukopisu. Nejjednodušším způsobem je deklarace výčtů se dvěma hodnotami: jeden k označení, že uživatel je zápis rukopisu a jeden, který označuje, že uživatel je výběr rukopisu.  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 Dál přidejte dva <xref:System.Windows.Ink.DrawingAttributes> pro třídu: jednu použijte, pokud uživatel zapíše rukopisu, jednu pro použijte, pokud uživatel vybere rukopisu.  V konstruktoru, inicializovat <xref:System.Windows.Ink.DrawingAttributes> a připojte oba <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> události, které mají stejné obslužné rutiny události. Nastavte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> vlastnost <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> k rukopisu <xref:System.Windows.Ink.DrawingAttributes>.  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 Přidáte vlastnost, která zveřejňuje režim výběru. Když uživatel změní režim výběru, nastavte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> vlastnost <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> na příslušné <xref:System.Windows.Ink.DrawingAttributes> objektu a znovu připojte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> vlastnost, která má <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 Vystavení <xref:System.Windows.Ink.DrawingAttributes> jako vlastnosti, takže aplikace můžete určit vzhled tahy a výběr tahy.  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 Pokud vlastnost <xref:System.Windows.Ink.DrawingAttributes> objektu změny, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> musí být znovu připojit ke <xref:System.Windows.Controls.InkPresenter>.  V obslužné rutiny události pro <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> událostí, připojte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> k <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>Pomocí IncrementalLassoHitTester  
 Vytvoření a inicializace <xref:System.Windows.Ink.StrokeCollection> obsahující vybrané tahy.  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 Když uživatel spustí kreslení tahu, barvou nebo laso, zrušte výběr všechny vybrané tahy. Poté, pokud uživatel je kreslení nepravidelné oblasti, vytvořte <xref:System.Windows.Ink.IncrementalLassoHitTester> voláním <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, přihlášení k odběru <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> událostí a volání <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>. Tento kód může být samostatné metodě a volat z <xref:System.Windows.UIElement.OnStylusDown%2A> a <xref:System.Windows.UIElement.OnMouseDown%2A> metody.  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 Přidání bodů pera k <xref:System.Windows.Ink.IncrementalLassoHitTester> při uživatele nevykresluje laso.  Volejte metodu z <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, a <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> metody.  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 Zpracování <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> událostí reagovat, když uživatel vybere a zruší výběr nakresleného tahy.  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> Třída má <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> a <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> vlastnosti, které získají tahy, které byly vybrány a zrušit, v uvedeném pořadí.  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 Po dokončení kreslení laso uživatele odhlášení odběru <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> událostí a volání <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>Všechny připravuje umístění.  
 V následujícím příkladu je vlastní ovládací prvek, který umožňuje uživateli vybrat rukopisu s nepravidelné oblasti.  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>  
 <xref:System.Windows.Ink.StrokeCollection>  
 <xref:System.Windows.Input.StylusPointCollection>  
 [Vytváření rukopisu vstupního ovládacího prvku](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
