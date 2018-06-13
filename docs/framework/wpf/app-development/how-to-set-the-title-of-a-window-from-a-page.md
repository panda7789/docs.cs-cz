---
title: 'Postupy: nastavení název časového období ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: e69812b59783717b7b9c832d4e8ab01ab42827c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546182"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Postupy: nastavení název časového období ze stránky
Tento příklad ukazuje, jak nastavit nadpis okna, ve kterém <xref:System.Windows.Controls.Page> je hostovaná.  
  
## <a name="example"></a>Příklad  
 Na stránce můžete změnit v záhlaví okna, který je hostitelem nastavením <xref:System.Windows.Controls.Page.WindowTitle%2A> vlastnosti, například takto:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Nastavení <xref:System.Windows.Controls.Page.Title%2A> vlastnosti stránky nezmění hodnota záhlaví okna. Místo toho <xref:System.Windows.Controls.Page.Title%2A> Určuje název položky stránky v historii navigace.
