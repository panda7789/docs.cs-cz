---
title: "Postupy: nastavení šířky okna ze stránky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc9843d4a0f76547b76698a9686b5c4936baa322
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a><span data-ttu-id="9879b-102">Postupy: nastavení šířky okna ze stránky</span><span class="sxs-lookup"><span data-stu-id="9879b-102">How to: Set the Width of a Window from a Page</span></span>
<span data-ttu-id="9879b-103">Tento příklad ukazuje, jak nastavit šířku v okně <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="9879b-103">This example illustrates how to set the width of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9879b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9879b-104">Example</span></span>  
 <span data-ttu-id="9879b-105">A <xref:System.Windows.Controls.Page> můžete nastavit šířku jeho hostitelské okno nastavením <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span><span class="sxs-lookup"><span data-stu-id="9879b-105">A <xref:System.Windows.Controls.Page> can set the width of its host window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span></span> <span data-ttu-id="9879b-106">Tato vlastnost umožňuje <xref:System.Windows.Controls.Page> k nejsou explicitní znalostní báze typu hostitelského okna.</span><span class="sxs-lookup"><span data-stu-id="9879b-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9879b-107">Chcete-li nastavit šířku okna pomocí <xref:System.Windows.Controls.Page.WindowWidth%2A>, <xref:System.Windows.Controls.Page> musí být podřízeným časového období.</span><span class="sxs-lookup"><span data-stu-id="9879b-107">To set the width of a window using <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
