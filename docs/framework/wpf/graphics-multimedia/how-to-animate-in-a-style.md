---
title: Postup animace ve stylu (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 617d41ca1c97463bf1c61c0d1e2728756fd8f1fb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459238"
---
# <a name="how-to-animate-in-a-style"></a>Postup animace ve stylu

Tento příklad ukazuje, jak animovat vlastnosti v rámci stylu. Při animování ve stylu je možné přímo cílit pouze na prvek rozhraní, pro který je definován styl. Chcete-li cílit na objekt Freezable, musíte "tečkou dolů" z vlastnosti elementu style.

V následujícím příkladu je několik animací definováno ve stylu a použito pro <xref:System.Windows.Controls.Button>. Když uživatel přesune ukazatel myši na tlačítko, zmizí z neprůhledných na částečně Průsvitný a zpátky znovu. Když uživatel přesune myš mimo tlačítko, stane se úplně neprůhledný. Po kliknutí na tlačítko se barva pozadí změní z oranžová na bílou a zpět. Vzhledem k tomu, že <xref:System.Windows.Media.SolidColorBrush> použitá k malování na tlačítko nelze cílit přímo, je k němu přistupovaná odvoláním z vlastnosti <xref:System.Windows.Controls.Control.Background%2A> tlačítka.

## <a name="example"></a>Příklad

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

Všimněte si, že při animování ve stylu je možné cílit na objekty, které neexistují. Předpokládejme například, že váš styl používá <xref:System.Windows.Media.SolidColorBrush> k nastavení vlastnosti pozadí tlačítka, ale v určitém okamžiku je styl přepsán a pozadí tlačítka je nastaveno pomocí <xref:System.Windows.Media.LinearGradientBrush>.  Při pokusu o animaci <xref:System.Windows.Media.SolidColorBrush> nevyvolá výjimku. animace se jednoduše nezdaří v tichém režimu.

Další informace o syntaxi cílící na scénář naleznete v [přehledu scénářů](storyboards-overview.md). Další informace o animacích najdete v [přehledu animace](animation-overview.md). Další informace o stylech naleznete v tématu [stylování a šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md).
