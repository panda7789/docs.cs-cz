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
ms.openlocfilehash: 426f6c93433711ac72fe67eff2ee3006aa4d9166
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037136"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Postupy: Vyhledávání elementů generovaných objektem ControlTemplate
Tento příklad ukazuje, jak najít prvky, které jsou generovány <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, styl, který vytvoří jednoduchý <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button> třídy:  
  
 [!code-xaml[FindGeneratedItems#CT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Nalezení prvku v rámci šablony po použití šablony, můžete volat <xref:System.Windows.FrameworkTemplate.FindName%2A> metodu <xref:System.Windows.Controls.Control.Template%2A>. Následující příklad vytvoří okno se zprávou, která zobrazuje hodnota skutečné šířky <xref:System.Windows.Controls.Grid> v šabloně ovládacího prvku:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Viz také:

- [Hledání elementů generovaných šablonou DataTemplate](../data/how-to-find-datatemplate-generated-elements.md)
- [Styly a šablony](styling-and-templating.md)
- [Obory názvů WPF XAML](../advanced/wpf-xaml-namescopes.md)
- [Stromy v subsystému WPF](../advanced/trees-in-wpf.md)
