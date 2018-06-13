---
title: 'Postupy: přejděte zpátky pomocí historie navigace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 9acbc5d3388a8df0ec7d7b5326f449f092f0cb03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546667"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="aa211-102">Postupy: přejděte zpátky pomocí historie navigace</span><span class="sxs-lookup"><span data-stu-id="aa211-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="aa211-103">Tento příklad ukazuje, jak přejděte na položky zpět v historii navigace.</span><span class="sxs-lookup"><span data-stu-id="aa211-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa211-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa211-104">Example</span></span>  
 <span data-ttu-id="aa211-105">Kód, který je spuštěn z obsahu, který je hostován v <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> použít <xref:System.Windows.Navigation.NavigationService>, nebo [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] můžete přejít zpět pomocí historie navigace, jedna položka v čase.</span><span class="sxs-lookup"><span data-stu-id="aa211-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> use <xref:System.Windows.Navigation.NavigationService>, or [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="aa211-106">Navigační zpět jedna položka vyžaduje nejprve kontroluje, že se položky v historii back navigační zkontrolováním **CanGoBack** vlastnost, před voláním přejdete zpět jednu položku **GoBack** Metoda.</span><span class="sxs-lookup"><span data-stu-id="aa211-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="aa211-107">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="aa211-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="aa211-108">**CanGoBack** a **GoBack** jsou implementované <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="aa211-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa211-109">Při volání **GoBack**, a v historii back navigace, nejsou žádné položky <xref:System.InvalidOperationException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="aa211-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
