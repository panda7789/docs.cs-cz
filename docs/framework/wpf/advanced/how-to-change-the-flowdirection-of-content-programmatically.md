---
title: 'Postupy: Změna FlowDirection obsahu z programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
ms.openlocfilehash: 97a64ad54384077a15a643dc528d043b2ef6627a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543403"
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Postupy: Změna FlowDirection obsahu z programu
Tento příklad ukazuje, jak změnit prostřednictvím kódu programu <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Příklad  
 Dva <xref:System.Windows.Controls.Button> prvky jsou vytvořeny, každý představuje jeden z možných hodnot <xref:System.Windows.FlowDirection>. Při kliknutí na tlačítko je k obsahu použita hodnota přidružené vlastnosti <xref:System.Windows.Controls.FlowDocumentReader> s názvem `tf1`.  Hodnota vlastnosti se zapisují také do <xref:System.Windows.Controls.TextBlock> s názvem `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Příklad  
 Události související s kliknutí na tlačítko, které jsou definované výše jsou zpracovány v souboru kódu C#.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
