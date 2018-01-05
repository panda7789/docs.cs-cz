---
title: "Postupy: Změna FlowDirection obsahu z programu"
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
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3670deceb2c06e58d859fae15fbf9ee791819dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Postupy: Změna FlowDirection obsahu z programu
Tento příklad ukazuje, jak změnit prostřednictvím kódu programu <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Příklad  
 Dva <xref:System.Windows.Controls.Button> prvky jsou vytvořeny, každý představuje jeden z možných hodnot <xref:System.Windows.FlowDirection>. Při kliknutí na tlačítko je k obsahu použita hodnota přidružené vlastnosti <xref:System.Windows.Controls.FlowDocumentReader> s názvem `tf1`.  Hodnota vlastnosti se zapisují také do <xref:System.Windows.Controls.TextBlock> s názvem `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Příklad  
 Události související s kliknutí na tlačítko, které jsou definované výše jsou zpracovány v [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] souboru kódu na pozadí.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
