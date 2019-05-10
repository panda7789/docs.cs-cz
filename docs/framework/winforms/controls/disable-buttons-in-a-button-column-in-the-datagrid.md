---
title: 'Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: b5a90270d398fd7b9304b0eba1b60d17d24d76fe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614845"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridViewButtonCell> třída pro zobrazování buňky pomocí uživatelského rozhraní (UI) jako tlačítko. Ale <xref:System.Windows.Forms.DataGridViewButtonCell> neposkytuje způsob, jak zakázat vzhled tlačítka zobrazený buňku.  
  
 Následující příklad kódu ukazuje, jak přizpůsobit <xref:System.Windows.Forms.DataGridViewButtonCell> třídy k zobrazení tlačítka, která se může objevit zakázán. Příklad definuje nový typ buňky `DataGridViewDisableButtonCell`, která je odvozena od <xref:System.Windows.Forms.DataGridViewButtonCell>. Tento typ buňky poskytuje novou `Enabled` vlastnost, která může být nastaven na `false` nakreslete zakázané tlačítko v buňce. Příklad také definuje nový typ sloupce, `DataGridViewDisableButtonColumn`, který zobrazí `DataGridViewDisableButtonCell` objekty. Abychom tuto novou buňku ve sloupci Typ, aktuální hodnota pro každou z <xref:System.Windows.Forms.DataGridViewCheckBoxCell> v nadřazeném prvku. <xref:System.Windows.Forms.DataGridView> Určuje, zda `Enabled` vlastnost `DataGridViewDisableButtonCell` na stejném řádku je `true` nebo `false`.  
  
> [!NOTE]
>  Pokud odvozujete od <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy, je nutné přepsat `Clone` metoda kopírování nové vlastnosti během operace klonování. Měli byste také zavolat základní třídu `Clone` metodu tak, aby vlastností základní třídy jsou zkopírovány do nové buňky nebo sloupec.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Drawing, System.Windows.Forms a System.Windows.Forms.VisualStyles.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:

- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
- [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
