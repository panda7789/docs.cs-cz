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
ms.openlocfilehash: 8d8111e0c9c957e65232a261230fdeefc23012cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Postupy: Přístup k objektům připojeným k řádkům Windows Forms DataGridView
Někdy je užitečné zobrazit tabulku informací uložených v kolekci objektů firmy. Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> řízení takové shromažďování každé veřejné vlastnosti se zobrazí v vlastní sloupce, pokud vlastnost nebyl označen jiný procházet s <xref:System.ComponentModel.BrowsableAttribute>. Například kolekce `Customer` objekty by mít sloupce jako **název** a **adresu**.  
  
 Pokud tyto objekty obsahují další informace a kód, který chcete získat přístup, mohou být využity prostřednictvím řádek objekty. Uživatelé v následujícím příkladu kódu, můžete vybrat více řádků a klikněte na tlačítko pro odesílání pro všechny zákazníky odpovídající faktury.  
  
### <a name="to-access-row-bound-objects"></a>Pro přístup k objektům vázané na řádek  
  
-   Použití <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>Příklad  
 Úplný příklad kódu zahrnuje jednoduchou `Customer` implementaci a vazby <xref:System.Windows.Forms.DataGridView> k <xref:System.Collections.ArrayList> obsahuje několik `Customer` objekty. <xref:System.Windows.Forms.Control.Click> Obslužnou rutinu události <xref:System.Windows.Forms.Button?displayProperty=nameWithType> potřebuje přístup `Customer` objekty prostřednictvím řádky, protože není přístupný mimo kolekci zákazníka <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obslužné rutiny události.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)
