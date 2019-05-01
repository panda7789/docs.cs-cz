---
title: 'Postupy: Nastavení výšky okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c99ea134478635f368b71443f43e4d8f772cb5aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007298"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>Postupy: Nastavení výšky okna ze stránky
Tento příklad ukazuje, jak nastavit výšku okna z <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Příklad  
 A <xref:System.Windows.Controls.Page> výšku okna hostitele můžete nastavit tak, že nastavíte <xref:System.Windows.Controls.Page.WindowHeight%2A>. Tato vlastnost umožňuje <xref:System.Windows.Controls.Page> nebudete chtít explicitní znalost typu hostitelského okna.  
  
> [!NOTE]
>  Chcete-li nastavit výšku okna pomocí <xref:System.Windows.Controls.Page.WindowHeight%2A>, <xref:System.Windows.Controls.Page> musí být podřízené okno.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
