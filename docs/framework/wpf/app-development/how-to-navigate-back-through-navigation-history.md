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
ms.openlocfilehash: c489a1593b3d1f22fe1ad6e648d3f8a3f7a6cd44
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377765"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Postupy: Přecházení zpět v historii navigace
Tento příklad ukazuje, jak přejít na položky zpět v historii navigace.  
  
## <a name="example"></a>Příklad  
 Kód, který je spuštěn z obsahu, který je hostován v <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> pomocí <xref:System.Windows.Navigation.NavigationService>, nebo [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] můžete přecházení zpět v historii navigace, jedna položka v čase.  
  
 Navigační zpět jedna položka vyžaduje nejprve kontroluje se, že jsou položky v historii pro navigaci zpět, že se podíváte **CanGoBack** vlastnost před voláním navigace zpět jednu položku **GoBack** Metoda. To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** a **GoBack** implementují <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Při volání **GoBack**, a nejsou žádné záznamy v historii pro navigaci zpět <xref:System.InvalidOperationException> je vyvolána.
