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
ms.openlocfilehash: f9407f59c3daafd09fa5b84006f33ef2f3ebd31f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209421"
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a>Postupy: Umístění vlastní místní nabídky v prvku RichTextBox
Tento příklad ukazuje, jak umístění vlastní místní nabídky pro <xref:System.Windows.Controls.RichTextBox>.  
  
 Pokud implementujete vlastní místní nabídky pro **RichTextBox**, zodpovídáte za zpracování umístění v místní nabídce.  Ve výchozím nastavení, je otevřít vlastní místní nabídky v centru **RichTextBox**.  
  
## <a name="example"></a>Příklad  
 Chcete-li potlačit výchozí chování umístění, přidejte naslouchací proces pro <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> událostí.  Následující příklad ukazuje, jak to provést prostřednictvím kódu programu.  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci odpovídající <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> naslouchací proces událostí.  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a>Viz také:

- [RichTextBox – přehled](richtextbox-overview.md)
- [TextBox – přehled](textbox-overview.md)
