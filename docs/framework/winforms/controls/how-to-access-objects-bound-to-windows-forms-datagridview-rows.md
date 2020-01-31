---
title: Přístup k objektům připojeným k řádkům DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743164"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Postupy: Přístup k objektům připojeným k řádkům Windows Forms DataGridView
Někdy je užitečné zobrazit tabulku informací uložených v kolekci obchodních objektů. Když svážete <xref:System.Windows.Forms.DataGridView> ovládací prvek s takovou kolekcí, každá veřejná vlastnost se zobrazí ve vlastním sloupci, pokud vlastnost není označena jako průchozí pomocí <xref:System.ComponentModel.BrowsableAttribute>. Například kolekce objektů `Customer` by měla obsahovat sloupce jako **jméno** a **adresa**.  
  
 Pokud tyto objekty obsahují další informace a kód, ke kterému chcete získat přístup, můžete k ní přistupovat prostřednictvím objektů řádků. V následujícím příkladu kódu mohou uživatelé vybrat více řádků a kliknutím na tlačítko odeslat fakturu každému z odpovídajících zákazníků.  
  
### <a name="to-access-row-bound-objects"></a>Přístup k objektům vázaným na řádek  
  
- Použijte vlastnost <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>Příklad  
 Úplný příklad kódu zahrnuje jednoduchou implementaci `Customer` a váže <xref:System.Windows.Forms.DataGridView> na <xref:System.Collections.ArrayList> obsahující několik objektů `Customer`. Obslužná rutina události <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.Button?displayProperty=nameWithType> musí přistupovat k objektům `Customer` prostřednictvím řádků, protože kolekce zákazníků není přístupná vně <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obslužné rutiny události.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
