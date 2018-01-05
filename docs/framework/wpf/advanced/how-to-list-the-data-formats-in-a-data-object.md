---
title: "Postupy: Seznam datových formátů v datovém objektu"
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
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb27928031b551da2957aab0696646e8adc3f803
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a>Postupy: Seznam datových formátů v datovém objektu
Následující příklady ukazují, jak používat <xref:System.Windows.DataObject.GetFormats%2A> přetížení metody get pole řetězce představující každý data formátu, který je k dispozici v datovém objektu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu používá <xref:System.Windows.DataObject.GetFormats%2A> přetížení získat pole řetězců, které označuje všechny formáty dat v datovém objektu (nativní a automaticky převoditelné) k dispozici.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu používá <xref:System.Windows.DataObject.GetFormats%2A> přetížení získat pole řetězců, které označuje pouze formáty dat v datovém objektu (převoditelné automaticky data jsou filtrovány formáty) k dispozici.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.IDataObject>  
 [Přehled přetažení](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
