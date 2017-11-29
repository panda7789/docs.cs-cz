---
title: "Postupy: Načtení dat v konkrétním datovém formátu"
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
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e6513fd6d8d443b76059626c0e40991e35830c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="7a48b-102">Postupy: Načtení dat v konkrétním datovém formátu</span><span class="sxs-lookup"><span data-stu-id="7a48b-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="7a48b-103">Následující příklady ukazují, jak k načtení dat z objektu dat v zadaném formátu.</span><span class="sxs-lookup"><span data-stu-id="7a48b-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a48b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a48b-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7a48b-105">Popis</span><span class="sxs-lookup"><span data-stu-id="7a48b-105">Description</span></span>  
 <span data-ttu-id="7a48b-106">Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> přetížení nejdřív zkontrolovat, pokud zadaná data formátu je k dispozici (nativně nebo automatický převod), pokud zadaný formát je k dispozici, příklad načte data pomocí <xref:System.Windows.DataObject.GetData%28System.String%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="7a48b-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7a48b-107">Kód</span><span class="sxs-lookup"><span data-stu-id="7a48b-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="7a48b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a48b-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7a48b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7a48b-109">Description</span></span>  
 <span data-ttu-id="7a48b-110">Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> přetížení nejdřív zkontrolujte, jestli je zadaná data formátu nativně dostupná (formáty automaticky převoditelné dat jsou filtrovány); Pokud zadaný formát je k dispozici, příklad načte data pomocí <xref:System.Windows.DataObject.GetData%28System.String%29>metoda.</span><span class="sxs-lookup"><span data-stu-id="7a48b-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7a48b-111">Kód</span><span class="sxs-lookup"><span data-stu-id="7a48b-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="7a48b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a48b-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="7a48b-113">Přetáhnout myší – přehled</span><span class="sxs-lookup"><span data-stu-id="7a48b-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
