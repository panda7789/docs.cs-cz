---
title: 'Postupy: Přecházení vpřed a zpět v historii navigace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: ac3b8b71b6adf04d71cf35edbb042b82c57d8e1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546263"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="29089-102">Postupy: Přecházení vpřed a zpět v historii navigace</span><span class="sxs-lookup"><span data-stu-id="29089-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="29089-103">Tento příklad ukazuje, jak přejděte na položky v historii navigace dopředu a zpět.</span><span class="sxs-lookup"><span data-stu-id="29089-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29089-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="29089-104">Example</span></span>  
 <span data-ttu-id="29089-105">Kód, který spouští z obsahu v následující hostitelé můžete procházet dopředu a zpět historie navigace, jedna položka v čase.</span><span class="sxs-lookup"><span data-stu-id="29089-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
-   <span data-ttu-id="29089-106"><xref:System.Windows.Navigation.NavigationWindow> Pomocí <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="29089-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   <span data-ttu-id="29089-107"><xref:System.Windows.Controls.Frame> Pomocí <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="29089-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="29089-108">Než přejdete dopředného jednu položku, Nejdřív musíte zkontrolovat, že se položky v historii dopředného navigační zkontrolováním **CanGoForward** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="29089-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="29089-109">Pokud chcete přejít na dopředného jednu položku, zavoláte **GoForward** metoda.</span><span class="sxs-lookup"><span data-stu-id="29089-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="29089-110">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="29089-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="29089-111">Předtím, než můžete přejít zpět jednu položku, Nejdřív musíte zkontrolovat, že se položky v historii back navigační zkontrolováním **CanGoBack** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="29089-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="29089-112">Chcete-li přejít zpět jednu položku, zavolejte **GoBack** metoda.</span><span class="sxs-lookup"><span data-stu-id="29089-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="29089-113">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="29089-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="29089-114">**CanGoForward**, **GoForward**, **CanGoBack**, a **GoBack** jsou implementované <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="29089-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29089-115">Při volání **GoForward**, a nejsou žádné položky v historii dopředného navigace, nebo při volání **GoBack**, a v historii back navigace, nejsou žádné položky <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="29089-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
