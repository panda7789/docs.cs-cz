---
title: 'Postupy: Vytvoření efektu přechodu použitím událostí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 806056397200fa5c567e83227499ba721544f523
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005177"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Postupy: Vytvoření efektu přechodu použitím událostí
Tento příklad ukazuje, jak změnit barvu prvku jako ukazatel myši do umístění a ponechání oblasti obsazené prvkem.  
  
 Tento příklad se skládá ze souboru [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a souboru kódu na pozadí.  
  
> [!NOTE]
> Tento příklad ukazuje, jak použít události, ale doporučený způsob dosažení stejného efektu je použití <xref:System.Windows.Trigger> ve stylu. Další informace najdete v tématu [stylování a šablonování](../controls/styling-and-templating.md).  
  
## <a name="example"></a>Příklad  
 Následující kód XAML vytvoří uživatelské rozhraní, které se skládá z <xref:System.Windows.Controls.Border> kolem <xref:System.Windows.Controls.TextBlock> a připojí obslužné rutiny událostí <xref:System.Windows.Input.Mouse.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> k <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Následující kód na pozadí vytvoří obslužné rutiny událostí <xref:System.Windows.UIElement.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave>.  Když ukazatel myši vstoupí do <xref:System.Windows.Controls.Border>, pozadí <xref:System.Windows.Controls.Border> se změní na červenou.  Když ukazatel myši opustí <xref:System.Windows.Controls.Border>, pozadí <xref:System.Windows.Controls.Border> se změní zpět na bílou.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
