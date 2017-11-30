---
title: "Postupy: Umístění podřízených elementů mřížky"
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
helpviewer_keywords: Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dbe0bcb5d3c46edcb97410e00832f1b9d6205b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Postupy: Umístění podřízených elementů mřížky
Tento příklad ukazuje, jak používat get a nastavit metody, které jsou definovány na <xref:System.Windows.Controls.Grid> na pozici podřízené elementy.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje nadřazený <xref:System.Windows.Controls.Grid> – element (`grid1`), má tři sloupce a tři řádky. Podřízenou <xref:System.Windows.Shapes.Rectangle> element (`rect1`) je přidán do <xref:System.Windows.Controls.Grid> v pozici sloupce nula, řádek pozice nula. <xref:System.Windows.Controls.Button>elementy reprezentují metody, které lze volat pro změnu umístění <xref:System.Windows.Shapes.Rectangle> v rámci <xref:System.Windows.Controls.Grid>. Když uživatel klikne na tlačítko, je aktivována související metody.  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 Následující příklad kódu zpracovává metody, tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> vyvolat události. V příkladu je zapsán těchto volání metody <xref:System.Windows.Controls.TextBlock> prvky, které používá související získat metody pro výstup nové hodnoty vlastností jako řetězce.  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Grid>  
 [Přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md)
