---
title: 'Postupy: přejděte na stránku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 896287376979d40816e3937fff77b38bf71a62f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548385"
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
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)] může být relativní nebo absolutní. Další informace najdete v tématu [Pack identifikátory URI v grafickém subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.NavigationService>
