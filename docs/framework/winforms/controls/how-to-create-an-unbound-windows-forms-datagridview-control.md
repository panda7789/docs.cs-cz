---
title: 'Postupy: Vytvoření ovládacího prvku nevázaného Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: f4f36622d16ee7b1fcbd743f73e376283d04e76a
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261047"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a>Postupy: Vytvoření ovládacího prvku nevázaného Windows Forms DataGridView
Následující příklad kódu ukazuje, jak naplnit <xref:System.Windows.Forms.DataGridView> řízení prostřednictvím kódu programu bez vazby ke zdroji dat. To je užitečné, pokud máte malé množství dat, které chcete zobrazit ve formátu tabulky.  
  
 Úplné vysvětlení tento příklad kódu naleznete v tématu [názorný postup: Vytvoření nevázaného Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  

## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- [Návod: Vytvoření nevázaného Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
