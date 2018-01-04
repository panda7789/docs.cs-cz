---
title: 'Postupy: Animace ve stylu'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2aabe24b77a9016b5b8119646c80ea84eb73acb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-in-a-style"></a>Postupy: Animace ve stylu
Tento příklad ukazuje postup animace vlastnosti v rámci styl. Při animaci v rámci styl, pro který je definován styl jenom element framework můžete použít přímo. Pokud chcete zacílit zmrazitelné objekt, můžete musí "dot dolů" z vlastnosti stylem elementu.  
  
 V následujícím příkladu jsou definovány v rámci styl a použity pro několik animace <xref:System.Windows.Controls.Button>. Když se uživatel přesune na tlačítko myši, je oznámení neprůhledných a částečně průhledné pozadí znovu, opakovaně. Pokud se uživatel přesune mimo tlačítko myši, stane se zcela neprůhledný. Při kliknutí na tlačítko Barva jeho pozadí změní z oranžová bílé a zálohovat znovu. Protože <xref:System.Windows.Media.SolidColorBrush> použita k vyplnění tlačítko nemůžou být cílem přímo, je přístupný pomocí dotting dolů z tlačítka <xref:System.Windows.Controls.Control.Background%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 Všimněte si, že při animaci v rámci styl, je možné cílové objekty, které neexistují. Předpokládejme například, používá vaše styl <xref:System.Windows.Media.SolidColorBrush> nastavit vlastnost tlačítkem na pozadí, ale na některé bodu styl přepsáno a pozadí na tlačítko nastavena <xref:System.Windows.Media.LinearGradientBrush>.  Při pokusu o animace <xref:System.Windows.Media.SolidColorBrush> nebude vyvolat výjimku; animace se jednoduše nezdaří bez upozornění.  
  
 Další informace o storyboard cílení na syntaxi najdete v článku [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md). Další informace o animace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Další informace o styly najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).
