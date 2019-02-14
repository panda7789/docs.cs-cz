---
title: 'Postupy: Zajištění standardních položek nabídky pro formulář'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
ms.openlocfilehash: 823cc774e4bfd9ba94ea84efeda493b225a04a35
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260904"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a>Postupy: Zajištění standardních položek nabídky pro formulář
Můžete zadat standardní nabídky formuláře s <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.  
  
 Není k dispozici rozsáhlou podporu pro tuto funkci v sadě Visual Studio.  
  
 Viz také [názorný postup: Poskytnutí standardních položek nabídky formuláři](walkthrough-providing-standard-menu-items-to-a-form.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.MenuStrip> ovládacího prvku na formulář s standardní nabídky vytvořit. Výběr položky nabídky se zobrazí v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Ovládací prvek MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
