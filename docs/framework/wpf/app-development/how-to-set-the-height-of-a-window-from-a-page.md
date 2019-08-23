---
title: 'Postupy: Nastavení výšky okna ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c1041af88241011b51c96d7b61423344a32b25ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940804"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>Postupy: Nastavení výšky okna ze stránky
Tento příklad ukazuje, jak nastavit výšku okna z <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Příklad  
 Může nastavit výšku svého hostitelského okna <xref:System.Windows.Controls.Page.WindowHeight%2A>nastavením. <xref:System.Windows.Controls.Page> Tato vlastnost umožňuje, <xref:System.Windows.Controls.Page> aby nemusela explicitní znalosti typu okna, který je hostitelem.  
  
> [!NOTE]
> Chcete-li nastavit výšku okna pomocí <xref:System.Windows.Controls.Page.WindowHeight%2A> <xref:System.Windows.Controls.Page> , musí být podřízeným objektem okna.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
