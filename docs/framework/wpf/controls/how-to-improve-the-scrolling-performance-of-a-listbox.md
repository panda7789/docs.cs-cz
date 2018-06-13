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
ms.openlocfilehash: 224b996ad97d9a71ce43023143b68c2ab5b8467b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552789"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a><span data-ttu-id="0b4f5-102">Postupy: Zvýšení výkonu posunování prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="0b4f5-102">How to: Improve the Scrolling Performance of a ListBox</span></span>
<span data-ttu-id="0b4f5-103">Pokud <xref:System.Windows.Controls.ListBox> obsahuje mnoho položek rozhraní odpověď uživatele může být pomalé, co uživatel posune <xref:System.Windows.Controls.ListBox> pomocí kolečka myši nebo přetažením úchytu posuvníku.</span><span class="sxs-lookup"><span data-stu-id="0b4f5-103">If a <xref:System.Windows.Controls.ListBox> contains many items, the user interface response can be slow when a user scrolls the <xref:System.Windows.Controls.ListBox> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="0b4f5-104">Může zlepšit výkon <xref:System.Windows.Controls.ListBox> když uživatel posune nastavením `VirtualizingStackPanel.VirtualizationMode` přidružená vlastnost k <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0b4f5-104">You can improve the performance of the <xref:System.Windows.Controls.ListBox> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b4f5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b4f5-105">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="0b4f5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0b4f5-106">Description</span></span>  
<span data-ttu-id="0b4f5-107">Následující příklad vytvoří <xref:System.Windows.Controls.ListBox> a nastaví `VirtualizingStackPanel.VirtualizationMode` přidružená vlastnost k <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> ke zlepšení výkonu při posouvání.</span><span class="sxs-lookup"><span data-stu-id="0b4f5-107">The following example creates a <xref:System.Windows.Controls.ListBox> and sets the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to improve performance during scrolling.</span></span>  
  
## <a name="code"></a><span data-ttu-id="0b4f5-108">Kód</span><span class="sxs-lookup"><span data-stu-id="0b4f5-108">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 <span data-ttu-id="0b4f5-109">Následující příklad ukazuje data, že předchozí příklad používá.</span><span class="sxs-lookup"><span data-stu-id="0b4f5-109">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
