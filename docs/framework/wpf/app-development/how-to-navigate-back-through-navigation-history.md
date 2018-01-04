---
title: "Postupy: přejděte zpátky pomocí historie navigace"
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
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3bfc809dbe76c17859cb3fcd83f8a293a24b308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Postupy: přejděte zpátky pomocí historie navigace
Tento příklad ukazuje, jak přejděte na položky zpět v historii navigace.  
  
## <a name="example"></a>Příklad  
 Kód, který je spuštěn z obsahu, který je hostován v <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> použít <xref:System.Windows.Navigation.NavigationService>, nebo [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] můžete přejít zpět pomocí historie navigace, jedna položka v čase.  
  
 Navigační zpět jedna položka vyžaduje nejprve kontroluje, že se položky v historii back navigační zkontrolováním **CanGoBack** vlastnost, před voláním přejdete zpět jednu položku **GoBack** Metoda. To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** a **GoBack** jsou implementované <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Při volání **GoBack**, a v historii back navigace, nejsou žádné položky <xref:System.InvalidOperationException> je vyvolána.
