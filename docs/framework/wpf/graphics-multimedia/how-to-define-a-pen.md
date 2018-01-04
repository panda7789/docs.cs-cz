---
title: 'Postupy: Definice pera'
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
- pens [WPF], defining
- creating [WPF], pens
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02a3bef369f5bdd70588f3934e4199d7d4c703f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-pen"></a>Postupy: Definice pera
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Pen> se vymezí obrazce. Chcete-li vytvořit jednoduchou <xref:System.Windows.Media.Pen>, je nutné jenom zadat jeho <xref:System.Windows.Media.Pen.Thickness%2A> a <xref:System.Windows.Media.Pen.Brush%2A>. Je-li vytvořit složitější pera zadáním <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A>, a <xref:System.Windows.Media.Pen.EndLineCap%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Pen> se vymezí obrazce definované <xref:System.Windows.Media.GeometryDrawing>.  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 ![Obsahuje přehled vytváří pomocí pera](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")  
Objekt GeometryDrawing sestávající
