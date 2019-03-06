---
title: 'Postupy: Zvýšení výkonu posunování prvku ListBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: a9d1ca1d8ac2ef830984408f3052eb0ed0987c5d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364551"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a><span data-ttu-id="6705a-102">Postupy: Zvýšení výkonu posunování prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="6705a-102">How to: Improve the Scrolling Performance of a ListBox</span></span>
<span data-ttu-id="6705a-103">Pokud <xref:System.Windows.Controls.ListBox> obsahuje mnoho položek odezvy uživatelského rozhraní může být pomalé, když bude uživatel posouvat <xref:System.Windows.Controls.ListBox> pomocí kolečka myši nebo přetažením thumb posuvník.</span><span class="sxs-lookup"><span data-stu-id="6705a-103">If a <xref:System.Windows.Controls.ListBox> contains many items, the user interface response can be slow when a user scrolls the <xref:System.Windows.Controls.ListBox> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="6705a-104">Můžete zvýšit výkon <xref:System.Windows.Controls.ListBox> při procházení tak, že nastavíte `VirtualizingStackPanel.VirtualizationMode` připojené vlastnosti <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6705a-104">You can improve the performance of the <xref:System.Windows.Controls.ListBox> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6705a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="6705a-105">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="6705a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6705a-106">Description</span></span>  
<span data-ttu-id="6705a-107">Následující příklad vytvoří <xref:System.Windows.Controls.ListBox> a nastaví `VirtualizingStackPanel.VirtualizationMode` připojené vlastnosti <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> ke zlepšení výkonu při posouvání.</span><span class="sxs-lookup"><span data-stu-id="6705a-107">The following example creates a <xref:System.Windows.Controls.ListBox> and sets the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to improve performance during scrolling.</span></span>  
  
## <a name="code"></a><span data-ttu-id="6705a-108">Kód</span><span class="sxs-lookup"><span data-stu-id="6705a-108">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 <span data-ttu-id="6705a-109">Následující příklad ukazuje data předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="6705a-109">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
