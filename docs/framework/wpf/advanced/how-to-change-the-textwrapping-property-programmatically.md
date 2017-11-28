---
title: "Postupy: Změna vlastnosti TextWrapping z programu"
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
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 74ddcf55c8918602ecac866913f2007da143f443
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a><span data-ttu-id="e371f-102">Postupy: Změna vlastnosti TextWrapping z programu</span><span class="sxs-lookup"><span data-stu-id="e371f-102">How to: Change the TextWrapping Property Programmatically</span></span>
## <a name="example"></a><span data-ttu-id="e371f-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="e371f-103">Example</span></span>  
 <span data-ttu-id="e371f-104">Následující příklad kódu ukazuje, jak změnit hodnotu <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> vlastnost prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="e371f-104">The following code example shows how to change the value of the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> property programmatically.</span></span>  
  
 <span data-ttu-id="e371f-105">Tři <xref:System.Windows.Controls.Button> elementy jsou umístěny v rámci <xref:System.Windows.Controls.StackPanel> element v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e371f-105">Three <xref:System.Windows.Controls.Button> elements are placed within a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="e371f-106">Každý <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí pro <xref:System.Windows.Controls.Button> odpovídá obslužnou rutinu v kódu.</span><span class="sxs-lookup"><span data-stu-id="e371f-106">Each <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event for a <xref:System.Windows.Controls.Button> corresponds with an event handler in the code.</span></span> <span data-ttu-id="e371f-107">Obslužné rutiny událostí používají stejný název jako <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> hodnotu, použijí se na `txt2` při kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e371f-107">The event handlers use the same name as the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> value they will apply to `txt2` when the button is clicked.</span></span> <span data-ttu-id="e371f-108">Navíc text v `txt1` ( <xref:System.Windows.Controls.TextBlock> to není znázorněné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) se aktualizuje, aby odrážely změny ve vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e371f-108">Also, the text in `txt1` (a <xref:System.Windows.Controls.TextBlock> not shown in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) is updated to reflect the change in the property.</span></span>  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e371f-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="e371f-109">See Also</span></span>  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>  
 <xref:System.Windows.TextWrapping>
