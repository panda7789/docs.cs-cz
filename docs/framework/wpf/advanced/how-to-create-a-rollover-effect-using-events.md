---
title: "Postupy: Vytvoření efektu přechodu použitím událostí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c82d993c31174419793319da74ffa38d122ef203
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Postupy: Vytvoření efektu přechodu použitím událostí
Tento příklad ukazuje, jak změnit barvu elementu jako ukazatel myši vstoupí do a z oblasti obsazena elementu.  
  
 V tomto příkladu se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a soubor kódu.  
  
> [!NOTE]
>  Tento příklad ukazuje, jak používat události, ale je doporučeným způsobem, jak dosáhnout Tento stejný účinek použití <xref:System.Windows.Trigger> ve stylu. Další informace najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří uživatelské rozhraní, který se skládá z <xref:System.Windows.Controls.Border> kolem <xref:System.Windows.Controls.TextBlock>a připojí <xref:System.Windows.Input.Mouse.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> obslužné rutiny událostí k <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Následující kód vytvoří <xref:System.Windows.UIElement.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> obslužné rutiny událostí.  Pokud se ukazatel myši vstoupí <xref:System.Windows.Controls.Border>, pozadí <xref:System.Windows.Controls.Border> se změní na červený.  Pokud se ukazatel myši opustí <xref:System.Windows.Controls.Border>, pozadí <xref:System.Windows.Controls.Border> se změní zpět na prázdné.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
