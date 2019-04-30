---
title: 'Postupy: Změna směru toku obsahu pomocí programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
ms.openlocfilehash: ec159ed0efce8b5514788331e8715a55e7a8a638
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776555"
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Postupy: Změna směru toku obsahu pomocí programu
Tento příklad ukazuje, jak programově změnit <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Příklad  
 Dvě <xref:System.Windows.Controls.Button> prvky jsou vytvořeny, každý představující jednu z možných hodnot <xref:System.Windows.FlowDirection>. Po kliknutí na tlačítko hodnotu přidružené vlastnosti platí pro obsah <xref:System.Windows.Controls.FlowDocumentReader> s názvem `tf1`.  Hodnota vlastnosti se zapisují také do <xref:System.Windows.Controls.TextBlock> s názvem `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Příklad  
 Události přidružené ke kliknutí na tlačítko, které jsou definované výše zachází C# soubor kódu na pozadí.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
