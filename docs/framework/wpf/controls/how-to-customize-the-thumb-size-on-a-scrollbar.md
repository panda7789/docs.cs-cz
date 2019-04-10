---
title: 'Postupy: Přizpůsobení velikosti jezdce v prvku ScrollBar'
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 60ae7c4e95801036c5deb0c485645297509b830c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207276"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a><span data-ttu-id="bc80f-102">Postupy: Přizpůsobení velikosti jezdce v prvku ScrollBar</span><span class="sxs-lookup"><span data-stu-id="bc80f-102">How to: Customize the Thumb Size on a ScrollBar</span></span>
<span data-ttu-id="bc80f-103">Toto téma vysvětluje, jak nastavit <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar> s pevnou velikostí a jak určit minimální velikost <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="bc80f-103">This topic explains how to set the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar> to a fixed size and how to specify a minimum size for the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc80f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc80f-104">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="bc80f-105">Popis</span><span class="sxs-lookup"><span data-stu-id="bc80f-105">Description</span></span>  
 <span data-ttu-id="bc80f-106">Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.ScrollBar> , který má <xref:System.Windows.Controls.Primitives.Thumb> s pevnou velikostí.</span><span class="sxs-lookup"><span data-stu-id="bc80f-106">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a fixed size.</span></span> <span data-ttu-id="bc80f-107">V příkladu je nastavena <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> vlastnost <xref:System.Windows.Controls.Primitives.Thumb> k <xref:System.Double.NaN> a nastaví výšku <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="bc80f-107">The example sets the <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> property of the <xref:System.Windows.Controls.Primitives.Thumb> to <xref:System.Double.NaN> and sets the height of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  <span data-ttu-id="bc80f-108">Chcete-li vytvořit vodorovnou <xref:System.Windows.Controls.Primitives.ScrollBar> s <xref:System.Windows.Controls.Primitives.Thumb> , který má pevnou šířku, nastavte šířku <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="bc80f-108">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a fixed width, set the width of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="bc80f-109">Kód</span><span class="sxs-lookup"><span data-stu-id="bc80f-109">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a><span data-ttu-id="bc80f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="bc80f-110">Description</span></span>  
 <span data-ttu-id="bc80f-111">Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.ScrollBar> , který má <xref:System.Windows.Controls.Primitives.Thumb> s minimální velikostí.</span><span class="sxs-lookup"><span data-stu-id="bc80f-111">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a minimum size.</span></span> <span data-ttu-id="bc80f-112">Příklad nastaví hodnotu <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc80f-112">The example sets the value of <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span></span> <span data-ttu-id="bc80f-113">Chcete-li vytvořit vodorovnou <xref:System.Windows.Controls.Primitives.ScrollBar> s <xref:System.Windows.Controls.Primitives.Thumb> , který má minimální šířka, nastavte <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc80f-113">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a minimum width, set the <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="bc80f-114">Kód</span><span class="sxs-lookup"><span data-stu-id="bc80f-114">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bc80f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc80f-115">See also</span></span>

- [<span data-ttu-id="bc80f-116">ScrollBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="bc80f-116">ScrollBar Styles and Templates</span></span>](scrollbar-styles-and-templates.md)
