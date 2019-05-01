---
title: 'Postupy: Definice pera'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [WPF], defining
- creating [WPF], pens
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
ms.openlocfilehash: 1d69a40604dbf2f7a73c17279ae946faeb6c634a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965387"
---
# <a name="how-to-define-a-pen"></a>Postupy: Definice pera
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Pen> pro vytváření obrysových obrazce. Chcete-li vytvořit jednoduchou <xref:System.Windows.Media.Pen>, stačí jen zadat jeho <xref:System.Windows.Media.Pen.Thickness%2A> a <xref:System.Windows.Media.Pen.Brush%2A>. Můžete vytvářet složitější pera určením <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A>, a <xref:System.Windows.Media.Pen.EndLineCap%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Pen> pro vytváření obrysových obrazce definované <xref:System.Windows.Media.GeometryDrawing>.  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 ![Jsou podrobněji popsány dále produkuje pomocí pera](./media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")  
GeometryDrawing
