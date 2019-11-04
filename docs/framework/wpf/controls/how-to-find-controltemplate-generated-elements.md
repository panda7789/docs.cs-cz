---
title: 'Postupy: Vyhledávání elementů generovaných objektem ControlTemplate'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: 232ee7d2859059591c9beff753f45781598a8127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460702"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Postupy: Vyhledávání elementů generovaných objektem ControlTemplate
Tento příklad ukazuje, jak najít prvky, které jsou generovány <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje styl, který vytvoří jednoduchý <xref:System.Windows.Controls.ControlTemplate> pro třídu <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[FindGeneratedItems#CT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Chcete-li najít element v šabloně po použití šablony, můžete zavolat metodu <xref:System.Windows.FrameworkTemplate.FindName%2A> <xref:System.Windows.Controls.Control.Template%2A>. Následující příklad vytvoří okno se zprávou, které zobrazuje skutečnou hodnotu šířky <xref:System.Windows.Controls.Grid> v rámci šablony ovládacího prvku:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Viz také:

- [Hledání elementů generovaných šablonou DataTemplate](../data/how-to-find-datatemplate-generated-elements.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Obory názvů WPF XAML](../advanced/wpf-xaml-namescopes.md)
- [Stromy v subsystému WPF](../advanced/trees-in-wpf.md)
