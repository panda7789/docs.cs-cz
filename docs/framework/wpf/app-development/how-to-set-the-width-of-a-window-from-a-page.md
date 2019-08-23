---
title: 'Postupy: Nastavení šířky okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: 1e16b75ecb85550facdf24a5b9e341cf0c061178
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940767"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a><span data-ttu-id="5c69f-102">Postupy: Nastavení šířky okna ze stránky</span><span class="sxs-lookup"><span data-stu-id="5c69f-102">How to: Set the Width of a Window from a Page</span></span>
<span data-ttu-id="5c69f-103">Tento příklad ukazuje, jak nastavit šířku okna z <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="5c69f-103">This example illustrates how to set the width of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c69f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c69f-104">Example</span></span>  
 <span data-ttu-id="5c69f-105">Může nastavit šířku okna <xref:System.Windows.Controls.Page.WindowWidth%2A>hostitele nastavením. <xref:System.Windows.Controls.Page></span><span class="sxs-lookup"><span data-stu-id="5c69f-105">A <xref:System.Windows.Controls.Page> can set the width of its host window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span></span> <span data-ttu-id="5c69f-106">Tato vlastnost umožňuje, <xref:System.Windows.Controls.Page> aby nemusela explicitní znalosti typu okna, který je hostitelem.</span><span class="sxs-lookup"><span data-stu-id="5c69f-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c69f-107">Chcete-li nastavit šířku okna pomocí <xref:System.Windows.Controls.Page.WindowWidth%2A> <xref:System.Windows.Controls.Page> , musí být podřízeným objektem okna.</span><span class="sxs-lookup"><span data-stu-id="5c69f-107">To set the width of a window using <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
