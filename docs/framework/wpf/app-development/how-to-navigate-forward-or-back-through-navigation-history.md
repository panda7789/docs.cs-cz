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
ms.openlocfilehash: 85d3562246170901d83d6314caec5747d52fb9a0
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817961"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="2e2ae-102">Postupy: Přecházení vpřed a zpět v historii navigace</span><span class="sxs-lookup"><span data-stu-id="2e2ae-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="2e2ae-103">Tento příklad ukazuje, jak přejít vpřed nebo zpět k položkám v historii navigace.</span><span class="sxs-lookup"><span data-stu-id="2e2ae-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e2ae-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e2ae-104">Example</span></span>  
 <span data-ttu-id="2e2ae-105">Kód, který se spouští z obsahu na následujících hostitelích, může přejít vpřed nebo zpět prostřednictvím historie navigace, vždy po jednotlivých položkách.</span><span class="sxs-lookup"><span data-stu-id="2e2ae-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="2e2ae-106"><xref:System.Windows.Navigation.NavigationWindow>použití<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="2e2ae-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="2e2ae-107"><xref:System.Windows.Controls.Frame>použití<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="2e2ae-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="2e2ae-108">Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="2e2ae-108">Internet Explorer</span></span>  
  
 <span data-ttu-id="2e2ae-109">Než budete moct přejít na jednu položku vpřed, musíte nejdřív zkontrolovat, jestli jsou v historii navigace vpřed položky, a to kontrolou vlastnosti **CanGoForward** .</span><span class="sxs-lookup"><span data-stu-id="2e2ae-109">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="2e2ae-110">Chcete-li přejít o jednu položku vpřed, zavolejte metodu **GoForward** .</span><span class="sxs-lookup"><span data-stu-id="2e2ae-110">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="2e2ae-111">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2e2ae-111">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="2e2ae-112">Předtím, než budete moci přejít zpět na jednu položku, je třeba nejprve zkontrolovat, zda jsou položky v historii zpětné navigace zkontrolovány vlastností **CanGoBack** .</span><span class="sxs-lookup"><span data-stu-id="2e2ae-112">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="2e2ae-113">Chcete-li přejít zpět o jednu položku, zavolejte metodu **GoBack** .</span><span class="sxs-lookup"><span data-stu-id="2e2ae-113">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="2e2ae-114">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2e2ae-114">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="2e2ae-115">**CanGoForward**, **GoForward**, **CanGoBack**a **GoBack** jsou implementovány pomocí <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>a <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="2e2ae-115">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e2ae-116">Pokud zavoláte **GoForward**a neexistují žádné položky v historii navigace před přechodem nebo pokud volátea v <xref:System.InvalidOperationException> historii navigace neexistují žádné položky, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2e2ae-116">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
