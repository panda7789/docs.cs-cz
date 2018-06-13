---
title: 'Postupy: Vytvoření reflexe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: c791dbbe02faaba790c650d482db092702730fa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560573"
---
# <a name="how-to-create-a-reflection"></a>Postupy: Vytvoření reflexe
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.VisualBrush> k vytvoření reflexe. Protože <xref:System.Windows.Media.VisualBrush> , můžete zobrazit stávající visual této funkci můžete použít k vytvoření zajímavé vizuální efekty, jako je například odrazů a zvětšení.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.VisualBrush> vytvořit odraz <xref:System.Windows.Controls.Border> obsahující několik elementy. Následující obrázek znázorňuje výstupu, který tento příklad vytvoří.  
  
 ![A projeví vizuální objekt](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Zrcadlený vizuální objekt  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Je kompletní ukázka, která obsahuje příklady, které ukazují, jak zvětšit části obrazovky a postup vytvoření odrazů, najdete v části [VisualBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160049).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.VisualBrush>  
 [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
