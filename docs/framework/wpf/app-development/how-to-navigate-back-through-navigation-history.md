---
title: 'Postupy: přecházení zpět v historii navigace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 7266c9486524e962a859c34c9be5ab8f6d7bf7d5
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46322230"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="67b93-102">Postupy: přecházení zpět v historii navigace</span><span class="sxs-lookup"><span data-stu-id="67b93-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="67b93-103">Tento příklad ukazuje, jak přejít na položky zpět v historii navigace.</span><span class="sxs-lookup"><span data-stu-id="67b93-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67b93-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="67b93-104">Example</span></span>  
 <span data-ttu-id="67b93-105">Kód, který je spuštěn z obsahu, který je hostován v <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> pomocí <xref:System.Windows.Navigation.NavigationService>, nebo [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] můžete přecházení zpět v historii navigace, jedna položka v čase.</span><span class="sxs-lookup"><span data-stu-id="67b93-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService>, or [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="67b93-106">Navigační zpět jedna položka vyžaduje nejprve kontroluje se, že jsou položky v historii pro navigaci zpět, že se podíváte **CanGoBack** vlastnost před voláním navigace zpět jednu položku **GoBack** Metoda.</span><span class="sxs-lookup"><span data-stu-id="67b93-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="67b93-107">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="67b93-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="67b93-108">**CanGoBack** a **GoBack** implementují <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="67b93-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67b93-109">Při volání **GoBack**, a nejsou žádné záznamy v historii pro navigaci zpět <xref:System.InvalidOperationException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="67b93-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
