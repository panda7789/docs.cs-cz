---
title: 'Postupy: Rozpoznání gest aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
ms.openlocfilehash: 647e7c9c1d785cebfdc362dc48511d865f3945dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767432"
---
# <a name="how-to-recognize-application-gestures"></a><span data-ttu-id="c2c16-102">Postupy: Rozpoznání gest aplikace</span><span class="sxs-lookup"><span data-stu-id="c2c16-102">How To: Recognize Application Gestures</span></span>
<span data-ttu-id="c2c16-103">Následující příklad ukazuje, jak když uživatel provede smazání inkoustu <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gesta na <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="c2c16-103">The following example demonstrates how to erase ink when a user makes a <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gesture on an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="c2c16-104">Tento příklad předpokládá <xref:System.Windows.Controls.InkCanvas>, označované jako `inkCanvas1`, je deklarována v souboru XAML.</span><span class="sxs-lookup"><span data-stu-id="c2c16-104">This example assumes an <xref:System.Windows.Controls.InkCanvas>, called `inkCanvas1`, is declared in the XAML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2c16-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2c16-105">Example</span></span>  
 [!code-csharp[HowToRecognizeGestures#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c2c16-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2c16-106">See also</span></span>

- <xref:System.Windows.Ink.ApplicationGesture>
- <xref:System.Windows.Controls.InkCanvas>
- <xref:System.Windows.Controls.InkCanvas.Gesture>
