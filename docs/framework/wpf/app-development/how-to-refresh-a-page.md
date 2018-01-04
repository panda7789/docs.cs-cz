---
title: "Postupy: aktualizaci stránky."
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
- pages [WPF], refreshing
- refreshing pages [WPF]
ms.assetid: 06dd1bbd-81c4-40ad-ac0d-7a5b326b1465
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e250c8dbb04aa3c6dc5397c711a7f97a637f0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-refresh-a-page"></a>Postupy: aktualizaci stránky.
Tento příklad ukazuje způsob volání <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> metoda aktualizace v aktuálním obsahu <xref:System.Windows.Navigation.NavigationWindow>.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A>Aktualizuje aktuální obsah <xref:System.Windows.Navigation.NavigationWindow> na znovu načíst z její zdroj.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigaterefreshcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigaterefreshcode)]
