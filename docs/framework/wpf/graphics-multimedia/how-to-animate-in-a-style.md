---
title: 'Postupy: Animace ve stylu'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: e0741a869ab81875aaa25340de851ef939e11a6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558810"
---
# <a name="how-to-animate-in-a-style"></a>Postupy: Animace ve stylu
Tento příklad ukazuje postup animace vlastnosti v rámci styl. Při animaci v rámci styl, pro který je definován styl jenom element framework můžete použít přímo. Pokud chcete zacílit zmrazitelné objekt, můžete musí "dot dolů" z vlastnosti stylem elementu.  
  
 V následujícím příkladu jsou definovány v rámci styl a použity pro několik animace <xref:System.Windows.Controls.Button>. Když se uživatel přesune na tlačítko myši, je oznámení neprůhledných a částečně průhledné pozadí znovu, opakovaně. Pokud se uživatel přesune mimo tlačítko myši, stane se zcela neprůhledný. Při kliknutí na tlačítko Barva jeho pozadí změní z oranžová bílé a zálohovat znovu. Protože <xref:System.Windows.Media.SolidColorBrush> použita k vyplnění tlačítko nemůžou být cílem přímo, je přístupný pomocí dotting dolů z tlačítka <xref:System.Windows.Controls.Control.Background%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 Všimněte si, že při animaci v rámci styl, je možné cílové objekty, které neexistují. Předpokládejme například, používá vaše styl <xref:System.Windows.Media.SolidColorBrush> nastavit vlastnost tlačítkem na pozadí, ale na některé bodu styl přepsáno a pozadí na tlačítko nastavena <xref:System.Windows.Media.LinearGradientBrush>.  Při pokusu o animace <xref:System.Windows.Media.SolidColorBrush> nebude vyvolat výjimku; animace se jednoduše nezdaří bez upozornění.  
  
 Další informace o storyboard cílení na syntaxi najdete v článku [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md). Další informace o animace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Další informace o styly najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).
