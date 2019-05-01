---
title: 'Postupy: Uložení několika datových formátů do datového objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], storing multiple formats
- DataFormats class [WPF], storing multiple formats
- drag-and-drop [WPF], storing multiple formats
ms.assetid: 941ace29-29c4-4c26-b75b-ea7d06aa0d69
ms.openlocfilehash: 3f8e7233e1d28fec1f7dac114b04287aa3aff49f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052375"
---
# <a name="how-to-store-multiple-data-formats-in-a-data-object"></a><span data-ttu-id="5f3c1-102">Postupy: Uložení několika datových formátů do datového objektu</span><span class="sxs-lookup"><span data-stu-id="5f3c1-102">How to: Store Multiple Data Formats in a Data Object</span></span>
<span data-ttu-id="5f3c1-103">Následující příklad ukazuje způsob použití <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> metoda pro přidání dat na datový objekt v různých formátech.</span><span class="sxs-lookup"><span data-stu-id="5f3c1-103">The following example shows how to use the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> method to add data to a data object in multiple formats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f3c1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f3c1-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5f3c1-105">Popis</span><span class="sxs-lookup"><span data-stu-id="5f3c1-105">Description</span></span>  
  
### <a name="code"></a><span data-ttu-id="5f3c1-106">Kód</span><span class="sxs-lookup"><span data-stu-id="5f3c1-106">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
## <a name="see-also"></a><span data-ttu-id="5f3c1-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f3c1-107">See also</span></span>

- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="5f3c1-108">Přehled přetažení</span><span class="sxs-lookup"><span data-stu-id="5f3c1-108">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
