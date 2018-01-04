---
title: "Postupy: Interaktivní používání vlastnosti Spring v prvku StatusStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c642b0c4cb2313d04bdca00294af791847e68c76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a>Postupy: Interaktivní používání vlastnosti Spring v prvku StatusStrip
Můžete použít <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost na pozici <xref:System.Windows.Forms.ToolStripStatusLabel> řídit ve <xref:System.Windows.Forms.StatusStrip> ovládacího prvku. <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Vlastnost určuje, zda <xref:System.Windows.Forms.ToolStripStatusLabel> řízení automaticky doplní dostupné místo na <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost na pozici <xref:System.Windows.Forms.ToolStripStatusLabel> řídit ve <xref:System.Windows.Forms.StatusStrip> ovládacího prvku. <xref:System.Windows.Forms.ToolStripItem.Click> Exkluzivní provede obslužné rutiny události – operace (XOR –) Chcete-li přepnout hodnotu nebo <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost.  
  
 Použijte tento příklad kódu, kompilovat, spusťte aplikaci a potom klikněte **střední (pružiny)** na <xref:System.Windows.Forms.StatusStrip> řízení přepnout hodnotu <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
