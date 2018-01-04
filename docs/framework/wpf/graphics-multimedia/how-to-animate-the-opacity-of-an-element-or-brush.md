---
title: "Postupy: Animace krytí elementu nebo štětce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3b750e6ee21c8347d3896ec290f0ff564cc0a2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Postupy: Animace krytí elementu nebo štětce
Chcete-li element framework objevovat a deaktivovat zobrazení, použije animaci jeho <xref:System.Windows.UIElement.Opacity%2A> vlastnost nebo je můžete animace <xref:System.Windows.Media.Brush.Opacity%2A> vlastnost <xref:System.Windows.Media.Brush> (nebo štětce) použita k vyplnění ho. Animace elementu krytí a její podřízené položky objevovat a deaktivovat zobrazení se však animace štětce použita k vyplnění elementu umožňuje být užší zmenšuje jaká část elementu. Například může animace krytí štětce použita k vyplnění tlačítkem na pozadí. To by způsobilo a odhlašování vykreslit zobrazení, a nechat textu jeho plně neprůhledného pozadí na tlačítko.  
  
> [!NOTE]
>  Animace <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.Brush> poskytuje výkonu výhod oproti animace <xref:System.Windows.UIElement.Opacity%2A> vlastnost elementu.  
  
 V následujícím příkladu jsou dvě tlačítka animované tak, aby se objevovat a deaktivovat zobrazení. Krytí první <xref:System.Windows.Controls.Button> je animovaný z `1.0` k `0.0` přes <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pět sekund. Tlačítko druhý je také animovaný, ale krytí SolidColorBrush – použita k vyplnění jeho <xref:System.Windows.Controls.Control.Background%2A> je animovaný místo krytí celý tlačítko. Při spuštění v příkladu, zmenšuje směřující zobrazení zcela na první tlačítko při jenom na pozadí na druhý tlačítko zmenšuje směřující zobrazení. Zůstávají plně neprůhledného jeho text a ohraničení.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 Z tohoto příkladu byla vynechána kódu. V celé ukázce také ukazuje, jak animace krytí <xref:System.Windows.Media.Color> v rámci <xref:System.Windows.Media.LinearGradientBrush>.  Pro úplnou ukázku najdete [animace krytí – ukázka prvky](http://go.microsoft.com/fwlink/?LinkID=159968).
