---
title: 'Postupy: Nastavení šířky okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: 1e16b75ecb85550facdf24a5b9e341cf0c061178
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940767"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Postupy: Nastavení šířky okna ze stránky
Tento příklad ukazuje, jak nastavit šířku okna z <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Příklad  
 Může nastavit šířku okna <xref:System.Windows.Controls.Page.WindowWidth%2A>hostitele nastavením. <xref:System.Windows.Controls.Page> Tato vlastnost umožňuje, <xref:System.Windows.Controls.Page> aby nemusela explicitní znalosti typu okna, který je hostitelem.  
  
> [!NOTE]
> Chcete-li nastavit šířku okna pomocí <xref:System.Windows.Controls.Page.WindowWidth%2A> <xref:System.Windows.Controls.Page> , musí být podřízeným objektem okna.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
