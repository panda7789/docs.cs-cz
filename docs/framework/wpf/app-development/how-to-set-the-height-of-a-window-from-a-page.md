---
title: 'Postupy: Nastavení výšky okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c99ea134478635f368b71443f43e4d8f772cb5aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007298"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a><span data-ttu-id="11239-102">Postupy: Nastavení výšky okna ze stránky</span><span class="sxs-lookup"><span data-stu-id="11239-102">How to: Set the Height of a Window from a Page</span></span>
<span data-ttu-id="11239-103">Tento příklad ukazuje, jak nastavit výšku okna z <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="11239-103">This example illustrates how to set the height of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11239-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="11239-104">Example</span></span>  
 <span data-ttu-id="11239-105">A <xref:System.Windows.Controls.Page> výšku okna hostitele můžete nastavit tak, že nastavíte <xref:System.Windows.Controls.Page.WindowHeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="11239-105">A <xref:System.Windows.Controls.Page> can set the height of its host window by setting <xref:System.Windows.Controls.Page.WindowHeight%2A>.</span></span> <span data-ttu-id="11239-106">Tato vlastnost umožňuje <xref:System.Windows.Controls.Page> nebudete chtít explicitní znalost typu hostitelského okna.</span><span class="sxs-lookup"><span data-stu-id="11239-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11239-107">Chcete-li nastavit výšku okna pomocí <xref:System.Windows.Controls.Page.WindowHeight%2A>, <xref:System.Windows.Controls.Page> musí být podřízené okno.</span><span class="sxs-lookup"><span data-stu-id="11239-107">To set the height of a window using <xref:System.Windows.Controls.Page.WindowHeight%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
