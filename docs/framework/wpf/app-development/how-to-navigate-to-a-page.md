---
title: 'Postupy: Přechod na stránku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: c8e808180682bfd97f397d8cadd1e4deafd7eb06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141047"
---
# <a name="how-to-navigate-to-a-page"></a>Postupy: Přechod na stránku
Tento příklad ukazuje několik způsobů, jimiž stránku se dá Navigovat z <xref:System.Windows.Navigation.NavigationWindow>.  
  
## <a name="example"></a>Příklad  
 Je možné, <xref:System.Windows.Navigation.NavigationWindow> přejít na stránku pomocí jedné z následujících akcí:  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A> Vlastnost.  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> Metody.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)] může být relativní nebo absolutní. Další informace najdete v tématu [identifikátory Pack URI v subsystému WPF](pack-uris-in-wpf.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
