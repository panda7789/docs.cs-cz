---
title: 'Postupy: Umístění podřízených elementů mřížky'
description: Naučte se používat metody Get a set, které jsou definovány v Windows Presentation Foundation mřížce k umístění podřízených elementů.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 926d223097dd21dd0292c9523903b4be8aba8ba9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167394"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Postupy: Umístění podřízených elementů mřížky
Tento příklad ukazuje, jak použít metody Get a set, které jsou definovány <xref:System.Windows.Controls.Grid> pro k umístění podřízených elementů.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje nadřazený <xref:System.Windows.Controls.Grid> element ( `grid1` ), který má tři sloupce a tři řádky. Podřízený <xref:System.Windows.Shapes.Rectangle> prvek ( `rect1` ) je přidán do <xref:System.Windows.Controls.Grid> pozice sloupce nula, pozice řádku je nula. <xref:System.Windows.Controls.Button>prvky reprezentují metody, které lze volat pro změnu umístění <xref:System.Windows.Shapes.Rectangle> elementu v rámci <xref:System.Windows.Controls.Grid> . Když uživatel klikne na tlačítko, je aktivována související metoda.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 Následující příklad kódu zpracovává metody, které <xref:System.Windows.Controls.Primitives.ButtonBase.Click> vyvolají události tlačítka. Tento příklad zapíše volání těchto metod do <xref:System.Windows.Controls.TextBlock> prvků, které používají související metody get pro výstup nových hodnot vlastností jako řetězců.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 Tady je konečný výsledek.

 ![snímek obrazovky znázorňuje uživatelské rozhraní WPF se dvěma sloupci, pravá strana má 3 x 3 mřížky a vlevo obsahuje tlačítka pro přesunutí barevného obdélníku mezi sloupci a řádky mřížky.](././media/grid-methods-sample.png)
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Grid>
- [Přehled panelů](panels-overview.md)
