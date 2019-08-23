---
title: 'Postupy: Nastavení názvu okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 0f618af89965822b0df96a264997dabd9cae7608
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940790"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a><span data-ttu-id="e6cfe-102">Postupy: Nastavení názvu okna ze stránky</span><span class="sxs-lookup"><span data-stu-id="e6cfe-102">How to: Set the Title of a Window from a Page</span></span>
<span data-ttu-id="e6cfe-103">Tento příklad ukazuje, jak nastavit název okna, ve kterém <xref:System.Windows.Controls.Page> je hostovaný.</span><span class="sxs-lookup"><span data-stu-id="e6cfe-103">This example shows how to set the title of the window in which a <xref:System.Windows.Controls.Page> is hosted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6cfe-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6cfe-104">Example</span></span>  
 <span data-ttu-id="e6cfe-105">Stránka může změnit název okna, který je hostitelem, nastavením <xref:System.Windows.Controls.Page.WindowTitle%2A> vlastnosti, například takto:</span><span class="sxs-lookup"><span data-stu-id="e6cfe-105">A page can change the title of the window that is hosting it by setting the <xref:System.Windows.Controls.Page.WindowTitle%2A> property, like so:</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
> <span data-ttu-id="e6cfe-106"><xref:System.Windows.Controls.Page.Title%2A> Nastavením vlastnosti stránky se nezmění hodnota názvu okna.</span><span class="sxs-lookup"><span data-stu-id="e6cfe-106">Setting the <xref:System.Windows.Controls.Page.Title%2A> property of a page does not change the value of the window title.</span></span> <span data-ttu-id="e6cfe-107">Místo toho <xref:System.Windows.Controls.Page.Title%2A> Určuje název položky stránky v historii navigace.</span><span class="sxs-lookup"><span data-stu-id="e6cfe-107">Instead, <xref:System.Windows.Controls.Page.Title%2A> specifies the name of a page entry in navigation history.</span></span>
