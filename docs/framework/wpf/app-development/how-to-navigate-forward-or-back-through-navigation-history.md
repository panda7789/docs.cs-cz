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
ms.openlocfilehash: 4c20ebfab45a24cf34b1476fb94dae6913fb4d99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947755"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="aad16-102">Postupy: Přecházení vpřed a zpět v historii navigace</span><span class="sxs-lookup"><span data-stu-id="aad16-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="aad16-103">Tento příklad ukazuje, jak přejít na položky v historii pro navigaci vpřed nebo vzad.</span><span class="sxs-lookup"><span data-stu-id="aad16-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aad16-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="aad16-104">Example</span></span>  
 <span data-ttu-id="aad16-105">Kód, který se spouští z obsahu následující hostitelů můžete přejít vpřed nebo vzad historii navigace, jedna položka v čase.</span><span class="sxs-lookup"><span data-stu-id="aad16-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="aad16-106"><xref:System.Windows.Navigation.NavigationWindow> použití <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="aad16-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="aad16-107"><xref:System.Windows.Controls.Frame> použití <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="aad16-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="aad16-108">Předtím, než přejdete vpřed jednu položku, Nejdřív musíte zkontrolovat, zda jsou položky v historii navigace směrem vpřed zkontrolováním **CanGoForward** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aad16-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="aad16-109">Pro navigaci vpřed jednu položku, můžete volat **GoForward** metody.</span><span class="sxs-lookup"><span data-stu-id="aad16-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="aad16-110">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="aad16-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="aad16-111">Předtím, než můžete přejít zpět jednu položku, musíte nejprve zkontrolujte, zda jsou položky v historii pro navigaci zpět zkontrolováním **CanGoBack** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aad16-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="aad16-112">Přejít zpět jeden záznam, zavolejte **GoBack** metody.</span><span class="sxs-lookup"><span data-stu-id="aad16-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="aad16-113">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="aad16-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="aad16-114">**CanGoForward**, **GoForward**, **CanGoBack**, a **GoBack** implementují <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="aad16-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aad16-115">Při volání **GoForward**, a nejsou žádné záznamy v historii navigace směrem vpřed nebo při volání **GoBack**, a nejsou žádné záznamy v historii pro navigaci zpět <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="aad16-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
