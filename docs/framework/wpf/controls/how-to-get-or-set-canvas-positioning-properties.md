---
title: 'Postupy: Získání nebo nastavení vlastností umístění plátna'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
ms.openlocfilehash: 06508e1198736ccb1cbda41641dff4bc634ef82b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910478"
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a>Postupy: Získání nebo nastavení vlastností umístění plátna
Tento příklad ukazuje způsob použití metod pro posunutí umístění <xref:System.Windows.Controls.Canvas> element na pozici podřízený obsah. Tento příklad používá obsah <xref:System.Windows.Controls.ListBoxItem> představující umístění hodnoty a převádí hodnoty instance <xref:System.Double>, což je povinný argument pro umístění. Hodnoty jsou poté převeden zpět do řetězce a zobrazí jako text v <xref:System.Windows.Controls.TextBlock> elementu s použitím <xref:System.Windows.Controls.Canvas.GetLeft%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Windows.Controls.ListBox> element, který má jedenáct volitelných <xref:System.Windows.Controls.ListBoxItem> elementy. <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Aktivačních procedur událostí `ChangeLeft` vlastní metodu, která definuje následující kód bloku.  
  
 Každý <xref:System.Windows.Controls.ListBoxItem> představuje <xref:System.Double> hodnotu, která je jeden z argumentů, který <xref:System.Windows.Controls.Canvas.SetLeft%2A> metodu <xref:System.Windows.Controls.Canvas> přijímá. Aby bylo možné používat <xref:System.Windows.Controls.ListBoxItem> k reprezentaci instance <xref:System.Double>, je nutné nejprve převést <xref:System.Windows.Controls.ListBoxItem> do správného datového typu.  
  
 [!code-xaml[CanvasPositioningProperties#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 Když uživatel změní <xref:System.Windows.Controls.ListBox> výběr, vyvolá `ChangeLeft` vlastní metodu. Tato metoda předává <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.LengthConverter> objekt, který převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> k instanci <xref:System.Double> (Všimněte si, že tato hodnota již byl převeden na <xref:System.String> pomocí <xref:System.Windows.Controls.Control.ToString%2A> Metoda). Tato hodnota je pak předán zpět <xref:System.Windows.Controls.Canvas.SetLeft%2A> a <xref:System.Windows.Controls.Canvas.GetLeft%2A> metody <xref:System.Windows.Controls.Canvas> Chcete-li změnit umístění `text1` objektu.  
  
 [!code-csharp[CanvasPositioningProperties#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.ListBoxItem>
- <xref:System.Windows.LengthConverter>
- [Přehled panelu](panels-overview.md)
