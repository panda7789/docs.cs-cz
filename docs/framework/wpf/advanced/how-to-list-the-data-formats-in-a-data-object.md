---
title: 'Postupy: Seznam datových formátů v datovém objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
ms.openlocfilehash: c8e9f24a0e991fa44ddd3f4d778cc7ba640ae9c3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370173"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="439fd-102">Postupy: Seznam datových formátů v datovém objektu</span><span class="sxs-lookup"><span data-stu-id="439fd-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="439fd-103">Následující příklady ukazují, jak používat <xref:System.Windows.DataObject.GetFormats%2A> přetížení metody get pole řetězců, které označuje každou formát dat, který je k dispozici v datovém objektu.</span><span class="sxs-lookup"><span data-stu-id="439fd-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="439fd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="439fd-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="439fd-105">Popis</span><span class="sxs-lookup"><span data-stu-id="439fd-105">Description</span></span>  
 <span data-ttu-id="439fd-106">Následující příklad kódu používá <xref:System.Windows.DataObject.GetFormats%2A> přetížení pro získání pole řetězců, které označuje všechny datových formátů do datového objektu (nativní a automaticky převoditelné).</span><span class="sxs-lookup"><span data-stu-id="439fd-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="439fd-107">Kód</span><span class="sxs-lookup"><span data-stu-id="439fd-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="439fd-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="439fd-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="439fd-109">Popis</span><span class="sxs-lookup"><span data-stu-id="439fd-109">Description</span></span>  
 <span data-ttu-id="439fd-110">Následující příklad kódu používá <xref:System.Windows.DataObject.GetFormats%2A> přetížení pro získání pole řetězců, které označuje pouze datových formátů do datového objektu (formáty jsou filtrovány lze automaticky převést data) k dispozici.</span><span class="sxs-lookup"><span data-stu-id="439fd-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="439fd-111">Kód</span><span class="sxs-lookup"><span data-stu-id="439fd-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="439fd-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="439fd-112">See also</span></span>
- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="439fd-113">Přehled přetažení</span><span class="sxs-lookup"><span data-stu-id="439fd-113">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
