---
title: 'Postupy: Animace krytí elementu nebo štětce'
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: 2f18861eb18f81b631245d1d933b7acb1b3e0e42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950503"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Postupy: Animace krytí elementu nebo štětce
Chcete-li nastavit, aby byl prvek architektury vymizet a mimo zobrazení, můžete <xref:System.Windows.UIElement.Opacity%2A> animovat jeho vlastnost nebo můžete <xref:System.Windows.Media.Brush.Opacity%2A> animovat vlastnost <xref:System.Windows.Media.Brush> (nebo štětce) použitou k malování. Animování neprůhlednosti prvku způsobí, že je a jeho podřízené objekty se zesílí a odchází z pohledu, ale animace štětce používaného k vykreslování elementu vám umožní být více selektivních, které části elementu zmizí. Můžete například animovat neprůhlednost štětce používaného k vykreslování pozadí tlačítka. To by způsobilo, že se pozadí tlačítka rozloží a zmizí, zatímco text zůstane zcela neprůhledný.  
  
> [!NOTE]
> Animování a <xref:System.Windows.Media.Brush> poskytuje výkonnostní <xref:System.Windows.UIElement.Opacity%2A> výhody před animováním vlastnosti prvku. <xref:System.Windows.Media.Brush.Opacity%2A>  
  
 V následujícím příkladu jsou dvě tlačítka animovaná, takže se objevují a odcházejí ze zobrazení. Neprůhlednost prvního <xref:System.Windows.Controls.Button> je animována z `1.0` na `0.0` více než <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pět sekund. Druhé tlačítko je také animováno, ale neprůhlednost SolidColorBrush, která se používá k vykreslování <xref:System.Windows.Controls.Control.Background%2A> , je animována, nikoliv neprůhlednost celého tlačítka. Když je tento příklad spuštěný, první tlačítko se úplně zesílí a zobrazí se z pohledu, zatímco na druhém tlačítku se rozchází a zmizí. Jeho text a ohraničení zůstane zcela neprůhledné.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#10](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 V tomto příkladu byl vynechán kód. Úplný vzorek také ukazuje, jak animovat neprůhlednost <xref:System.Windows.Media.Color> <xref:System.Windows.Media.LinearGradientBrush>v rámci.  Úplnou ukázku naleznete v tématu [animace neprůhlednosti vzorku elementu](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/OpacityAnimation).
