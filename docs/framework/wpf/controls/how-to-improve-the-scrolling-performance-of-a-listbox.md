---
title: "Postupy: Zvýšení výkonu posunování prvku ListBox"
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
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 46a54c9ed1dff9796506df78d07d7506dfd29cbf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a><span data-ttu-id="83584-102">Postupy: Zvýšení výkonu posunování prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="83584-102">How to: Improve the Scrolling Performance of a ListBox</span></span>
<span data-ttu-id="83584-103">Pokud <xref:System.Windows.Controls.ListBox> obsahuje mnoho položek rozhraní odpověď uživatele může být pomalé, co uživatel posune <xref:System.Windows.Controls.ListBox> pomocí kolečka myši nebo přetažením úchytu posuvníku.</span><span class="sxs-lookup"><span data-stu-id="83584-103">If a <xref:System.Windows.Controls.ListBox> contains many items, the user interface response can be slow when a user scrolls the <xref:System.Windows.Controls.ListBox> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="83584-104">Může zlepšit výkon <xref:System.Windows.Controls.ListBox> když uživatel posune nastavením `VirtualizingStackPanel.VirtualizationMode` přidružená vlastnost k <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83584-104">You can improve the performance of the <xref:System.Windows.Controls.ListBox> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83584-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="83584-105">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="83584-106">Popis</span><span class="sxs-lookup"><span data-stu-id="83584-106">Description</span></span>  
<span data-ttu-id="83584-107">Následující příklad vytvoří <xref:System.Windows.Controls.ListBox> a nastaví `VirtualizingStackPanel.VirtualizationMode` přidružená vlastnost k <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> ke zlepšení výkonu při posouvání.</span><span class="sxs-lookup"><span data-stu-id="83584-107">The following example creates a <xref:System.Windows.Controls.ListBox> and sets the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to improve performance during scrolling.</span></span>  
  
## <a name="code"></a><span data-ttu-id="83584-108">Kód</span><span class="sxs-lookup"><span data-stu-id="83584-108">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 <span data-ttu-id="83584-109">Následující příklad ukazuje data, že předchozí příklad používá.</span><span class="sxs-lookup"><span data-stu-id="83584-109">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
