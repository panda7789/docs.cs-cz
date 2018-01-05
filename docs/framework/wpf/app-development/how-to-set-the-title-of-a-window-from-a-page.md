---
title: "Postupy: nastavení název časového období ze stránky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11f33eede479e090a78bffe841d7998e03eab6c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Postupy: nastavení název časového období ze stránky
Tento příklad ukazuje, jak nastavit nadpis okna, ve kterém <xref:System.Windows.Controls.Page> je hostovaná.  
  
## <a name="example"></a>Příklad  
 Na stránce můžete změnit v záhlaví okna, který je hostitelem nastavením <xref:System.Windows.Controls.Page.WindowTitle%2A> vlastnosti, například takto:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Nastavení <xref:System.Windows.Controls.Page.Title%2A> vlastnosti stránky nezmění hodnota záhlaví okna. Místo toho <xref:System.Windows.Controls.Page.Title%2A> Určuje název položky stránky v historii navigace.
