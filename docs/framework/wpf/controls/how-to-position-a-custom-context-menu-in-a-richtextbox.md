---
title: "Postupy: Umístění vlastní místní nabídky v prvku RichTextBox"
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
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1c0a4fd8d2df15dcca2d9d1751f3089922d9a5ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a><span data-ttu-id="00dcf-102">Postupy: Umístění vlastní místní nabídky v prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="00dcf-102">How to: Position a Custom Context Menu in a RichTextBox</span></span>
<span data-ttu-id="00dcf-103">Tento příklad ukazuje, jak na pozici vlastní kontextovou nabídku pro <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="00dcf-103">This example shows how to position a custom context menu for a <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="00dcf-104">Při implementaci vlastní kontextovou nabídku pro **RichTextBox**, je zodpovědná za zpracování umístění v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="00dcf-104">When you implement a custom context menu for a **RichTextBox**, you are responsible for handling the placement of the context menu.</span></span>  <span data-ttu-id="00dcf-105">Ve výchozím nastavení, je vlastní Kontextová nabídka otevřít na střed **RichTextBox**.</span><span class="sxs-lookup"><span data-stu-id="00dcf-105">By default, a custom context menu is opened at the center of the **RichTextBox**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00dcf-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="00dcf-106">Example</span></span>  
 <span data-ttu-id="00dcf-107">Chcete-li přepsat výchozí umístění chování, přidejte naslouchací proces pro <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> událostí.</span><span class="sxs-lookup"><span data-stu-id="00dcf-107">To override the default placement behavior, add a listener for the <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event.</span></span>  <span data-ttu-id="00dcf-108">Následující příklad ukazuje, jak to provést prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="00dcf-108">The following example shows how to do this programmatically.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a><span data-ttu-id="00dcf-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="00dcf-109">Example</span></span>  
 <span data-ttu-id="00dcf-110">Následující příklad ukazuje implementaci odpovídající <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> událostí naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="00dcf-110">The following example shows an implementation the corresponding <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event listener.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="00dcf-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="00dcf-111">See Also</span></span>  
 [<span data-ttu-id="00dcf-112">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="00dcf-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="00dcf-113">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="00dcf-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
