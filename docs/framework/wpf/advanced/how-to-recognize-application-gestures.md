---
title: 'Postupy: Rozlišení gest aplikací'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
ms.openlocfilehash: 99deaa528a089f2d16268747f2e946873f3420a0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370511"
---
# <a name="how-to-recognize-application-gestures"></a>Postupy: Rozlišení gest aplikací
Následující příklad ukazuje, jak když uživatel provede smazání inkoustu <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gesta na <xref:System.Windows.Controls.InkCanvas>. Tento příklad předpokládá <xref:System.Windows.Controls.InkCanvas>, označované jako `inkCanvas1`, je deklarována v souboru XAML.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[HowToRecognizeGestures#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Ink.ApplicationGesture>
- <xref:System.Windows.Controls.InkCanvas>
- <xref:System.Windows.Controls.InkCanvas.Gesture>
