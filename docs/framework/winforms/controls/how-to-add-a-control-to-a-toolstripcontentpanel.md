---
title: "Postupy: Přidání ovládacího prvku do ToolStripContentPanel"
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
helpviewer_keywords: ToolStripContentPanel [Windows Forms], adding controls
ms.assetid: fa410960-bf1a-42fc-80e8-f2e27fb3dbb8
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 150dd8939077052d4e6d947925c047da0d0432c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-control-to-a-toolstripcontentpanel"></a>Postupy: Přidání ovládacího prvku do ToolStripContentPanel
Prostřednictvím kódu programu můžete přidat jeden nebo více ovládacích prvků k <xref:System.Windows.Forms.ToolStripContentPanel>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat <xref:System.Windows.Forms.RichTextBox> k <xref:System.Windows.Forms.ToolStripContentPanel>.  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad kódu vyžaduje:  
  
-   Odkazy na systém, System.Data a System.Windows.Forms sestavení.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění příklad kódu dokončení Windows Forms pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) nebo [ToolStripContainer úloh dialogové okno](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStripContentPanel>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [ToolStripContainer – ovládací prvek](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)  
 [ToolStrip – ovládací prvek](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
