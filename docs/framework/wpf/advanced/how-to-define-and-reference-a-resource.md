---
title: 'Postupy: Definice a odkaz zdroje'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 89471c45aabd9f3415c45a2e8af41d1a52900324
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460171"
---
# <a name="how-to-define-and-reference-a-resource"></a>Postupy: Definice a odkaz zdroje

Tento příklad ukazuje, jak definovat prostředek a na něj odkazovat pomocí atributu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

## <a name="example"></a>Příklad

Následující příklad definuje dva typy prostředků: <xref:System.Windows.Media.SolidColorBrush> prostředek a několik prostředků <xref:System.Windows.Style>. `MyBrush` prostředků <xref:System.Windows.Media.SolidColorBrush> slouží k poskytnutí hodnoty pro několik vlastností, které každá z nich převezme hodnotu <xref:System.Windows.Media.Brush>ho typu. Prostředky <xref:System.Windows.Style> `PageBackground`, `TitleText` a `Label` každý cíl konkrétního typu ovládacího prvku. Styly nastavují různé vlastnosti pro cílené ovládací prvky, pokud je tento prostředek stylu odkazován klíčem prostředku a slouží k nastavení vlastnosti <xref:System.Windows.FrameworkElement.Style%2A> několika specifických elementů ovládacích prvků definovaných v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

Všimněte si, že jedna z vlastností v rámci setter stylu `Label` také odkazuje na dříve definovaný prostředek `MyBrush`. Toto je běžná technika, ale je důležité si uvědomit, že prostředky jsou analyzovány a zadány do slovníku prostředků v pořadí, v jakém jsou uvedeny. Prostředky, které se ve slovníku naleznou, taky vyžádají, pokud použijete [rozšíření značek StaticResource](staticresource-markup-extension.md) k odkazování v rámci jiného prostředku. Ujistěte se, že všechny prostředky, na které odkazujete, jsou definované dříve v rámci kolekce prostředků, než kde je tento prostředek požadován. V případě potřeby můžete obejít striktní pořadí vytváření odkazů na prostředky pomocí [rozšíření značek DynamicResource](dynamicresource-markup-extension.md) k odkazování prostředku za běhu, ale měli byste si uvědomit, že tato DynamicResource technika má výkon. výsledků. Podrobnosti najdete v tématu [prostředky XAML](xaml-resources.md).

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Viz také:

- [Prostředky XAML](xaml-resources.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
