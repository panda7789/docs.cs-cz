---
title: 'Postupy: nastavení název časového období ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: e69812b59783717b7b9c832d4e8ab01ab42827c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546182"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a><span data-ttu-id="8e4b2-102">Postupy: nastavení název časového období ze stránky</span><span class="sxs-lookup"><span data-stu-id="8e4b2-102">How to: Set the Title of a Window from a Page</span></span>
<span data-ttu-id="8e4b2-103">Tento příklad ukazuje, jak nastavit nadpis okna, ve kterém <xref:System.Windows.Controls.Page> je hostovaná.</span><span class="sxs-lookup"><span data-stu-id="8e4b2-103">This example shows how to set the title of the window in which a <xref:System.Windows.Controls.Page> is hosted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e4b2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e4b2-104">Example</span></span>  
 <span data-ttu-id="8e4b2-105">Na stránce můžete změnit v záhlaví okna, který je hostitelem nastavením <xref:System.Windows.Controls.Page.WindowTitle%2A> vlastnosti, například takto:</span><span class="sxs-lookup"><span data-stu-id="8e4b2-105">A page can change the title of the window that is hosting it by setting the <xref:System.Windows.Controls.Page.WindowTitle%2A> property, like so:</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  <span data-ttu-id="8e4b2-106">Nastavení <xref:System.Windows.Controls.Page.Title%2A> vlastnosti stránky nezmění hodnota záhlaví okna.</span><span class="sxs-lookup"><span data-stu-id="8e4b2-106">Setting the <xref:System.Windows.Controls.Page.Title%2A> property of a page does not change the value of the window title.</span></span> <span data-ttu-id="8e4b2-107">Místo toho <xref:System.Windows.Controls.Page.Title%2A> Určuje název položky stránky v historii navigace.</span><span class="sxs-lookup"><span data-stu-id="8e4b2-107">Instead, <xref:System.Windows.Controls.Page.Title%2A> specifies the name of a page entry in navigation history.</span></span>
