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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366657"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>Postupy: Přecházení vpřed a zpět v historii navigace
Tento příklad ukazuje, jak přejít na položky v historii pro navigaci vpřed nebo vzad.  
  
## <a name="example"></a>Příklad  
 Kód, který se spouští z obsahu následující hostitelů můžete přejít vpřed nebo vzad historii navigace, jedna položka v čase.  
  
-   <xref:System.Windows.Navigation.NavigationWindow> použití <xref:System.Windows.Navigation.NavigationService>  
  
-   <xref:System.Windows.Controls.Frame> použití <xref:System.Windows.Navigation.NavigationService>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 Předtím, než přejdete vpřed jednu položku, Nejdřív musíte zkontrolovat, zda jsou položky v historii navigace směrem vpřed zkontrolováním **CanGoForward** vlastnost. Pro navigaci vpřed jednu položku, můžete volat **GoForward** metody. To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 Předtím, než můžete přejít zpět jednu položku, musíte nejprve zkontrolujte, zda jsou položky v historii pro navigaci zpět zkontrolováním **CanGoBack** vlastnost. Přejít zpět jeden záznam, zavolejte **GoBack** metody. To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**, **GoForward**, **CanGoBack**, a **GoBack** implementují <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Při volání **GoForward**, a nejsou žádné záznamy v historii navigace směrem vpřed nebo při volání **GoBack**, a nejsou žádné záznamy v historii pro navigaci zpět <xref:System.InvalidOperationException> je vyvolána výjimka.
