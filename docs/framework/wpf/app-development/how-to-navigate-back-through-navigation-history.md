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
# <a name="how-to-navigate-back-through-navigation-history"></a>Postupy: Přecházení zpět v historii navigace
Tento příklad ukazuje, jak přejít na položky v historii navigace zpět.  
  
## <a name="example"></a>Příklad  
 Kód, který je spuštěn z obsahu, který je hostován <xref:System.Windows.Navigation.NavigationWindow>v <xref:System.Windows.Controls.Frame> , <xref:System.Windows.Navigation.NavigationService>pomocí nebo Internet Explorer, může přejít zpět prostřednictvím historie navigace, vždy po jednotlivých položkách.  
  
 Navigace v rámci jedné položky vyžaduje nejprve kontrolu, zda jsou položky v historii navigace zpět, zkontrolováním vlastnosti **CanGoBack** před navigací zpětnou položkou voláním metody **GoBack** . To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** a **GoBack** jsou implementovány <xref:System.Windows.Navigation.NavigationWindow>pomocí <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationService>a.  
  
> [!NOTE]
>  Pokud zavoláte **GoBack**a v historii navigace zpět neexistují žádné položky, je <xref:System.InvalidOperationException> vyvolána výjimka.
