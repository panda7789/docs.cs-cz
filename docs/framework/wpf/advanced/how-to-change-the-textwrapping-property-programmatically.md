---
title: "Postupy: Změna vlastnosti TextWrapping z programu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 74ddcf55c8918602ecac866913f2007da143f443
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>Postupy: Změna vlastnosti TextWrapping z programu
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak změnit hodnotu <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> vlastnost prostřednictvím kódu programu.  
  
 Tři <xref:System.Windows.Controls.Button> elementy jsou umístěny v rámci <xref:System.Windows.Controls.StackPanel> element v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Každý <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí pro <xref:System.Windows.Controls.Button> odpovídá obslužnou rutinu v kódu. Obslužné rutiny událostí používají stejný název jako <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> hodnotu, použijí se na `txt2` při kliknutí na tlačítko. Navíc text v `txt1` ( <xref:System.Windows.Controls.TextBlock> to není znázorněné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) se aktualizuje, aby odrážely změny ve vlastnosti.  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>  
 <xref:System.Windows.TextWrapping>
