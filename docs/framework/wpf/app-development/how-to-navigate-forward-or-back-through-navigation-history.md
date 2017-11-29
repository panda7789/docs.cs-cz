---
title: "Postupy: Přecházení vpřed a zpět v historii navigace"
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
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ad909af071d4006346d64ad8e4bd7b57c4eefad
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="98e63-102">Postupy: Přecházení vpřed a zpět v historii navigace</span><span class="sxs-lookup"><span data-stu-id="98e63-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="98e63-103">Tento příklad ukazuje, jak přejděte na položky v historii navigace dopředu a zpět.</span><span class="sxs-lookup"><span data-stu-id="98e63-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98e63-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="98e63-104">Example</span></span>  
 <span data-ttu-id="98e63-105">Kód, který spouští z obsahu v následující hostitelé můžete procházet dopředu a zpět historie navigace, jedna položka v čase.</span><span class="sxs-lookup"><span data-stu-id="98e63-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
-   <span data-ttu-id="98e63-106"><xref:System.Windows.Navigation.NavigationWindow>pomocí<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="98e63-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   <span data-ttu-id="98e63-107"><xref:System.Windows.Controls.Frame>pomocí<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="98e63-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="98e63-108">Než přejdete dopředného jednu položku, Nejdřív musíte zkontrolovat, že se položky v historii dopředného navigační zkontrolováním **CanGoForward** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="98e63-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="98e63-109">Pokud chcete přejít na dopředného jednu položku, zavoláte **GoForward** metoda.</span><span class="sxs-lookup"><span data-stu-id="98e63-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="98e63-110">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="98e63-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="98e63-111">Předtím, než můžete přejít zpět jednu položku, Nejdřív musíte zkontrolovat, že se položky v historii back navigační zkontrolováním **CanGoBack** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="98e63-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="98e63-112">Chcete-li přejít zpět jednu položku, zavolejte **GoBack** metoda.</span><span class="sxs-lookup"><span data-stu-id="98e63-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="98e63-113">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="98e63-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="98e63-114">**CanGoForward**, **GoForward**, **CanGoBack**, a **GoBack** jsou implementované <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="98e63-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98e63-115">Při volání **GoForward**, a nejsou žádné položky v historii dopředného navigace, nebo při volání **GoBack**, a v historii back navigace, nejsou žádné položky <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="98e63-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
