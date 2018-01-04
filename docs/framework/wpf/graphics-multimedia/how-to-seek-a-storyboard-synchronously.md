---
title: "Postupy: Synchronní hledání ve scénáři"
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
- seeking Storyboards synchronously [WPF]
- Storyboards [WPF], seeking synchronously
ms.assetid: 03e06271-a946-4810-88ea-3fb4cfa9e0f1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb5f0203c80cc94d17fcfcd40ff4d79bf8ecdc85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-seek-a-storyboard-synchronously"></a><span data-ttu-id="073c0-102">Postupy: Synchronní hledání ve scénáři</span><span class="sxs-lookup"><span data-stu-id="073c0-102">How to: Seek a Storyboard Synchronously</span></span>
<span data-ttu-id="073c0-103">Následující příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> metodu <xref:System.Windows.Media.Animation.Storyboard> požadovat všechny pozice v storyboard animace synchronně.</span><span class="sxs-lookup"><span data-stu-id="073c0-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to seek to any position in a storyboard animation synchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="073c0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="073c0-104">Example</span></span>  
 <span data-ttu-id="073c0-105">Zde je kód XAML pro vzorovou.</span><span class="sxs-lookup"><span data-stu-id="073c0-105">The following is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardSynchronouslyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml#seekstoryboardsynchronouslyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="073c0-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="073c0-106">Example</span></span>  
 <span data-ttu-id="073c0-107">Následuje kód použít s výše uvedený kód XAML.</span><span class="sxs-lookup"><span data-stu-id="073c0-107">The following is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml.cs#seekstoryboardsynchronouslycodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardSynchronouslyExample.xaml.vb#seekstoryboardsynchronouslycodebehindexamplewholepage)]
