---
title: 'Postupy: Přecházení zpět v historii navigace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 86590c2794339ac22cbc8ec5e11224736133e870
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817978"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="3deb5-102">Postupy: Přecházení zpět v historii navigace</span><span class="sxs-lookup"><span data-stu-id="3deb5-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="3deb5-103">Tento příklad ukazuje, jak přejít na položky v historii navigace zpět.</span><span class="sxs-lookup"><span data-stu-id="3deb5-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3deb5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3deb5-104">Example</span></span>  
 <span data-ttu-id="3deb5-105">Kód, který je spuštěn z obsahu, který je hostován <xref:System.Windows.Navigation.NavigationWindow>v <xref:System.Windows.Controls.Frame> , <xref:System.Windows.Navigation.NavigationService>pomocí nebo Internet Explorer, může přejít zpět prostřednictvím historie navigace, vždy po jednotlivých položkách.</span><span class="sxs-lookup"><span data-stu-id="3deb5-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService>, or Internet Explorer can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="3deb5-106">Navigace v rámci jedné položky vyžaduje nejprve kontrolu, zda jsou položky v historii navigace zpět, zkontrolováním vlastnosti **CanGoBack** před navigací zpětnou položkou voláním metody **GoBack** .</span><span class="sxs-lookup"><span data-stu-id="3deb5-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="3deb5-107">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3deb5-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="3deb5-108">**CanGoBack** a **GoBack** jsou implementovány <xref:System.Windows.Navigation.NavigationWindow>pomocí <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationService>a.</span><span class="sxs-lookup"><span data-stu-id="3deb5-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3deb5-109">Pokud zavoláte **GoBack**a v historii navigace zpět neexistují žádné položky, je <xref:System.InvalidOperationException> vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="3deb5-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
