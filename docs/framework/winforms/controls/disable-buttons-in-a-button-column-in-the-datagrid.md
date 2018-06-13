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
ms.openlocfilehash: 957d5ebac7c8f6d7c1f4ce95e79e1918164db955
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529896"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Zahrnuje ovládací prvek <xref:System.Windows.Forms.DataGridViewButtonCell> třídu pro zobrazení buněk s uživatelské rozhraní (UI) jako tlačítko. Ale <xref:System.Windows.Forms.DataGridViewButtonCell> neposkytuje způsob, jak zakázat zobrazení tlačítka zobrazí buňky.  
  
 Následující příklad kódu ukazuje, jak přizpůsobit <xref:System.Windows.Forms.DataGridViewButtonCell> třída pro zobrazení tlačítka, která se může zobrazit zakázána. V příkladu definuje nový typ buňky, `DataGridViewDisableButtonCell`, která je odvozena od <xref:System.Windows.Forms.DataGridViewButtonCell>. Tento typ buňky poskytuje novou `Enabled` vlastnost, která může být nastaven na `false` k vykreslení zakázané tlačítko v buňce. Tento příklad také definuje nový typ sloupce, `DataGridViewDisableButtonColumn`, který zobrazí `DataGridViewDisableButtonCell` objekty. K předvedení této nové buňky a ve sloupci Typ, aktuální hodnota jednotlivých <xref:System.Windows.Forms.DataGridViewCheckBoxCell> v nadřízeném <xref:System.Windows.Forms.DataGridView> Určuje, zda `Enabled` vlastnost `DataGridViewDisableButtonCell` na stejném řádku je `true` nebo `false`.  
  
> [!NOTE]
>  Pokud odvozujete od <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy, je nutné přepsat `Clone` metoda kopírování nové vlastnosti během operací klonování. Měli byste také zavolat základní třídy `Clone` metoda tak, aby vlastnosti základní třídy jsou zkopírovány do nového buňky nebo sloupec.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Drawing, System.Windows.Forms a System.Windows.Forms.VisualStyles sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [Architektura ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
