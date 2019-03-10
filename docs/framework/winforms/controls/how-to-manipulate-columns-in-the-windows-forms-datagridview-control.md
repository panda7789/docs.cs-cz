---
title: 'Postupy: Manipulace se sloupci v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGridView control [Windows Forms], manipulating columns
- columns [Windows Forms], manipulating
- data grids [Windows Forms], manipulating columns
ms.assetid: d8cfe6b3-bbab-4182-bec2-0517d9f1eaf6
ms.openlocfilehash: 95d41093178c56c999ecfe515a380927513e715d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722448"
---
# <a name="how-to-manipulate-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Manipulace se sloupci v ovládacím prvku Windows Forms DataGridView

Následující příklad kódu ukazuje různé možnosti pro manipulaci s <xref:System.Windows.Forms.DataGridView> sloupců pomocí vlastnosti <xref:System.Windows.Forms.DataGridViewColumn> třídy.

## <a name="example"></a>Příklad

[!code-cpp[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CPP/DataGridViewColumnDemo.cpp#100)]
[!code-csharp[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CS/DataGridViewColumnDemo.cs#100)]
[!code-vb[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/VB/datagridviewcolumndemo.vb#100)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

- Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.

Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewBand>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView](programming-with-cells-rows-and-columns-in-the-datagrid.md)
