---
title: 'Postupy: nastavení výšku okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: e25bc3cf2f5de01177f79f671390bac39875d079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>Postupy: nastavení výšku okna ze stránky
Tento příklad ukazuje, jak nastavit výšku v okně <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Příklad  
 A <xref:System.Windows.Controls.Page> můžete nastavit výšku jeho hostitelské okno nastavením <xref:System.Windows.Controls.Page.WindowHeight%2A>. Tato vlastnost umožňuje <xref:System.Windows.Controls.Page> k nejsou explicitní znalostní báze typu hostitelského okna.  
  
> [!NOTE]
>  Chcete-li nastavit výšku okna pomocí <xref:System.Windows.Controls.Page.WindowHeight%2A>, <xref:System.Windows.Controls.Page> musí být podřízeným časového období.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
