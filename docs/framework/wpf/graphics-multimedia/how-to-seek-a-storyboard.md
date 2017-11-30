---
title: "Postupy: Hledání ve scénáři"
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
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c76236d8497936500989b56c816f8fe50efcc238
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="bd223-102">Postupy: Hledání ve scénáři</span><span class="sxs-lookup"><span data-stu-id="bd223-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="bd223-103">Následující příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metodu <xref:System.Windows.Media.Animation.Storyboard> na všechny pozice v storyboard animace.</span><span class="sxs-lookup"><span data-stu-id="bd223-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd223-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd223-104">Example</span></span>  
 <span data-ttu-id="bd223-105">Níže je kód XAML pro vzorovou.</span><span class="sxs-lookup"><span data-stu-id="bd223-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="bd223-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd223-106">Example</span></span>  
 <span data-ttu-id="bd223-107">Níže je kód použít s výše uvedený kód XAML.</span><span class="sxs-lookup"><span data-stu-id="bd223-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="bd223-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd223-108">See Also</span></span>  
 [<span data-ttu-id="bd223-109">Hledat scénáře synchronně</span><span class="sxs-lookup"><span data-stu-id="bd223-109">Seek a Storyboard Synchronously</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)
