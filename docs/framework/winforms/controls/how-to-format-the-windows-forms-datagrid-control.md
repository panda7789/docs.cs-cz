---
title: 'Postupy: Formátování ovládacího prvku Windows Forms DataGrid'
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
ms.openlocfilehash: 99acef0a7b29228ddf0406352ff5a88b77294b00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966674"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Postupy: Formátování ovládacího prvku Windows Forms DataGrid
> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView> Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Použití různých barev u různých částí <xref:System.Windows.Forms.DataGrid> ovládacího prvku může usnadnit čtení a interpretaci informací. Barvu lze použít u řádků a sloupců. Řádky a sloupce můžete také skrýt nebo zobrazit podle vašeho uvážení.  
  
 Existují tři základní aspekty formátování <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Můžete nastavit vlastnosti pro vytvoření výchozího stylu, ve kterém jsou zobrazena data. Z této základny pak můžete přizpůsobit způsob, jakým jsou v době běhu zobrazeny určité tabulky. Nakonec můžete upravit, které sloupce se zobrazí v datové mřížce, a také barvy a jiné zobrazené formátování.  
  
 Jako počáteční krok při formátování datové mřížky můžete nastavit vlastnosti <xref:System.Windows.Forms.DataGrid> sebe sama. Volby barev a formátů tvoří základ, ze kterého pak můžete provádět změny v závislosti na zobrazených tabulkách dat a sloupcích.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Vytvoření výchozího stylu pro ovládací prvek DataGrid  
  
1. Podle potřeby nastavte následující vlastnosti:  
  
    |Vlastnost|Popis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> Vlastnost definuje barvu sudého číslování řádků mřížky. Když nastavíte <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> vlastnost na jinou barvu, každý další řádek je nastaven na tuto novou barvu (řádky 1, 3, 5 atd.).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Barva pozadí sudého číslování řádků mřížky (řádky 0, 2, 4, 6 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Vzhledem k tomu <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> , že vlastnosti <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>aurčují barvu řádků v mřížce, vlastnost určuje barvu oblasti nonrow, která je viditelná pouze v případě, že je mřížka posunuta dolů nebo pokud je v ní obsažen pouze pár řádků. <xref:System.Windows.Forms.DataGrid.BackColor%2A> mřížka.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl ohraničení mřížky, jedna z <xref:System.Windows.Forms.BorderStyle> hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Barva pozadí nadpisu okna mřížky, která se zobrazuje hned nad mřížkou|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Písmo popisku v horní části mřížky|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Barva pozadí nadpisu okna mřížky|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Písmo použité k zobrazení textu v mřížce|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Barva písma zobrazeného v datech v řádcích datové mřížky|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Barva čar mřížky pro datovou mřížku.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl čar, který odděluje buňky v mřížce, jednu z <xref:System.Windows.Forms.DataGridLineStyle> hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Barva pozadí záhlaví řádků a sloupců|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Písmo použité pro záhlaví sloupců|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Barva popředí záhlaví sloupců v mřížce, včetně textu záhlaví sloupce a glyfů plus/mínus (pro rozbalení řádků při zobrazení více souvisejících tabulek).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Barva textu všech odkazů v mřížce dat, včetně odkazů na podřízené tabulky, název vztahu atd.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|V podřízené tabulce se jedná o barvu pozadí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|V podřízené tabulce je to barva popředí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Určuje, zda jsou názvy tabulek a sloupců zobrazeny v nadřazeném řádku prostřednictvím <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Výchozí šířka (v pixelech) sloupců v mřížce. Nastavte tuto vlastnost před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastností a <xref:System.Windows.Forms.DataGrid.DataMember%2A> (buď <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> samostatně, nebo prostřednictvím metody), nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nemůže být nastavena na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Výška řádku (v pixelech) řádků v mřížce Nastavte tuto vlastnost před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastností a <xref:System.Windows.Forms.DataGrid.DataMember%2A> (buď <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> samostatně, nebo prostřednictvím metody), nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nemůže být nastavena na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Šířka záhlaví řádků mřížky|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Když je vybrán řádek nebo buňka, jedná se o barvu pozadí.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Když je vybrán řádek nebo buňka, jedná se o barvu popředí.|  
  
    > [!NOTE]
    > Mějte na paměti, že při přizpůsobování barev ovládacích prvků je možné nastavit, aby byl ovládací prvek nepřístupný, protože je zvolena špatná barva (například červená a zelená). K tomuto problému se vyhnete použitím barev dostupných na paletě **systémových barev** .  
  
     Následující postupy předpokládají, že váš formulář má <xref:System.Windows.Forms.DataGrid> ovládací prvek vázaný na datovou tabulku. Další informace naleznete v tématu [svázání model Windows Forms ovládacího prvku DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Nastavení stylu tabulky a sloupce tabulky dat prostřednictvím kódu programu  
  
1. Vytvořte nový styl tabulky a nastavte jeho vlastnosti.  
  
2. Vytvořte styl sloupce a nastavte jeho vlastnosti.  
  
3. Přidejte styl sloupce do kolekce stylů sloupců stylu tabulky.  
  
4. Přidejte styl tabulky do kolekce stylů tabulek v datové mřížce.  
  
5. V následujícím příkladu vytvořte instanci nového <xref:System.Windows.Forms.DataGridTableStyle> a nastavte její <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost.  
  
6. Vytvořte novou instanci **GridColumnStyle** a nastavte její **mapování** (a jiné vlastnosti rozložení a zobrazení).  
  
7. Opakujte kroky 2 až 6 pro každý styl sloupce, který chcete vytvořit.  
  
     Následující příklad ukazuje, jak <xref:System.Windows.Forms.DataGridTextBoxColumn> je vytvořena, protože název je zobrazen ve sloupci. Kromě toho můžete přidat styl sloupce do <xref:System.Windows.Forms.GridColumnStylesCollection> stylu tabulky a přidat styl tabulky <xref:System.Windows.Forms.GridTableStylesCollection> k datové mřížce.  
  
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
- [Postupy: Odstranění nebo skrytí sloupců v model Windows Forms ovládacím prvku DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
