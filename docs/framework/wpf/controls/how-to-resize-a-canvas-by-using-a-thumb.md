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
ms.openlocfilehash: 84f5ac2b53124b7f4d7c15741e94b40e7ee81526
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124296"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Postupy: Změna velikosti plátna použitím jezdce
Tento příklad ukazuje, jak použít ovládací prvek <xref:System.Windows.Controls.Primitives.Thumb> pro změnu velikosti ovládacího prvku <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Příklad  
 Ovládací prvek <xref:System.Windows.Controls.Primitives.Thumb> poskytuje funkce přetažení, které lze použít k přesunutí nebo změně velikosti ovládacích prvků monitorováním <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> a <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> událostí <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Uživatel zahájí operaci přetažení stisknutím levého tlačítka myši, když je ukazatel myši pozastaven na ovládacím prvku <xref:System.Windows.Controls.Primitives.Thumb>. Operace přetažení bude pokračovat, dokud nebude stisknuto levé tlačítko myši. Během operace přetažení může <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> probíhat více než jednou. Pokaždé, když k tomu dojde, třída <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> poskytuje změnu pozice, která odpovídá změně pozice myši. Když uživatel uvolní levé tlačítko myši, operace přetažení se dokončí. Operace přetažení poskytuje pouze nové souřadnice; nemění automaticky umístění <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb> ovládací prvek, který je podřízeným prvkem <xref:System.Windows.Controls.Canvas> ovládacího prvku. Obslužná rutina události pro událost <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> poskytuje logiku pro přesunutí <xref:System.Windows.Controls.Primitives.Thumb> a změnu velikosti <xref:System.Windows.Controls.Canvas>. Obslužné rutiny události pro událost <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> a <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> mění barvu <xref:System.Windows.Controls.Primitives.Thumb> během operace přetažení. Následující příklad definuje <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> obslužnou rutinu události, která přesouvá <xref:System.Windows.Controls.Primitives.Thumb> a mění velikost <xref:System.Windows.Controls.Canvas> v reakci na pohyb myši.  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 Následující příklad ukazuje obslužnou rutinu události <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>.  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 Následující příklad ukazuje obslužnou rutinu události <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>.  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Úplnou ukázku najdete v tématu [Ukázka funkcionality přetažení jezdce](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
