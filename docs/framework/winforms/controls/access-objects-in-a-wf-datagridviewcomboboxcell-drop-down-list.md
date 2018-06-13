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
ms.openlocfilehash: 2758841031be9ca9f0a5eb5e57165191d6870e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529399"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Postupy: Přístup k objektům v rozevíracím seznamu Windows Forms DataGridViewComboBoxCell
Podobně jako <xref:System.Windows.Forms.ComboBox> ovládací prvek, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a <xref:System.Windows.Forms.DataGridViewComboBoxCell> typy povolit, můžete přidat libovolné objekty do jejich rozevírací seznamy. Pomocí této funkce může představovat komplexní stavů v rozevíracím seznamu bez nutnosti ukládat odpovídající objekty v samostatné kolekce.  
  
 Na rozdíl od <xref:System.Windows.Forms.ComboBox> ovládací prvek, <xref:System.Windows.Forms.DataGridView> typy nemají <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> vlastnost pro načítání aktuálně vybraného objektu. Místo toho je nutné nastavit <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> vlastnost na název vlastnosti v objektu vaší firmy. Když uživatel provede výběr, uvedené vlastnost objektu obchodní nastaví buňky <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost.  
  
 K načtení objektu obchodní prostřednictvím hodnotu buňky `ValueMember` vlastnost musí označovat vlastnost, která vrátí odkaz na objekt obchodní sám sebe. Proto pokud typ objektu obchodní není ve vaší kontrole, musíte přidat taková vlastnost rozšířením typu prostřednictvím dědičnosti.  
  
 Následující postupy ukazují, jak k naplnění rozevíracího seznamu s obchodní objekty a načtení objektů prostřednictvím buňky <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>Chcete-li přidat objekty obchodní do rozevíracího seznamu  
  
1.  Vytvořte novou <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a naplnit její <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> kolekce. Alternativně můžete nastavit sloupec <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> vlastnost ke kolekci obchodních objektů. V takovém případě však nelze přidáte "nepřiřazené" do rozevíracího seznamu bez vytvoření odpovídající obchodní objekt v kolekci.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  Nastavte <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> a <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> vlastnosti. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> Určuje vlastnost objektu obchodní zobrazíte v rozevíracím seznamu. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> Určuje vlastnost, která vrátí odkaz na objekt firmy.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  Ujistěte se, že vaše obchodní typ objektu obsahuje vlastnosti, která vrátí odkaz na aktuální instanci. Tato vlastnost musí mít název s hodnotu přiřazenou <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> v předchozím kroku.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Načíst objekt aktuálně vybraného firmy  
  
-   Získat buňky <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost a přetypovat na typ objektu firmy.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Příklad  
 Úplný příklad ukazuje použití obchodních objektů v rozevíracím seznamu. V příkladu <xref:System.Windows.Forms.DataGridView> ovládací prvek vázán ke kolekci `Task` objekty. Každý `Task` objekt má `AssignedTo` vlastnost, která určuje, `Employee` objektu, které jsou přiřazeny k této úlohy. `Assigned To` Sloupec zobrazuje `Name` přiřazena hodnota vlastnosti pro každý zaměstnanec, nebo "nepřiřazené", pokud `Task.AssignedTo` hodnota vlastnosti je `null`.  
  
 Chcete-li zobrazit chování tohoto příkladu, proveďte následující kroky:  
  
1.  Změna přiřazení v `Assigned To` sloupec výběrem různé hodnoty z rozevíracího seznamu nebo kombinace kláves CTRL + 0 v buňce pole se seznamem.  
  
2.  Klikněte na tlačítko `Generate Report` zobrazit aktuální přiřazení. Tento příklad ukazuje, který změnu `Assigned To` sloupec automaticky aktualizuje `tasks` kolekce.  
  
3.  Klikněte na tlačítko `Request Status` tlačítko volání `RequestStatus` metoda aktuálního `Employee` objektu na příslušném řádku. Tento příklad ukazuje úspěšně načetl vybraný objekt.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém a System.Windows.Forms sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ComboBox>  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
