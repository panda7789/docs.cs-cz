---
title: "Postupy: Nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci"
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
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8185adbf7d8979f03b3d0428fcc2ec0941c7999f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a>Postupy: Nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci
Můžete přizpůsobit vzhled vaší <xref:System.Windows.Forms.ToolStrip> řídí jednotlivě nebo pro všechny <xref:System.Windows.Forms.ToolStrip> ovládací prvky v aplikaci.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak selektivně používají vlastní zobrazovací jednotky k <xref:System.Windows.Forms.ToolStrip> řízení a <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.  
  
 Pokud chcete použít tento příklad kódu, kompilace a spusťte aplikaci a potom vyberte vlastní roztržení z oboru <xref:System.Windows.Forms.ComboBox> ovládacího prvku. Klikněte na tlačítko **použít** k nastavení vykreslovacího modulu.  
  
 Pokud chcete zobrazit vykreslování položky nabídky vlastní, vyberte <xref:System.Windows.Forms.MenuStrip> možnost z <xref:System.Windows.Forms.ComboBox> řídit, klikněte na tlačítko **použít**a pak otevřete **souboru** položku nabídky.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 Nastavit <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> použít vlastní zobrazovací jednotky pro všechny vlastnosti <xref:System.Windows.Forms.ToolStrip> ovládací prvky v aplikaci.  
  
 Nastavte <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost použít vlastní zobrazovací jednotky až k jednotlivcům <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
