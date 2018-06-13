---
title: 'Postupy: Umístění vlastní místní nabídky v prvku RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
ms.openlocfilehash: bde28cdb87bdaef3198d1efd3059fed3d0ae0ce2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553848"
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
