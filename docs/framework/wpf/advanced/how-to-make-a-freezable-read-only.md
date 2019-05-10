---
title: 'Postupy: Nastavení zablokovatelného objektu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 5748b7929db18578bbe00e3217b1578ac5fbc0f4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614594"
---
# <a name="how-to-make-a-freezable-read-only"></a>Postupy: Nastavení zablokovatelného objektu jen pro čtení
Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Freezable> voláním jen pro čtení jeho <xref:System.Windows.Freezable.Freeze%2A> metoda.  
  
 Nelze zmrazit <xref:System.Windows.Freezable> objektu, pokud je některý z následujících podmínek `true` o objektu:  
  
- Má animovat nebo data vázané vlastnosti.  
  
- Obsahuje vlastnosti, které určil institut NIST dynamický prostředek. Další informace o dynamické prostředky, najdete v článku [prostředky XAML](xaml-resources.md).  
  
- Obsahuje <xref:System.Windows.Freezable> podřízených objektů, které nelze zmrazit.  
  
 Pokud jsou tyto podmínky `false` pro vaše <xref:System.Windows.Freezable> objektů a vy nemáte v úmyslu upravit, vezměte v úvahu zmrazení to zlepší výkon.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se zablokuje <xref:System.Windows.Media.SolidColorBrush>, což je typ <xref:System.Windows.Freezable> objektu.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Další informace o <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Přehled zablokovatelných objektů](freezable-objects-overview.md)
- [Témata s postupy](base-elements-how-to-topics.md)
