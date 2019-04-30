---
title: Jak animace ve stylu (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 5fb18a2d927746c3437ec01d2a19327be373cae3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789282"
---
# <a name="how-to-animate-in-a-style"></a>Jak animace ve stylu

Tento příklad ukazuje, jak animovat vlastnosti v rámci style. Při animace ve stylu, pro který je definován styl pouze element framework lze zacílit přímo. Cílit na zmrazitelný objekt, můžete musí "tečky dolů" z vlastnosti elementu stylem.

V následujícím příkladu jsou definovány ve stylu a použít pro animací několik <xref:System.Windows.Controls.Button>. Když se uživatel přesune ukazatel myši nad tlačítkem, je oznámení od neprůhledných částečně více průchody průsvitných a back znovu, opakovaně. Když se uživatel přesune ukazatel myši mimo tlačítko, stane se stane zcela neprůhledný. Při kliknutí na tlačítko změní barvu pozadí od oranžové na bílou a zpět. Protože <xref:System.Windows.Media.SolidColorBrush> používá k malování tlačítko nemůžou být cílem přímo, je k nim přistupovat pomocí dotting dolů z tlačítka <xref:System.Windows.Controls.Control.Background%2A> vlastnost.

## <a name="example"></a>Příklad

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

Všimněte si, že když animace ve stylu, je možné cílové objektů, které neexistují. Předpokládejme například, že používá vašemu stylu <xref:System.Windows.Media.SolidColorBrush> nastavit vlastnost tlačítka na pozadí, ale někdy styl přepsat a pozadí tlačítka nastaven <xref:System.Windows.Media.LinearGradientBrush>.  Při pokusu o animace <xref:System.Windows.Media.SolidColorBrush> nebude vyvolat výjimku; animace se jednoduše nezdaří bezobslužné.

Další informace o scénáře, které cílí na syntaxi najdete v článku [přehled scénářů](storyboards-overview.md). Další informace o animace, najdete v článku [přehled animace](animation-overview.md). Další informace o stylů, najdete v článku [styly a šablony](../controls/styling-and-templating.md).
