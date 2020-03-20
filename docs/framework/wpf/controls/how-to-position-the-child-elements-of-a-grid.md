---
title: 'Postupy: Umístění podřízených elementů mřížky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 44268c32732a9409ea30f028adaa8a2631a06c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186724"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Postupy: Umístění podřízených elementů mřížky
Tento příklad ukazuje, jak používat get a <xref:System.Windows.Controls.Grid> set metody, které jsou definovány na umístění podřízených prvků.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje nadřazený <xref:System.Windows.Controls.Grid> prvek (`grid1`), který má tři sloupce a tři řádky. Podřízený <xref:System.Windows.Shapes.Rectangle> prvek`rect1`( ) <xref:System.Windows.Controls.Grid> je přidán do pozice ve sloupci nula, pozice řádku nula. <xref:System.Windows.Controls.Button>prvky představují metody, které lze <xref:System.Windows.Shapes.Rectangle> volat <xref:System.Windows.Controls.Grid>ke přemístění prvku v rámci . Když uživatel klepne na tlačítko, aktivuje se související metoda.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 Následující příklad na pozadí kódu zpracovává metody, které vyvolat události tlačítka. <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Příklad zapisuje <xref:System.Windows.Controls.TextBlock> tyto metody volání prvků, které používají související get metody k výstupu nové hodnoty vlastností jako řetězce.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 Zde je hotový výsledek!

 ![snímek obrazovky znázorňuje uživatelské rozhraní WPF se dvěma sloupci, pravá strana má mřížku 3 x 3 a vlevo má tlačítka pro pohyb barevného obdélníku mezi sloupci a řádky mřížky](././media/grid-methods-sample.png)
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Grid>
- [Přehled panelu](panels-overview.md)
