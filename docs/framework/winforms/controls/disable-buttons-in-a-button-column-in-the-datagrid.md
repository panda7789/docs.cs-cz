---
title: 'Postupy: Zakázat tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: dc92ed2ee7710d6a05cb14fa0cd28606a9a399b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726335"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Postupy: Zakázat tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridViewButtonCell> třída pro zobrazování buňky pomocí uživatelského rozhraní (UI) jako tlačítko. Ale <xref:System.Windows.Forms.DataGridViewButtonCell> neposkytuje způsob, jak zakázat vzhled tlačítka zobrazený buňku.  
  
 Následující příklad kódu ukazuje, jak přizpůsobit <xref:System.Windows.Forms.DataGridViewButtonCell> třídy k zobrazení tlačítka, která se může objevit zakázán. Příklad definuje nový typ buňky `DataGridViewDisableButtonCell`, která je odvozena od <xref:System.Windows.Forms.DataGridViewButtonCell>. Tento typ buňky poskytuje novou `Enabled` vlastnost, která může být nastaven na `false` nakreslete zakázané tlačítko v buňce. Příklad také definuje nový typ sloupce, `DataGridViewDisableButtonColumn`, který zobrazí `DataGridViewDisableButtonCell` objekty. Abychom tuto novou buňku ve sloupci Typ, aktuální hodnota pro každou z <xref:System.Windows.Forms.DataGridViewCheckBoxCell> v nadřazeném prvku. <xref:System.Windows.Forms.DataGridView> Určuje, zda `Enabled` vlastnost `DataGridViewDisableButtonCell` na stejném řádku je `true` nebo `false`.  
  
> [!NOTE]
>  Pokud odvozujete od <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy, je nutné přepsat `Clone` metoda kopírování nové vlastnosti během operace klonování. Měli byste také zavolat základní třídu `Clone` metodu tak, aby vlastností základní třídy jsou zkopírovány do nové buňky nebo sloupec.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing, System.Windows.Forms a System.Windows.Forms.VisualStyles.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také:
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
- [Architektura ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
