---
title: 'Postupy: Určení, zda datový objekt obsahuje formát dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
ms.openlocfilehash: e3e2f47df0ae1fdf0fe875827473f2c3a1b53fb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a>Postupy: Určení, zda datový objekt obsahuje formát dat
Následující příklady ukazují, jak používat různé <xref:System.Windows.DataObject.GetDataPresent%2A> přetížení metody pro dotaz, zda formát konkrétní dat se nachází v datovém objektu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> přetížení pro dotaz na přítomnost konkrétní datové formát řetězce popisovače.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> přetížení pro dotaz na přítomnost formát konkrétní dat podle typu.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> přetížení pro dotaz na data pomocí řetězce popisovače a určení způsobu zpracování formáty dat převoditelné automaticky.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.IDataObject>
