---
title: 'Postupy: přechod na stránku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 25a0dbbc609c7b6f8f2878d2068e61e492a59c7e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582542"
---
# <a name="how-to-navigate-to-a-page"></a>Postupy: přechod na stránku
Tento příklad znázorňuje několik způsobů, jak lze na stránku přejít z <xref:System.Windows.Navigation.NavigationWindow>.  
  
## <a name="example"></a>Příklad  
 @No__t_0 může přejít na stránku pomocí jedné z následujících možností:  
  
- Vlastnost <xref:System.Windows.Navigation.NavigationWindow.Source%2A>.  
  
- Metoda <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A>.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
> Identifikátory URI (Uniform Resource Identifier) můžou být buď relativní, nebo absolutní. Další informace najdete v tématu [identifikátory URI Pack v](pack-uris-in-wpf.md)subsystému WPF.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
