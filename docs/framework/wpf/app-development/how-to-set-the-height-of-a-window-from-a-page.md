---
title: 'Postupy: Nastavení výšky okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c1041af88241011b51c96d7b61423344a32b25ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940804"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a><span data-ttu-id="371ab-102">Postupy: Nastavení výšky okna ze stránky</span><span class="sxs-lookup"><span data-stu-id="371ab-102">How to: Set the Height of a Window from a Page</span></span>
<span data-ttu-id="371ab-103">Tento příklad ukazuje, jak nastavit výšku okna z <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="371ab-103">This example illustrates how to set the height of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="371ab-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="371ab-104">Example</span></span>  
 <span data-ttu-id="371ab-105">Může nastavit výšku svého hostitelského okna <xref:System.Windows.Controls.Page.WindowHeight%2A>nastavením. <xref:System.Windows.Controls.Page></span><span class="sxs-lookup"><span data-stu-id="371ab-105">A <xref:System.Windows.Controls.Page> can set the height of its host window by setting <xref:System.Windows.Controls.Page.WindowHeight%2A>.</span></span> <span data-ttu-id="371ab-106">Tato vlastnost umožňuje, <xref:System.Windows.Controls.Page> aby nemusela explicitní znalosti typu okna, který je hostitelem.</span><span class="sxs-lookup"><span data-stu-id="371ab-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="371ab-107">Chcete-li nastavit výšku okna pomocí <xref:System.Windows.Controls.Page.WindowHeight%2A> <xref:System.Windows.Controls.Page> , musí být podřízeným objektem okna.</span><span class="sxs-lookup"><span data-stu-id="371ab-107">To set the height of a window using <xref:System.Windows.Controls.Page.WindowHeight%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
