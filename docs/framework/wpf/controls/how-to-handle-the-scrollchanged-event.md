---
title: 'Postupy: Zpracování události ScrollChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], raising ScrollChanged events
- ScrollChanged events [WPF]
ms.assetid: 42c695d8-ee28-49d4-80fd-fc71e9be7f29
ms.openlocfilehash: 54f20a4b8c6e6fcc190257fcf5de4374415d68b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771056"
---
# <a name="how-to-handle-the-scrollchanged-event"></a><span data-ttu-id="4e6ef-102">Postupy: Zpracování události ScrollChanged</span><span class="sxs-lookup"><span data-stu-id="4e6ef-102">How to: Handle the ScrollChanged Event</span></span>
## <a name="example"></a><span data-ttu-id="4e6ef-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e6ef-103">Example</span></span>  
 <span data-ttu-id="4e6ef-104">Tento příklad ukazuje, jak zpracovat <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> události <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="4e6ef-104">This example shows how to handle the <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> event of a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 <span data-ttu-id="4e6ef-105">A <xref:System.Windows.Documents.FlowDocument> element s <xref:System.Windows.Documents.Paragraph> částí je definována v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e6ef-105">A <xref:System.Windows.Documents.FlowDocument> element with <xref:System.Windows.Documents.Paragraph> parts is defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="4e6ef-106">Když <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> události dochází kvůli zásahu uživatele, je vyvolána obslužná rutina a text je zapsán do <xref:System.Windows.Controls.TextBlock> označující, že došlo k události.</span><span class="sxs-lookup"><span data-stu-id="4e6ef-106">When the <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> event occurs due to user interaction, a handler is invoked, and text is written to a <xref:System.Windows.Controls.TextBlock> indicating that the event has occurred.</span></span>  
  
 [!code-xaml[scrollchangedeventargsLayout#1](~/samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#1)]  
[!code-xaml[scrollchangedeventargsLayout#2](~/samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[scrollchangedeventargsLayout#3](~/samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml.cs#3)]
 [!code-vb[scrollchangedeventargsLayout#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/scrollchangedeventargsLayout/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="4e6ef-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e6ef-107">See also</span></span>

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.ScrollViewer.ScrollChanged>
- <xref:System.Windows.Controls.ScrollChangedEventHandler>
- <xref:System.Windows.Controls.ScrollChangedEventArgs>
