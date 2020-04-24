---
title: 'Postupy: Definice a odkaz zdroje'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: e33c86b03d8b18113f3a15b3ab251753958ff5b2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646514"
---
# <a name="how-to-define-and-reference-a-resource"></a>Postupy: Definice a odkaz zdroje

Tento příklad ukazuje, jak definovat prostředek a odkazovat na něj pomocí atributu v aplikaci [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

## <a name="example"></a>Příklad

Následující příklad definuje dva typy prostředků: <xref:System.Windows.Media.SolidColorBrush> prostředek <xref:System.Windows.Style> a několik zdrojů. Prostředek <xref:System.Windows.Media.SolidColorBrush> `MyBrush` se používá k poskytnutí hodnoty několika vlastností, které každý z nich mít hodnotu <xref:System.Windows.Media.Brush> typu. `PageBackground`Prostředky <xref:System.Windows.Style> `TitleText` a `Label` každý cíl konkrétní typ ovládacího prvku. Styly nastavit různé vlastnosti na cílové ovládací prvky, když tento prostředek stylu odkazuje <xref:System.Windows.FrameworkElement.Style%2A> klíč prostředku a slouží [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]k nastavení vlastnosti několika specifických prvků ovládacího prvku definované v .

Všimněte si, že jedna z vlastností v `Label` nastavení `MyBrush` stylu také odkazuje na prostředek definovaný dříve. Jedná se o běžnou techniku, ale je důležité si uvědomit, že prostředky jsou analyzovány a zadány do slovníku prostředků v pořadí, ve které jsou uvedeny. Prostředky jsou také požadovány pořadí nalezené ve slovníku, pokud používáte [StaticResource Markup Extension](staticresource-markup-extension.md) odkazovat z v rámci jiného prostředku. Ujistěte se, že všechny prostředky, které odkazujete, je definován dříve v rámci kolekce prostředků, než kde je požadováno tento prostředek. V případě potřeby můžete obejít pořadí přísné ho vytvoření odkazů na prostředky pomocí [rozšíření dynamicResource Markup Extension](dynamicresource-markup-extension.md) odkazovat na prostředek za běhu místo, ale měli byste si být vědomi toho, že tato technika DynamicResource má důsledky výkonu. Podrobnosti naleznete v tématu [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Viz také

- [Zdroje XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
