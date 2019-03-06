---
title: 'Postupy: Použití vlastností roztažení na obsah viewbox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StretchDirection properties [WPF]
- Stretch properties [WPF]
- controls [WPF], Viewbox
- Viewbox control [WPF]
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
ms.openlocfilehash: 96d6584debe3e0dc85121cbcde5e6b4d1ac8c75c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352475"
---
# <a name="how-to-apply-stretch-properties-to-the-contents-of-a-viewbox"></a>Postupy: Použití vlastností roztažení na obsah viewbox
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak změnit hodnotu <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> a <xref:System.Windows.Controls.Viewbox.Stretch%2A> vlastnosti <xref:System.Windows.Controls.Viewbox>.  
  
 První příklad používá [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k definování <xref:System.Windows.Controls.Viewbox> elementu. Přiřadí <xref:System.Windows.FrameworkElement.MaxWidth%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> 400. Příklad používá vnořené <xref:System.Windows.Controls.Image> element v rámci <xref:System.Windows.Controls.Viewbox>. <xref:System.Windows.Controls.Button> prvky, které odpovídají hodnotám vlastností pro <xref:System.Windows.Controls.Viewbox.Stretch%2A> a <xref:System.Windows.Controls.StretchDirection> výčty manipulovat s roztažení chování ve vnořeném <xref:System.Windows.Controls.Image>.  
  
 [!code-xaml[viewboxStretchLayoutSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 Tyto popisovače souborů použití modelu code-behind <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události, která předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad definuje.  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.Viewbox>
- <xref:System.Windows.Media.Stretch>
- <xref:System.Windows.Controls.StretchDirection>
