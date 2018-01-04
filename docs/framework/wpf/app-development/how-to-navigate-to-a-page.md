---
title: "Postupy: přejděte na stránku"
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
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31c8461febf72e4345e015c10e0f731fcfbb05e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-to-a-page"></a>Postupy: přejděte na stránku
Tento příklad znázorňuje několik způsobů, ve kterých lze na stránce procházet k z <xref:System.Windows.Navigation.NavigationWindow>.  
  
## <a name="example"></a>Příklad  
 Je možné, <xref:System.Windows.Navigation.NavigationWindow> přejděte na stránku pomocí jedné z následujících akcí:  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A> Vlastnost.  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> Metoda.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)]může být relativní nebo absolutní. Další informace najdete v tématu [Pack identifikátory URI v grafickém subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.NavigationService>
