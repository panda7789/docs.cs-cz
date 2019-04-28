---
title: 'Postupy: Synchronní hledání ve scénáři'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- seeking Storyboards synchronously [WPF]
- Storyboards [WPF], seeking synchronously
ms.assetid: 03e06271-a946-4810-88ea-3fb4cfa9e0f1
ms.openlocfilehash: 8ac55346ac83ee94318de90655bde6053ef20687
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651230"
---
# <a name="how-to-seek-a-storyboard-synchronously"></a><span data-ttu-id="1f662-102">Postupy: Synchronní hledání ve scénáři</span><span class="sxs-lookup"><span data-stu-id="1f662-102">How to: Seek a Storyboard Synchronously</span></span>
<span data-ttu-id="1f662-103">Následující příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> metodu <xref:System.Windows.Media.Animation.Storyboard> na synchronní na libovolné místo v animace scénáře.</span><span class="sxs-lookup"><span data-stu-id="1f662-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to seek to any position in a storyboard animation synchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f662-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f662-104">Example</span></span>  
 <span data-ttu-id="1f662-105">Následuje kód XAML pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="1f662-105">The following is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardSynchronouslyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml#seekstoryboardsynchronouslyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="1f662-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f662-106">Example</span></span>  
 <span data-ttu-id="1f662-107">Následuje kód použitý s výše uvedený kód XAML.</span><span class="sxs-lookup"><span data-stu-id="1f662-107">The following is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml.cs#seekstoryboardsynchronouslycodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardSynchronouslyExample.xaml.vb#seekstoryboardsynchronouslycodebehindexamplewholepage)]
