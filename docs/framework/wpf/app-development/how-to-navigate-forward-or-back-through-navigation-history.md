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
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>Postupy: Přecházení vpřed a zpět v historii navigace
Tento příklad ukazuje, jak přejít vpřed nebo zpět k položkám v historii navigace.  
  
## <a name="example"></a>Příklad  
 Kód, který se spouští z obsahu na následujících hostitelích, může přejít vpřed nebo zpět prostřednictvím historie navigace, vždy po jednotlivých položkách.  
  
- <xref:System.Windows.Navigation.NavigationWindow>použití<xref:System.Windows.Navigation.NavigationService>  
  
- <xref:System.Windows.Controls.Frame>použití<xref:System.Windows.Navigation.NavigationService>  
  
- Internet Explorer  
  
 Než budete moct přejít na jednu položku vpřed, musíte nejdřív zkontrolovat, jestli jsou v historii navigace vpřed položky, a to kontrolou vlastnosti **CanGoForward** . Chcete-li přejít o jednu položku vpřed, zavolejte metodu **GoForward** . To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 Předtím, než budete moci přejít zpět na jednu položku, je třeba nejprve zkontrolovat, zda jsou položky v historii zpětné navigace zkontrolovány vlastností **CanGoBack** . Chcete-li přejít zpět o jednu položku, zavolejte metodu **GoBack** . To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**, **GoForward**, **CanGoBack**a **GoBack** jsou implementovány pomocí <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>a <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Pokud zavoláte **GoForward**a neexistují žádné položky v historii navigace před přechodem nebo pokud volátea v <xref:System.InvalidOperationException> historii navigace neexistují žádné položky, je vyvolána výjimka.
