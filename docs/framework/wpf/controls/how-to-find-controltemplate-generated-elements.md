---
title: "Postupy: Vyhledávání elementů generovaných objektem ControlTemplate"
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
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4e06de393fa9020277d01f24a332cddb9683bce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Postupy: Vyhledávání elementů generovaných objektem ControlTemplate
Tento příklad ukazuje, jak najít prvky, které jsou generované <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje styl, který vytvoří jednoduchou <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button> třídy:  
  
 [!code-xaml[FindGeneratedItems#CT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Chcete-li po použití šablony při vyhledávání prvku v rámci šablony, můžete zavolat <xref:System.Windows.FrameworkTemplate.FindName%2A> metodu <xref:System.Windows.Controls.Control.Template%2A>. Následující příklad vytvoří okno se zprávou, který se zobrazuje hodnota skutečná šířka <xref:System.Windows.Controls.Grid> v rámci šablony ovládacího prvku:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Viz také  
 [Hledání elementů generovaných šablonou DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Obory názvů WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [Stromy v subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
