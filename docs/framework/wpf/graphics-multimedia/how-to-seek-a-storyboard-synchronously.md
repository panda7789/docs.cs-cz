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
ms.openlocfilehash: 45d71dde85ea65e45a36b4f938e1fd5135cc0e00
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-seek-a-storyboard-synchronously"></a><span data-ttu-id="ec17a-102">Postupy: Synchronní hledání ve scénáři</span><span class="sxs-lookup"><span data-stu-id="ec17a-102">How to: Seek a Storyboard Synchronously</span></span>
<span data-ttu-id="ec17a-103">Následující příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> metodu <xref:System.Windows.Media.Animation.Storyboard> požadovat všechny pozice v storyboard animace synchronně.</span><span class="sxs-lookup"><span data-stu-id="ec17a-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to seek to any position in a storyboard animation synchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec17a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec17a-104">Example</span></span>  
 <span data-ttu-id="ec17a-105">Zde je kód XAML pro vzorovou.</span><span class="sxs-lookup"><span data-stu-id="ec17a-105">The following is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardSynchronouslyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml#seekstoryboardsynchronouslyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="ec17a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec17a-106">Example</span></span>  
 <span data-ttu-id="ec17a-107">Následuje kód použít s výše uvedený kód XAML.</span><span class="sxs-lookup"><span data-stu-id="ec17a-107">The following is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml.cs#seekstoryboardsynchronouslycodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardSynchronouslyExample.xaml.vb#seekstoryboardsynchronouslycodebehindexamplewholepage)]
