---
title: 'Postupy: Nastavení názvu okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 55444de6c61107979307b94910ba944e7001cf9e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357505"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Postupy: Nastavení názvu okna ze stránky
Tento příklad ukazuje, jak nastavit záhlaví okna, ve kterém <xref:System.Windows.Controls.Page> hostována.  
  
## <a name="example"></a>Příklad  
 Na stránce můžete změnit záhlaví okna, který je hostitelem tak, že nastavíte <xref:System.Windows.Controls.Page.WindowTitle%2A> vlastnost, takto:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Nastavení <xref:System.Windows.Controls.Page.Title%2A> vlastnosti stránky nezmění hodnotu záhlaví okna. Místo toho <xref:System.Windows.Controls.Page.Title%2A> Určuje název položky stránky v historii navigace.
