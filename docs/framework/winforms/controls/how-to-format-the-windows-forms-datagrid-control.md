---
title: Formátování ovládacího prvku DataGrid
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
ms.openlocfilehash: 30342a89f3176255fa7217ccbbbd91c166ff7f35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732956"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Postupy: Formátování ovládacího prvku Windows Forms DataGrid
> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Použití různých barev u různých částí <xref:System.Windows.Forms.DataGrid>ho ovládacího prvku může pomáhat usnadnit čtení a interpretaci informací. Barvu lze použít u řádků a sloupců. Řádky a sloupce můžete také skrýt nebo zobrazit podle vašeho uvážení.  
  
 Existují tři základní aspekty formátování ovládacího prvku <xref:System.Windows.Forms.DataGrid>. Můžete nastavit vlastnosti pro vytvoření výchozího stylu, ve kterém jsou zobrazena data. Z této základny pak můžete přizpůsobit způsob, jakým jsou v době běhu zobrazeny určité tabulky. Nakonec můžete upravit, které sloupce se zobrazí v datové mřížce, a také barvy a jiné zobrazené formátování.  
  
 Jako počáteční krok při formátování datové mřížky můžete nastavit vlastnosti samotného <xref:System.Windows.Forms.DataGrid>. Volby barev a formátů tvoří základ, ze kterého pak můžete provádět změny v závislosti na zobrazených tabulkách dat a sloupcích.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Vytvoření výchozího stylu pro ovládací prvek DataGrid  
  
1. Podle potřeby nastavte následující vlastnosti:  
  
    |Vlastnost|Popis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|Vlastnost <xref:System.Windows.Forms.DataGrid.BackColor%2A> definuje barvu sudého číslování řádků mřížky. Když nastavíte vlastnost <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> na jinou barvu, každý další řádek je nastaven na tuto novou barvu (řádky 1, 3, 5 atd.).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Barva pozadí sudého číslování řádků mřížky (řádky 0, 2, 4, 6 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Vzhledem k tomu, že vlastnosti <xref:System.Windows.Forms.DataGrid.BackColor%2A> a <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> určují barvu řádků v mřížce, vlastnost <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> Určuje barvu oblasti nonrow, která je viditelná pouze v případě, že se mřížka posouvá do dolní části, nebo pokud je v mřížce obsažen pouze pár řádků.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl ohraničení mřížky, jedna z hodnot <xref:System.Windows.Forms.BorderStyle> výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Barva pozadí nadpisu okna mřížky, která se zobrazuje hned nad mřížkou|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Písmo popisku v horní části mřížky|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Barva pozadí nadpisu okna mřížky|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Písmo použité k zobrazení textu v mřížce|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Barva písma zobrazeného v datech v řádcích datové mřížky|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Barva čar mřížky pro datovou mřížku.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl čar, který odděluje buňky mřížky, jednu z hodnot výčtu <xref:System.Windows.Forms.DataGridLineStyle>.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Barva pozadí záhlaví řádků a sloupců|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Písmo použité pro záhlaví sloupců|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Barva popředí záhlaví sloupců v mřížce, včetně textu záhlaví sloupce a glyfů plus/mínus (pro rozbalení řádků při zobrazení více souvisejících tabulek).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Barva textu všech odkazů v mřížce dat, včetně odkazů na podřízené tabulky, název vztahu atd.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|V podřízené tabulce se jedná o barvu pozadí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|V podřízené tabulce je to barva popředí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Určuje, zda jsou názvy tabulek a sloupců zobrazeny v nadřazeném řádku prostřednictvím výčtu <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Výchozí šířka (v pixelech) sloupců v mřížce. Tuto vlastnost nastavte před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastností (buď samostatně, nebo prostřednictvím metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>), nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nemůže být nastavena na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Výška řádku (v pixelech) řádků v mřížce Tuto vlastnost nastavte před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastností (buď samostatně, nebo prostřednictvím metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>), nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nemůže být nastavena na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Šířka záhlaví řádků mřížky|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Když je vybrán řádek nebo buňka, jedná se o barvu pozadí.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Když je vybrán řádek nebo buňka, jedná se o barvu popředí.|  
  
    > [!NOTE]
    > Mějte na paměti, že při přizpůsobování barev ovládacích prvků je možné nastavit, aby byl ovládací prvek nepřístupný, protože je zvolena špatná barva (například červená a zelená). K tomuto problému se vyhnete použitím barev dostupných na paletě **systémových barev** .  
  
     Následující postupy předpokládají, že ve formuláři je ovládací prvek <xref:System.Windows.Forms.DataGrid> svázaný s datovou tabulkou. Další informace naleznete v tématu [svázání model Windows Forms ovládacího prvku DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Nastavení stylu tabulky a sloupce tabulky dat prostřednictvím kódu programu  
  
1. Vytvořte nový styl tabulky a nastavte jeho vlastnosti.  
  
2. Vytvořte styl sloupce a nastavte jeho vlastnosti.  
  
3. Přidejte styl sloupce do kolekce stylů sloupců stylu tabulky.  
  
4. Přidejte styl tabulky do kolekce stylů tabulek v datové mřížce.  
  
5. V následujícím příkladu vytvořte instanci nového <xref:System.Windows.Forms.DataGridTableStyle> a nastavte její vlastnost <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>.  
  
6. Vytvořte novou instanci **GridColumnStyle** a nastavte její **mapování** (a jiné vlastnosti rozložení a zobrazení).  
  
7. Opakujte kroky 2 až 6 pro každý styl sloupce, který chcete vytvořit.  
  
     Následující příklad ukazuje, jak je vytvořen <xref:System.Windows.Forms.DataGridTextBoxColumn>, protože název se zobrazí ve sloupci. Navíc můžete přidat styl sloupce do <xref:System.Windows.Forms.GridColumnStylesCollection> stylu tabulky a přidat styl tabulky do <xref:System.Windows.Forms.GridTableStylesCollection> datové mřížky.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
