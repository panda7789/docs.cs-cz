---
title: Jak animace ve stylu (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: a455bbfb9defbcf83f7e490f60031917a3b41779
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540054"
---
# <a name="how-to-animate-in-a-style"></a>Jak animace ve stylu

Tento příklad ukazuje, jak animovat vlastnosti v rámci style. Při animace ve stylu, pro který je definován styl pouze element framework lze zacílit přímo. Cílit na zmrazitelný objekt, můžete musí "tečky dolů" z vlastnosti elementu stylem.

V následujícím příkladu jsou definovány ve stylu a použít pro animací několik <xref:System.Windows.Controls.Button>. Když se uživatel přesune ukazatel myši nad tlačítkem, je oznámení od neprůhledných částečně více průchody průsvitných a back znovu, opakovaně. Když se uživatel přesune ukazatel myši mimo tlačítko, stane se stane zcela neprůhledný. Při kliknutí na tlačítko změní barvu pozadí od oranžové na bílou a zpět. Protože <xref:System.Windows.Media.SolidColorBrush> používá k malování tlačítko nemůžou být cílem přímo, je k nim přistupovat pomocí dotting dolů z tlačítka <xref:System.Windows.Controls.Control.Background%2A> vlastnost.

## <a name="example"></a>Příklad

[!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

Všimněte si, že když animace ve stylu, je možné cílové objektů, které neexistují. Předpokládejme například, že používá vašemu stylu <xref:System.Windows.Media.SolidColorBrush> nastavit vlastnost tlačítka na pozadí, ale někdy styl přepsat a pozadí tlačítka nastaven <xref:System.Windows.Media.LinearGradientBrush>.  Při pokusu o animace <xref:System.Windows.Media.SolidColorBrush> nebude vyvolat výjimku; animace se jednoduše nezdaří bezobslužné.

Další informace o scénáře, které cílí na syntaxi najdete v článku [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md). Další informace o animace, najdete v článku [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Další informace o stylů, najdete v článku [styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md).
