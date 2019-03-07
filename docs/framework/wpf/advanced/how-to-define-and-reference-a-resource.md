---
title: 'Postupy: Definice a odkaz zdroje'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 80be1460906100072e6263c967c213df7968c705
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492059"
---
# <a name="how-to-define-and-reference-a-resource"></a>Postupy: Definice a odkaz zdroje

Tento příklad ukazuje, jak definovat prostředek a na něj odkazovat pomocí atributu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

## <a name="example"></a>Příklad

Následující příklad definuje dva typy prostředků: <xref:System.Windows.Media.SolidColorBrush> prostředků a několik <xref:System.Windows.Style> prostředky. <xref:System.Windows.Media.SolidColorBrush> Prostředků `MyBrush` slouží k poskytování hodnoty několik vlastností, že každá vzít <xref:System.Windows.Media.Brush> zadejte hodnotu. <xref:System.Windows.Style> Prostředky `PageBackground`, `TitleText` a `Label` každý cílový typ konkrétní ovládací prvek. Stylů širokou škálu různých vlastností nastavit na cílový ovládací prvky, když tento prostředek stylu odkazuje klíč prostředku a slouží k nastavení <xref:System.Windows.FrameworkElement.Style%2A> vlastnost několik konkrétní ovládací prvky definované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

V rámci elementů setter ze Poznámka, že jedna z vlastností `Label` styl také odkazuje `MyBrush` prostředek definovaný dříve. Toto je běžná technika, ale je dobré si uvědomit, že jsou analyzovány a zadat do slovníku prostředků v pořadí, ve kterém jsou uvedeny prostředky. Prostředky jsou také požadovaná podle pořadí, v rámci slovníku nebyl nalezen používáte [– rozšíření značek StaticResource](staticresource-markup-extension.md) odkazovat z v rámci jiného prostředku. Ujistěte se, že je prostředek, který budete odkazovat na dříve definována v rámci kolekci prostředků než ve kterém je tento prostředek pak požadovaný. Pokud nezbytné, můžete alternativně vyřešit striktní vytváření pořadí reference na prostředky s využitím [DynamicResource – rozšíření značek](dynamicresource-markup-extension.md) odkazovat prostředků v době běhu místo toho ale byste měli vědět, který tento DynamicResource Metoda má důsledky výkonu. Podrobnosti najdete v tématu [prostředky XAML](xaml-resources.md).

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Viz také:

- [Prostředky XAML](xaml-resources.md)
- [Styly a šablony](../controls/styling-and-templating.md)
