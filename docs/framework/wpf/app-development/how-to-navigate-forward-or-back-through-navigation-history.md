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
ms.workload: dotnet
ms.openlocfilehash: 78fd9fec6a93c100da6b4e7174376a963ae8beb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>Postupy: Přecházení vpřed a zpět v historii navigace
Tento příklad ukazuje, jak přejděte na položky v historii navigace dopředu a zpět.  
  
## <a name="example"></a>Příklad  
 Kód, který spouští z obsahu v následující hostitelé můžete procházet dopředu a zpět historie navigace, jedna položka v čase.  
  
-   <xref:System.Windows.Navigation.NavigationWindow>pomocí<xref:System.Windows.Navigation.NavigationService>  
  
-   <xref:System.Windows.Controls.Frame>pomocí<xref:System.Windows.Navigation.NavigationService>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 Než přejdete dopředného jednu položku, Nejdřív musíte zkontrolovat, že se položky v historii dopředného navigační zkontrolováním **CanGoForward** vlastnost. Pokud chcete přejít na dopředného jednu položku, zavoláte **GoForward** metoda. To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 Předtím, než můžete přejít zpět jednu položku, Nejdřív musíte zkontrolovat, že se položky v historii back navigační zkontrolováním **CanGoBack** vlastnost. Chcete-li přejít zpět jednu položku, zavolejte **GoBack** metoda. To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**, **GoForward**, **CanGoBack**, a **GoBack** jsou implementované <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Při volání **GoForward**, a nejsou žádné položky v historii dopředného navigace, nebo při volání **GoBack**, a v historii back navigace, nejsou žádné položky <xref:System.InvalidOperationException> je vyvolána výjimka.
