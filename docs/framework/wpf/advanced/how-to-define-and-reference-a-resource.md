---
title: 'Postupy: Definice a odkaz zdroje'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 347804f0ce6dd3b907d3ac088248a64569a63695
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543491"
---
# <a name="how-to-define-and-reference-a-resource"></a>Postupy: Definice a odkaz zdroje
Tento příklad ukazuje, jak definovat prostředku a odkazovat pomocí atributu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje dva typy prostředků: <xref:System.Windows.Media.SolidColorBrush> prostředků a několik <xref:System.Windows.Style> prostředky. <xref:System.Windows.Media.SolidColorBrush> Prostředků `MyBrush` slouží k poskytování hodnotu několik vlastností, že každý trvat <xref:System.Windows.Media.Brush> zadejte hodnotu. <xref:System.Windows.Style> Prostředky `PageBackground`, `TitleText` a `Label` každý cílí na určitý ovládací prvek typu. Styly nastavit celou řadu jiné vlastnosti na cílové ovládacích prvků, když styl prostředku je odkazován objektem klíč prostředku a slouží k nastavení <xref:System.Windows.FrameworkElement.Style%2A> vlastnost několik konkrétní ovládací prvky, které jsou definované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Všimněte si, že jedna z vlastností v rámci nastavením `Label` styl také odkazuje `MyBrush` prostředků definovaného dříve. To je běžné technika, ale je důležité si pamatovat, že jsou analyzovat a zadán do slovník prostředků, a pořadí, které jsou uvedené prostředky. Prostředky jsou také požadoval pořadí v rámci slovníku nalezen, pokud použijete [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) Chcete-li je ze v rámci jiný prostředek. Ujistěte se, že jakémukoli prostředku, který odkazujete je definována dříve v rámci kolekce prostředků než kde je pak požadovaný prostředku. Pokud potřeby můžete obejít pořadí striktní vytváření prostředků refererences pomocí [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) tak, aby odkazovaly prostředků v době běhu místo toho byste měli vědět, ale který tento DynamicResource technika má důsledky výkonu. Podrobnosti najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a>Viz také  
 [Prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
