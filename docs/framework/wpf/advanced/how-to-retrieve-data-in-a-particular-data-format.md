---
title: 'Postupy: Načtení dat v konkrétním datovém formátu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
ms.openlocfilehash: b3ec1b8fa873fd449956912e9e77e98b0362cb0e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080017"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="a7d0a-102">Postupy: Načtení dat v konkrétním datovém formátu</span><span class="sxs-lookup"><span data-stu-id="a7d0a-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="a7d0a-103">Následující příklady ukazují, jak načíst data z objektu dat v zadaném formátu.</span><span class="sxs-lookup"><span data-stu-id="a7d0a-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7d0a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7d0a-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a7d0a-105">Popis</span><span class="sxs-lookup"><span data-stu-id="a7d0a-105">Description</span></span>  
 <span data-ttu-id="a7d0a-106">Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> přetížení nejdřív zkontrolovat, pokud zadaná data naformátovat je k dispozici (nativní nebo automatický převod), pokud zadaný formát je k dispozici, příklad načte data s využitím <xref:System.Windows.DataObject.GetData%28System.String%29> metody.</span><span class="sxs-lookup"><span data-stu-id="a7d0a-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a7d0a-107">Kód</span><span class="sxs-lookup"><span data-stu-id="a7d0a-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="a7d0a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7d0a-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a7d0a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a7d0a-109">Description</span></span>  
 <span data-ttu-id="a7d0a-110">Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> nejprve zkontrolujte, jestli je zadaný datový formát nativně dostupná přetížení (převoditelné automaticky datových formátů jsou filtrovány); Pokud zadaný formát je k dispozici, příklad načte data s využitím <xref:System.Windows.DataObject.GetData%28System.String%29>metody.</span><span class="sxs-lookup"><span data-stu-id="a7d0a-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a7d0a-111">Kód</span><span class="sxs-lookup"><span data-stu-id="a7d0a-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="a7d0a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7d0a-112">See also</span></span>

- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="a7d0a-113">Přehled přetažení</span><span class="sxs-lookup"><span data-stu-id="a7d0a-113">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
