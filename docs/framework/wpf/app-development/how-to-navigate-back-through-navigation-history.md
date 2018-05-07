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
