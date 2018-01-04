---
title: "Postupy: Změna velikosti plátna použitím jezdce"
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
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c73509d58112e47f707e82243005bfdf9edca151
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Postupy: Změna velikosti plátna použitím jezdce
Tento příklad ukazuje, jak používat <xref:System.Windows.Controls.Primitives.Thumb> řízení ke změně velikosti <xref:System.Windows.Controls.Canvas> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.Primitives.Thumb> Řízení poskytuje přetažení funkce, které slouží k přesunutí nebo změna velikosti ovládacích prvků pomocí monitorování <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> a <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> události <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Uživatel začne operaci přetažení stisknutím levé tlačítko myši, když ukazatel myši je pozastaven na <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku. Operaci přetažení pokračuje tak dlouho, dokud zůstává levé tlačítko myši stisknuté. Během operace tažení <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> může dojít, více než jednou. Pokaždé, když k ní dojde, <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> třída poskytuje změnu v hodnotě pozice, který odpovídá změnu v pozici myši. Když uživatel uvolní levé tlačítko myši, dokončení operace přetažení. Operaci přetažení pouze poskytuje nové souřadnice; není automaticky přemístit <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb> prvek, který je o podřízený prvek <xref:System.Windows.Controls.Canvas> ovládacího prvku. Obslužné rutiny události pro jeho <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> událostí obsahuje logiku pro přesun <xref:System.Windows.Controls.Primitives.Thumb> a změňte velikost <xref:System.Windows.Controls.Canvas>. Obslužné rutiny událostí <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> a <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> událostí Změna barvy <xref:System.Windows.Controls.Primitives.Thumb> během operace přetažení. V následujícím příkladu je definován <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xaml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> obslužné rutiny události, která přemísťuje <xref:System.Windows.Controls.Primitives.Thumb> a změní <xref:System.Windows.Controls.Canvas> v reakci na pohybu myši.  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> obslužné rutiny události.  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> obslužné rutiny události.  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Kompletní příklad, najdete v části [jezdec přetažení funkce ukázka](http://go.microsoft.com/fwlink/?LinkID=160042).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Primitives.Thumb>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
