---
title: 'Postupy: Nastavení zablokovatelného režimu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 4185966d864be425bc631953461f6f27ab983bee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460067"
---
# <a name="how-to-make-a-freezable-read-only"></a>Postupy: Nastavení zablokovatelného režimu jen pro čtení
Tento příklad ukazuje, jak nastavit <xref:System.Windows.Freezable> jen pro čtení, voláním jeho metody <xref:System.Windows.Freezable.Freeze%2A>.  
  
 Objekt <xref:System.Windows.Freezable> nelze ukotvit, je-li některá z následujících podmínek `true` o objektu:  
  
- Obsahuje animované nebo vlastnosti vázaného na data.  
  
- Obsahuje vlastnosti, které jsou nastaveny dynamickým prostředkem. Další informace o dynamických prostředcích najdete v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Obsahuje <xref:System.Windows.Freezable> dílčích objektů, které nelze zmrazit.  
  
 Pokud jsou tyto podmínky `false` pro váš objekt <xref:System.Windows.Freezable> a nechcete ho upravovat, zvažte jeho zmrazení, abyste získali výhody výkonu.  
  
## <a name="example"></a>Příklad  
 Následující příklad zablokuje <xref:System.Windows.Media.SolidColorBrush>, což je typ objektu <xref:System.Windows.Freezable>.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Další informace o <xref:System.Windows.Freezable> objektů naleznete v tématu [Přehled objektů Freezable](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Přehled zablokovatelných objektů](freezable-objects-overview.md)
- [Témata s postupy](base-elements-how-to-topics.md)
