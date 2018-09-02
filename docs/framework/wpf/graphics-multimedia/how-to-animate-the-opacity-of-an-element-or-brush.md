---
title: 'Postupy: Animace krytí elementu nebo štětce'
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: 549d3eab0d6d75403e962eeb146be8d7995cc931
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421799"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Postupy: Animace krytí elementu nebo štětce
Chcete-li prvek framework fade do zobrazení, lze animovat jeho <xref:System.Windows.UIElement.Opacity%2A> lze animovat vlastnost, nebo můžete <xref:System.Windows.Media.Brush.Opacity%2A> vlastnost <xref:System.Windows.Media.Brush> (nebo stopy) používá k malování ho. Animace krytí elementu umožňuje fade své podřízené objekty do a z zobrazení, ale štětce použít k vykreslení elementu animace umožňuje měli pečlivěji jaká část elementu sníží (zesvětlí). Například lze animovat neprůhlednost štětce použít k vykreslení pozadí tlačítka. To by způsobilo pozadí tlačítka, která má vyblednout a oddálení zobrazení, ale zároveň je nechává jeho textu v úplně neprůhledné.  
  
> [!NOTE]
>  Animace <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.Brush> nabízí v porovnání s animace použitím výkony těží <xref:System.Windows.UIElement.Opacity%2A> vlastnost elementu.  
  
 V následujícím příkladu jsou dvě tlačítka animovat tak, aby jejich fade do zobrazení. Neprůhlednost první <xref:System.Windows.Controls.Button> je animovaný z `1.0` k `0.0` přes <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pět sekund. Také je animovaný druhé tlačítko, ale krytí objektů SolidColorBrush používá k malování jeho <xref:System.Windows.Controls.Control.Background%2A> je animovaný místo krytí celý tlačítko. Při spuštění v příkladu na první tlačítko zcela sníží (zesvětlí) do zobrazení, zatímco sníží (zesvětlí) jenom na pozadí na druhé tlačítko do zobrazení. Jeho textu a okraj zůstanou úplně neprůhledné.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 Bylo vynecháno kód v tomto příkladu. Úplnou ukázku najdete postup animace krytí <xref:System.Windows.Media.Color> v rámci <xref:System.Windows.Media.LinearGradientBrush>.  Úplnou ukázku najdete v tématu [animace krytí elementu vzorku](https://go.microsoft.com/fwlink/?LinkID=159968).
