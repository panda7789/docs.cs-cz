---
title: 'Postupy: Určení, jestli datový objekt obsahuje formát dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
ms.openlocfilehash: 4cec733490e2a9dc5d54b3b253ac38a5090ac885
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207965"
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a><span data-ttu-id="95ef1-102">Postupy: Určení, jestli datový objekt obsahuje formát dat</span><span class="sxs-lookup"><span data-stu-id="95ef1-102">How to: Determine if a Data Format is Present in a Data Object</span></span>
<span data-ttu-id="95ef1-103">Následující příklady ukazují, jak používat různé <xref:System.Windows.DataObject.GetDataPresent%2A> přetížení metody pro dotaz, zda je k dispozici v datovém objektu konkrétním datovém formátu.</span><span class="sxs-lookup"><span data-stu-id="95ef1-103">The following examples show how to use the various <xref:System.Windows.DataObject.GetDataPresent%2A> method overloads to query whether a particular data format is present in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95ef1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="95ef1-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="95ef1-105">Popis</span><span class="sxs-lookup"><span data-stu-id="95ef1-105">Description</span></span>  
 <span data-ttu-id="95ef1-106">Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> přetížení pro dotaz na přítomnost konkrétním datovém formátu řetězce popisovače.</span><span class="sxs-lookup"><span data-stu-id="95ef1-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to query for the presence of a particular data format by descriptor string.</span></span>  
  
### <a name="code"></a><span data-ttu-id="95ef1-107">Kód</span><span class="sxs-lookup"><span data-stu-id="95ef1-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a><span data-ttu-id="95ef1-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="95ef1-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="95ef1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="95ef1-109">Description</span></span>  
 <span data-ttu-id="95ef1-110">Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> přetížení pro dotaz na přítomnost konkrétním datovém formátu podle typu.</span><span class="sxs-lookup"><span data-stu-id="95ef1-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> overload to query for the presence of a particular data format by type.</span></span>  
  
### <a name="code"></a><span data-ttu-id="95ef1-111">Kód</span><span class="sxs-lookup"><span data-stu-id="95ef1-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a><span data-ttu-id="95ef1-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="95ef1-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="95ef1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="95ef1-113">Description</span></span>  
 <span data-ttu-id="95ef1-114">Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> přetížení pro dotaz na data pomocí řetězce popisovače a určíte, jak nakládat s automaticky převoditelné datových formátů.</span><span class="sxs-lookup"><span data-stu-id="95ef1-114">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to query for data by descriptor string, and specifying how to treat auto-convertible data formats.</span></span>  
  
### <a name="code"></a><span data-ttu-id="95ef1-115">Kód</span><span class="sxs-lookup"><span data-stu-id="95ef1-115">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a><span data-ttu-id="95ef1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95ef1-116">See also</span></span>

- <xref:System.Windows.IDataObject>
