---
title: "Postupy: nastavení šířky okna ze stránky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc9843d4a0f76547b76698a9686b5c4936baa322
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Postupy: nastavení šířky okna ze stránky
Tento příklad ukazuje, jak nastavit šířku v okně <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Příklad  
 A <xref:System.Windows.Controls.Page> můžete nastavit šířku jeho hostitelské okno nastavením <xref:System.Windows.Controls.Page.WindowWidth%2A>. Tato vlastnost umožňuje <xref:System.Windows.Controls.Page> k nejsou explicitní znalostní báze typu hostitelského okna.  
  
> [!NOTE]
>  Chcete-li nastavit šířku okna pomocí <xref:System.Windows.Controls.Page.WindowWidth%2A>, <xref:System.Windows.Controls.Page> musí být podřízeným časového období.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
