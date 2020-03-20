---
title: Formát ovládacího prvku datové mřížky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
ms.openlocfilehash: 180f837c7d60f49af880faefc05da262be061d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182138"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Postupy: Formátování ovládacího prvku Windows Forms DataGrid
> [!NOTE]
> Ovládací <xref:System.Windows.Forms.DataGridView> prvek nahradí a přidá <xref:System.Windows.Forms.DataGrid> funkce ovládacího prvku; <xref:System.Windows.Forms.DataGrid> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete. Další informace naleznete v [tématu Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Použití různých barev na <xref:System.Windows.Forms.DataGrid> různé části ovládacího prvku může usnadnit čtení a interpretaci informací v ovládacím prvku. Barvu lze aplikovat na řádky a sloupce. Řádky a sloupce mohou být také skryté nebo zobrazeny podle vašeho uvážení.  
  
 Existují tři základní aspekty formátování <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Můžete nastavit vlastnosti pro vytvoření výchozího stylu, ve kterém jsou data zobrazena. Z této základny pak můžete přizpůsobit způsob, jakým jsou některé tabulky zobrazeny za běhu. Nakonec můžete upravit, které sloupce jsou zobrazeny v datové mřížce, stejně jako barvy a další formátování, které se zobrazí.  
  
 Jako první krok při formátování datové mřížky můžete nastavit <xref:System.Windows.Forms.DataGrid> vlastnosti samotného. Tyto volby barev a formátů tvoří základ, ze kterého pak můžete provádět změny v závislosti na zobrazených datových tabulkách a sloupcích.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Vytvoření výchozího stylu ovládacího prvku DataGrid  
  
1. Podle potřeby nastavte následující vlastnosti:  
  
    |Vlastnost|Popis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|Vlastnost <xref:System.Windows.Forms.DataGrid.BackColor%2A> definuje barvu sudých řádků mřížky. Když nastavíte <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> vlastnost na jinou barvu, každý druhý řádek je nastaven na tuto novou barvu (řádky 1, 3, 5 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Barva pozadí sudých řádků mřížky (řádky 0, 2, 4, 6 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Vzhledem <xref:System.Windows.Forms.DataGrid.BackColor%2A> k <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> tomu, vlastnosti a určuje barvu <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> řádků v mřížce, vlastnost určuje barvu oblasti nonrow, která je viditelná pouze při posunu mřížky dolů, nebo pokud jsou obsaženy pouze několik řádků v mřížce.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl ohraničení mřížky, jedna <xref:System.Windows.Forms.BorderStyle> z hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Barva pozadí titulku okna mřížky, která se zobrazí bezprostředně nad mřížkou.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Písmo titulku v horní části mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Barva pozadí titulku okna mřížky.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Písmo použité k zobrazení textu v mřížce.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Barva písma zobrazená daty v řádcích mřížky dat.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Barva čar mřížky datové mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl čar oddělujících buňky mřížky, <xref:System.Windows.Forms.DataGridLineStyle> jednu z hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Barva pozadí záhlaví řádků a sloupců.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Písmo použité pro záhlaví sloupců.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Barva popředí záhlaví sloupců mřížky, včetně textu záhlaví sloupce a glyfů plus/mínus (chcete-li rozbalit řádky při zobrazení více souvisejících tabulek).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Barva textu všech odkazů v datové mřížce, včetně odkazů na podřízené tabulky, název vztahu a tak dále.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|V podřízené tabulce se jedná o barvu pozadí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|V podřízené tabulce se jedná o barvu popředí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Určuje, zda jsou názvy tabulek a sloupců zobrazeny <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> v nadřazeném řádku pomocí výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Výchozí šířka (v obrazových bodech) sloupců v mřížce. Nastavte tuto vlastnost před <xref:System.Windows.Forms.DataGrid.DataSource%2A> <xref:System.Windows.Forms.DataGrid.DataMember%2A> resetováním vlastností a <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (samostatně nebo metodou) nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nelze nastavit na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Výška řádku (v obrazových bodech) řádků v mřížce. Nastavte tuto vlastnost před <xref:System.Windows.Forms.DataGrid.DataSource%2A> <xref:System.Windows.Forms.DataGrid.DataMember%2A> resetováním vlastností a <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (samostatně nebo metodou) nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nelze nastavit na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Šířka záhlaví řádků mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Když je vybrán řádek nebo buňka, jedná se o barvu pozadí.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Když je vybrán řádek nebo buňka, jedná se o barvu popředí.|  
  
    > [!NOTE]
    > Mějte na paměti, při přizpůsobení barev ovládacích prvků, že je možné, aby ovládací prvek nepřístupný, z důvodu špatné volby barev (například červené a zelené). Použijte barvy dostupné na paletě Systémové barvy, abyste se tomuto problému **vyhnuli.**  
  
     Následující postupy předpokládají, že <xref:System.Windows.Forms.DataGrid> formulář má ovládací prvek vázaný na tabulku dat. Další informace naleznete [v tématu Vazba ovládacího prvku Windows Forms DataGrid na zdroj dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Programové nastavení stylu tabulky a sloupce tabulky dat  
  
1. Vytvořte nový styl tabulky a nastavte jeho vlastnosti.  
  
2. Vytvořte styl sloupce a nastavte jeho vlastnosti.  
  
3. Přidejte styl sloupce do kolekce stylů sloupců stylu tabulky.  
  
4. Přidejte styl tabulky do kolekce stylů tabulek v tabulce mřížky dat.  
  
5. V níže uvedeném příkladu vytvořte instanci nové <xref:System.Windows.Forms.DataGridTableStyle> a nastavte její <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost.  
  
6. Vytvořte novou instanci **GridColumnStyle** a nastavte jeho **MappingName** (a některé další vlastnosti rozložení a zobrazení).  
  
7. Opakujte kroky 2 až 6 pro každý styl sloupce, který chcete vytvořit.  
  
     Následující příklad ukazuje, <xref:System.Windows.Forms.DataGridTextBoxColumn> jak je vytvořen, protože název má být zobrazen ve sloupci. Kromě toho přidáte styl sloupce <xref:System.Windows.Forms.GridColumnStylesCollection> do stylu tabulky a přidáte styl tabulky <xref:System.Windows.Forms.GridTableStylesCollection> do mřížky dat.  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName
       ' to the name of a DataColumn in the DataTable.
       ' Set the HeaderText and Width properties.
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to
       ' the GridTableStylesCollection.
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName
       // to the name of a DataColumn in the DataTable.
       // Set the HeaderText and Width properties.
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to
       // the GridTableStylesCollection.
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName
          // to the name of a DataColumn in the DataTable.
          // Set the HeaderText and Width properties.
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to
          // the GridTableStylesCollection.
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
