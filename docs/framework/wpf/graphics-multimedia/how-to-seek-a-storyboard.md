---
title: 'Postupy: Hledání ve scénáři'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
ms.openlocfilehash: 656a5cb38461f71698a312e6382a3a9c29158cc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560273"
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="02883-102">Postupy: Hledání ve scénáři</span><span class="sxs-lookup"><span data-stu-id="02883-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="02883-103">Následující příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metodu <xref:System.Windows.Media.Animation.Storyboard> na všechny pozice v storyboard animace.</span><span class="sxs-lookup"><span data-stu-id="02883-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02883-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="02883-104">Example</span></span>  
 <span data-ttu-id="02883-105">Níže je kód XAML pro vzorovou.</span><span class="sxs-lookup"><span data-stu-id="02883-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="02883-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="02883-106">Example</span></span>  
 <span data-ttu-id="02883-107">Níže je kód použít s výše uvedený kód XAML.</span><span class="sxs-lookup"><span data-stu-id="02883-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="02883-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="02883-108">See Also</span></span>  
 [<span data-ttu-id="02883-109">Synchronní hledání ve scénáři</span><span class="sxs-lookup"><span data-stu-id="02883-109">Seek a Storyboard Synchronously</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)
