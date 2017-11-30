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
ms.openlocfilehash: ca4c94fe073fd618ca79d08812c42550594f445d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a><span data-ttu-id="3ab72-102">Postupy: Změna FlowDirection obsahu z programu</span><span class="sxs-lookup"><span data-stu-id="3ab72-102">How to: Change the FlowDirection of Content Programmatically</span></span>
<span data-ttu-id="3ab72-103">Tento příklad ukazuje, jak změnit prostřednictvím kódu programu <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost <xref:System.Windows.Controls.FlowDocumentReader>.</span><span class="sxs-lookup"><span data-stu-id="3ab72-103">This example shows how to programmatically change the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property of a <xref:System.Windows.Controls.FlowDocumentReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ab72-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ab72-104">Example</span></span>  
 <span data-ttu-id="3ab72-105">Dva <xref:System.Windows.Controls.Button> prvky jsou vytvořeny, každý představuje jeden z možných hodnot <xref:System.Windows.FlowDirection>.</span><span class="sxs-lookup"><span data-stu-id="3ab72-105">Two <xref:System.Windows.Controls.Button> elements are created, each representing one of the possible values of <xref:System.Windows.FlowDirection>.</span></span> <span data-ttu-id="3ab72-106">Při kliknutí na tlačítko je k obsahu použita hodnota přidružené vlastnosti <xref:System.Windows.Controls.FlowDocumentReader> s názvem `tf1`.</span><span class="sxs-lookup"><span data-stu-id="3ab72-106">When a button is clicked, the associated property value is applied to the contents of a <xref:System.Windows.Controls.FlowDocumentReader> named `tf1`.</span></span>  <span data-ttu-id="3ab72-107">Hodnota vlastnosti se zapisují také do <xref:System.Windows.Controls.TextBlock> s názvem `txt1`.</span><span class="sxs-lookup"><span data-stu-id="3ab72-107">The property value is also written to a <xref:System.Windows.Controls.TextBlock> named `txt1`.</span></span>  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a><span data-ttu-id="3ab72-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ab72-108">Example</span></span>  
 <span data-ttu-id="3ab72-109">Události související s kliknutí na tlačítko, které jsou definované výše jsou zpracovány v [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="3ab72-109">The events associated with the button clicks defined above are handled in a [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] code-behind file.</span></span>  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
