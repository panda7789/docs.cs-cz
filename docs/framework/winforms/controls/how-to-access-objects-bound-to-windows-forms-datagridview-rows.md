---
title: 'Postupy: Přístup k objektům připojeným k řádkům Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 72dc0c55a946bfa8ffc6f87bdbf353a20205185e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500596"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Postupy: Přístup k objektům připojeným k řádkům Windows Forms DataGridView
Někdy je užitečné zobrazit tabulku informací uložených v kolekci objektů firmy. Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> ovládacího prvku na takové shromažďování každé veřejné vlastnosti se zobrazí v jeho vlastní sloupec, pokud vlastnost byl označen mimo-nelze procházet s <xref:System.ComponentModel.BrowsableAttribute>. Například kolekce `Customer` objekty, jako má sloupce **název** a **adresu**.  
  
 Pokud tyto objekty obsahují další informace a kód, který chcete získat přístup, můžete k němu přistoupit pomocí objektů řádek. Uživatelé v následujícím příkladu kódu, můžete vybrat více řádků a klikněte na tlačítko si pošlete faktury ke každému odpovídající zákazníků.  
  
### <a name="to-access-row-bound-objects"></a>Pro přístup k objektům vázané na řádek  
  
-   Použití <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>Příklad  
 Příklad úplného kódu obsahuje jednoduchý `Customer` provádění a vytvoří vazbu <xref:System.Windows.Forms.DataGridView> do <xref:System.Collections.ArrayList> obsahuje několik `Customer` objekty. <xref:System.Windows.Forms.Control.Click> Obslužná rutina události <xref:System.Windows.Forms.Button?displayProperty=nameWithType> musí přejít `Customer` objekty přes řádky, protože není přístupná mimo kolekci zákazníků <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obslužné rutiny události.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)
