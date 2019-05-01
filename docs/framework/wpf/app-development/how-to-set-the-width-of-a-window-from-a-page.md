---
title: 'Postupy: Nastavení šířky okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: fee6d4c9ae9dae03e81cc4be56576763cb59958b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006712"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a><span data-ttu-id="36a33-102">Postupy: Nastavení šířky okna ze stránky</span><span class="sxs-lookup"><span data-stu-id="36a33-102">How to: Set the Width of a Window from a Page</span></span>
<span data-ttu-id="36a33-103">Tento příklad ukazuje, jak nastavit šířku okna z <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="36a33-103">This example illustrates how to set the width of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36a33-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="36a33-104">Example</span></span>  
 <span data-ttu-id="36a33-105">A <xref:System.Windows.Controls.Page> šířku okna hostitele můžete nastavit tak, že nastavíte <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span><span class="sxs-lookup"><span data-stu-id="36a33-105">A <xref:System.Windows.Controls.Page> can set the width of its host window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span></span> <span data-ttu-id="36a33-106">Tato vlastnost umožňuje <xref:System.Windows.Controls.Page> nebudete chtít explicitní znalost typu hostitelského okna.</span><span class="sxs-lookup"><span data-stu-id="36a33-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36a33-107">Chcete-li nastavit šířku okna pomocí <xref:System.Windows.Controls.Page.WindowWidth%2A>, <xref:System.Windows.Controls.Page> musí být podřízené okno.</span><span class="sxs-lookup"><span data-stu-id="36a33-107">To set the width of a window using <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
