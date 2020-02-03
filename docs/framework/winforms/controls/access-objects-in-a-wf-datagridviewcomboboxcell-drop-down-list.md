---
title: Přístup k objektům v rozevíracím seznamu DataGridViewComboBoxCell
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 7e76ab1ac9089778e4371f4ee65b06d5ebc570bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746312"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Postupy: Přístup k objektům v rozevíracím seznamu Windows Forms DataGridViewComboBoxCell
Stejně jako ovládací prvek <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a <xref:System.Windows.Forms.DataGridViewComboBoxCell> typy umožňují přidat libovolné objekty do jejich rozevíracích seznamů. Pomocí této funkce můžete reprezentovat komplexní stavy v rozevíracím seznamu, aniž byste museli ukládat odpovídající objekty v samostatné kolekci.  
  
 Na rozdíl od ovládacího prvku <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.DataGridView> typy nemají vlastnost <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> pro načtení aktuálně vybraného objektu. Místo toho musíte nastavit vlastnost <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> na název vlastnosti v obchodním objektu. Když uživatel provede výběr, určí vlastnost byznys objektu vlastnost <xref:System.Windows.Forms.DataGridViewCell.Value%2A> buňky.  
  
 Chcete-li načíst obchodní objekt prostřednictvím hodnoty buňky, musí vlastnost `ValueMember` indikovat vlastnost, která vrací odkaz na samotný obchodní objekt. Proto pokud typ obchodního objektu není pod vaším ovládacím prvkem, je nutné přidat takovou vlastnost rozšířením typu prostřednictvím dědičnosti.  
  
 Následující postupy ukazují, jak naplnit rozevírací seznam pomocí obchodních objektů a načíst objekty pomocí vlastnosti <xref:System.Windows.Forms.DataGridViewCell.Value%2A> buňky.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>Přidání obchodních objektů do rozevíracího seznamu  
  
1. Vytvořte nový <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a naplňte jeho kolekci <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>. Případně můžete nastavit vlastnost <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> sloupce na kolekci obchodních objektů. V takovém případě však nemůžete do rozevíracího seznamu přidat "Nepřiřazeno" bez vytvoření odpovídajícího podnikového objektu v kolekci.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> a <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> určuje vlastnost obchodního objektu, která se má zobrazit v rozevíracím seznamu. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> určuje vlastnost, která vrací odkaz na obchodní objekt.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. Ujistěte se, že typ obchodního objektu obsahuje vlastnost, která vrací odkaz na aktuální instanci. Tato vlastnost musí být pojmenována s hodnotou přiřazenou <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> v předchozím kroku.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Načtení aktuálně vybraného obchodního objektu  
  
- Získat vlastnost <xref:System.Windows.Forms.DataGridViewCell.Value%2A> buňky a přetypovat ji na typ obchodního objektu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Příklad  
 Kompletní příklad ukazuje použití obchodních objektů v rozevíracím seznamu. V příkladu je ovládací prvek <xref:System.Windows.Forms.DataGridView> vázán na kolekci objektů `Task`. Každý objekt `Task` má vlastnost `AssignedTo`, která indikuje objekt `Employee` aktuálně přiřazený k této úloze. `Assigned To` sloupec zobrazuje hodnotu vlastnosti `Name` pro každého přiřazeného zaměstnance nebo "Nepřiřazeno", pokud je hodnota vlastnosti `Task.AssignedTo` `null`a.  
  
 Chcete-li zobrazit chování tohoto příkladu, proveďte následující kroky:  
  
1. Změňte přiřazení ve sloupci `Assigned To` výběrem různých hodnot z rozevíracích seznamů nebo stisknutím kombinace kláves CTRL + 0 v buňce pole se seznamem.  
  
2. Kliknutím na `Generate Report` zobrazíte aktuální přiřazení. To ukazuje, že změna ve sloupci `Assigned To` automaticky aktualizuje kolekci `tasks`.  
  
3. Klikněte na `Request Status` tlačítko a zavolejte metodu `RequestStatus` aktuálního objektu `Employee` pro daný řádek. To ukazuje, že vybraný objekt byl úspěšně načten.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také

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
