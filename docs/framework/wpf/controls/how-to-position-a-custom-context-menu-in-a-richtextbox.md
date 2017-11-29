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
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a>Postupy: Umístění vlastní místní nabídky v prvku RichTextBox
Tento příklad ukazuje, jak na pozici vlastní kontextovou nabídku pro <xref:System.Windows.Controls.RichTextBox>.  
  
 Při implementaci vlastní kontextovou nabídku pro **RichTextBox**, je zodpovědná za zpracování umístění v místní nabídce.  Ve výchozím nastavení, je vlastní Kontextová nabídka otevřít na střed **RichTextBox**.  
  
## <a name="example"></a>Příklad  
 Chcete-li přepsat výchozí umístění chování, přidejte naslouchací proces pro <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> událostí.  Následující příklad ukazuje, jak to provést prostřednictvím kódu programu.  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci odpovídající <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> událostí naslouchací proces.  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a>Viz také  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)
