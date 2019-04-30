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
ms.openlocfilehash: 87740a215136863199d962a2704cf691f27fc3bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776646"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Postupy: Vytvoření efektu přechodu použitím událostí
Tento příklad ukazuje, jak změnit barvu elementu a ukazatel myši přejde do opustí zabraná elementu.  
  
 Tento příklad se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor a soubor kódu na pozadí.  
  
> [!NOTE]
>  Tento příklad ukazuje, jak pomocí událostí, ale je doporučeným způsobem, jak tohoto stejného efektu dosáhnete tak použití <xref:System.Windows.Trigger> ve stylu. Další informace najdete v tématu [styly a šablony](../controls/styling-and-templating.md).  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří uživatelské rozhraní, který se skládá z <xref:System.Windows.Controls.Border> kolem <xref:System.Windows.Controls.TextBlock>a připojí <xref:System.Windows.Input.Mouse.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> obslužných rutin událostí k <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Následující kód vytvoří <xref:System.Windows.UIElement.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> obslužných rutin událostí.  Pokud kurzor myši vstoupí <xref:System.Windows.Controls.Border>, na pozadí <xref:System.Windows.Controls.Border> se změní na červený.  Pokud kurzor myši opustí <xref:System.Windows.Controls.Border>, na pozadí <xref:System.Windows.Controls.Border> se změní zpět na bílou.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
