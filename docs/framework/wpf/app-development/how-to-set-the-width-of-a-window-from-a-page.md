---
title: 'Postupy: Nastavení šířky okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: fee6d4c9ae9dae03e81cc4be56576763cb59958b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379351"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Postupy: Nastavení šířky okna ze stránky
Tento příklad ukazuje, jak nastavit šířku okna z <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Příklad  
 A <xref:System.Windows.Controls.Page> šířku okna hostitele můžete nastavit tak, že nastavíte <xref:System.Windows.Controls.Page.WindowWidth%2A>. Tato vlastnost umožňuje <xref:System.Windows.Controls.Page> nebudete chtít explicitní znalost typu hostitelského okna.  
  
> [!NOTE]
>  Chcete-li nastavit šířku okna pomocí <xref:System.Windows.Controls.Page.WindowWidth%2A>, <xref:System.Windows.Controls.Page> musí být podřízené okno.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
