---
title: 'Postupy: Přístup k objektům v rozevíracím seznamu Windows Forms DataGridViewComboBoxCell'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 8df9ef1c30704c8b0d0dc7bbec48e53252cf9ae6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665874"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Postupy: Přístup k objektům v rozevíracím seznamu Windows Forms DataGridViewComboBoxCell
Podobně jako <xref:System.Windows.Forms.ComboBox> ovládací prvek, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a <xref:System.Windows.Forms.DataGridViewComboBoxCell> typy umožňují přidat libovolné objekty do rozevíracích seznamů. Pomocí této funkce může představovat komplexní státy v rozevíracím seznamu bez nutnosti mít uložené odpovídající objekty v samostatné kolekce.  
  
 Na rozdíl od <xref:System.Windows.Forms.ComboBox> ovládací prvek, <xref:System.Windows.Forms.DataGridView> typy nemají <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> vlastnost pro načtení aktuálně vybraného objektu. Místo toho je nutné nastavit <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> nastavte na název vlastnosti pro objekt vaší firmy. Když uživatel provede výběr, uvedené vlastnosti objektu obchodní nastaví buňku <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost.  
  
 K načtení objektu firmy prostřednictvím její hodnotu `ValueMember` vlastnost musíte uvést vlastnost, která vrátí odkaz na samotný objekt firmy. Proto pokud typ objektu obchodní není pod vaší kontrolou, je třeba přidat tato vlastnost rozšiřování typu prostřednictvím dědičnosti.  
  
 Následující postupy ukazují, jak naplnit rozevírací seznam pro obchodní objekty a načtení objektů prostřednictvím buňku <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>Chcete-li přidat objekty obchodní rozevíracího seznamu  
  
1. Vytvořte nový <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a naplnění jeho <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> kolekce. Alternativně můžete nastavit sloupci <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> vlastností do kolekce pro obchodní objekty. V takovém případě ale nemůže přidat "nepřiřazené" do rozevíracího seznamu bez vytvoření odpovídající obchodní objekt v kolekci.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. Nastavte <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> a <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> vlastnosti. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> Určuje vlastnost, která obchodního objektu, chcete-li zobrazit v rozevíracím seznamu. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> Určuje vlastnost, která vrátí odkaz na objekt firmy.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. Ujistěte se, že vaše obchodní typ objektu obsahuje vlastnost, která vrátí odkaz na aktuální instanci. Tato vlastnost musí mít název s hodnotou přiřazenou k <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> v předchozím kroku.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Aby se načetl objekt aktuálně vybrané obchodní  
  
- Získat buňku <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost a přetypujte ji pro obchodní typ objektu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Příklad  
 Kompletní příklad demonstruje použití obchodních objektů v rozevíracím seznamu. V příkladu <xref:System.Windows.Forms.DataGridView> ovládací prvek vázán na kolekci `Task` objekty. Každý `Task` objekt má `AssignedTo` vlastnost, která označuje `Employee` objekt aktuálně přiřazená k této úloze. `Assigned To` Sloupec zobrazuje `Name` přiřazené hodnota vlastnosti pro každý zaměstnanec, nebo "nepřiřazené", pokud `Task.AssignedTo` hodnota vlastnosti je `null`.  
  
 Chcete-li zobrazit chování tohoto příkladu, proveďte následující kroky:  
  
1. Změna přiřazení v `Assigned To` odvodit sloupec podle výběru různých hodnot z rozevíracích seznamů nebo stisknutím klávesy CTRL + 0 v buňce pole se seznamem.  
  
2. Klikněte na tlačítko `Generate Report` k zobrazení aktuálního přiřazení. To ukazuje, že změna `Assigned To` sloupce automaticky aktualizuje `tasks` kolekce.  
  
3. Klikněte na tlačítko `Request Status` tlačítka zavoláte `RequestStatus` metoda aktuálního `Employee` objekt pro tento řádek. Tento příklad ukazuje, že vybraný objekt se úspěšně načetl.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
