---
title: 'Postupy: Změna velikosti plátna použitím jezdce'
ms.date: 03/30/2017
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
ms.openlocfilehash: 14942157429b029147d47e2f88428c56e66523d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770744"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Postupy: Změna velikosti plátna použitím jezdce
Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.Primitives.Thumb> ovládací prvek pro změnu velikosti <xref:System.Windows.Controls.Canvas> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.Primitives.Thumb> Ovládacího prvku poskytuje funkce přetažení, kterého chcete přesunout nebo změna velikosti ovládacích prvků při sledování <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> a <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> události <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Uživatel začne operace přetažení. stisknutím klávesy levé tlačítko myši při umístění ukazatele myši je pozastaven na <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku. Operace přetažení pokračuje tak dlouho, dokud zůstává levé tlačítko myši stisknuté. Během operace přetažení <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> mohou vyskytovat více než jednou. Pokaždé, když k ní dojde, <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> třída poskytuje změn v pozici, která odpovídá změně pozice myši. Když uživatel uvolní levé tlačítko myši, dokončení operace přetažení. Operace přetažení pouze poskytuje nové souřadnice; nepřemístí automaticky <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb> prvek, který je podřízený prvek <xref:System.Windows.Controls.Canvas> ovládacího prvku. Obslužnou rutinu události pro jeho <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> událostí obsahuje logiku a přesunout <xref:System.Windows.Controls.Primitives.Thumb> a změňte jeho velikost <xref:System.Windows.Controls.Canvas>. Obslužné rutiny událostí pro <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> a <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> události změnit barvu <xref:System.Windows.Controls.Primitives.Thumb> během operace přetažení. Následující příklad definuje <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> obslužná rutina události, který přesouvá <xref:System.Windows.Controls.Primitives.Thumb> a změní velikost <xref:System.Windows.Controls.Canvas> v reakci na pohybu myši.  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> obslužné rutiny události.  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> obslužné rutiny události.  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Úplnou ukázku najdete v tématu [ukázkové funkce přetáhněte Thumb](https://go.microsoft.com/fwlink/?LinkID=160042).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
