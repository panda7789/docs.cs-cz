---
title: 'Postupy: Nastavení názvu okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 0f618af89965822b0df96a264997dabd9cae7608
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940790"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Postupy: Nastavení názvu okna ze stránky
Tento příklad ukazuje, jak nastavit název okna, ve kterém <xref:System.Windows.Controls.Page> je hostovaný.  
  
## <a name="example"></a>Příklad  
 Stránka může změnit název okna, který je hostitelem, nastavením <xref:System.Windows.Controls.Page.WindowTitle%2A> vlastnosti, například takto:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
> <xref:System.Windows.Controls.Page.Title%2A> Nastavením vlastnosti stránky se nezmění hodnota názvu okna. Místo toho <xref:System.Windows.Controls.Page.Title%2A> Určuje název položky stránky v historii navigace.
