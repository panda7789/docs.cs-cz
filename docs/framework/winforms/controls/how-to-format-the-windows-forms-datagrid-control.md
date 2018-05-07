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
ms.openlocfilehash: ffcb84059dfceb85cdb347c3ddf1b80ab96c2aac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Postupy: Formátování ovládacího prvku Windows Forms DataGrid
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Použití různých barev pro různé součásti <xref:System.Windows.Forms.DataGrid> řízení může pomoct snadněji informace v něm ke čtení a interpretovat. Barva je použít pro řádků a sloupců. Řádků a sloupců, můžete také být skrytý nebo vidět svého uvážení.  
  
 Existují tři základní aspekty formátování <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Můžete nastavit vlastnosti pro vytvoření výchozí styl, ve kterém se zobrazí data. Z tohoto základní následně můžete přizpůsobit způsob zobrazování určité tabulky v době běhu. Nakonec můžete upravit sloupce, které se zobrazují v datové mřížce, jakož i barvy a další formátování, které se zobrazí.  
  
 Jako počáteční krok při formátování dat mřížky, můžete nastavit vlastnosti <xref:System.Windows.Forms.DataGrid> sám sebe. Tyto možnosti barvy a formát tvoří základ, ze které potom můžete provést změny v závislosti na data tabulky a sloupce zobrazí.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Pro vytvoření výchozí styl ovládacího prvku DataGrid  
  
1.  Podle potřeby nastavte následující vlastnosti:  
  
    |Vlastnost|Popis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> Vlastnost definuje barvu sudých řádků mřížky. Když nastavíte <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> na jinou barvu, každý druhý řádek je nastavena na tuto novou barvu (řádků 1, 3, 5 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Barva pozadí sudých řádků mřížky (řádků 0, 2, 4, 6 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Zatímco <xref:System.Windows.Forms.DataGrid.BackColor%2A> a <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> vlastnosti určuje barvu řádků v mřížce <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> vlastnost určuje barvu nonrow oblast, která je viditelná jen při přesunut do dolní oblasti mřížky, nebo pokud jenom pár řádků, které jsou obsaženy v mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl ohraničení mřížky, jeden z <xref:System.Windows.Forms.BorderStyle> hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Barva pozadí mřížky okno popisek, který se zobrazí okamžitě nad mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Písmo popisku v horní části mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Barva pozadí záhlaví okna mřížky.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Písmo použité k zobrazení textu v mřížce.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Barva písma zobrazuje data v řádky mřížky data.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Barva čar mřížky dat mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl čar oddělujících buňky mřížky, jeden z <xref:System.Windows.Forms.DataGridLineStyle> hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Barva pozadí záhlaví řádků a sloupců.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Písmo použité pro záhlaví sloupců.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Barvu popředí záhlaví sloupců mřížky, včetně textu záhlaví sloupce a glyfy plus nebo minus (Chcete-li rozbalit řádků, pokud se zobrazí více související tabulky).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Barva textu všechny odkazy na data mřížky, včetně odkazů na podřízené tabulky, název relace a tak dále.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|V podřízené tabulce je to barvu pozadí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|V podřízené tabulce je to barvu popředí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Určuje, zda jsou názvy tabulek a sloupců zobrazovat v řádku nadřazené prostřednictvím <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Šířka výchozí sloupců v mřížce (v pixelech). Tuto vlastnost nastavit před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti (buď samostatně, nebo pomocí <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nelze nastavit na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Výška řádku řádků v mřížce (v pixelech). Tuto vlastnost nastavit před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti (buď samostatně, nebo pomocí <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nelze nastavit na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Šířka záhlaví řádků mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Pokud je vybraný řádek nebo buňky, jde barvu pozadí.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Pokud je vybraný řádek nebo buňky, jde barvu popředí.|  
  
    > [!NOTE]
    >  Mějte na paměti, když přizpůsobení barev ovládacích prvků, aby bylo možné zajistit ovládacího prvku nepřístupný z důvodu nízký barva výběru (například red a zelená). Použít k dispozici na barvy **barvy systému** palety chcete tomuto problému vyhnout.  
  
     Následujících postupech se předpokládá má formulář <xref:System.Windows.Forms.DataGrid> ovládací prvek vázán k tabulce data. Další informace najdete v tématu [Vazba ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Chcete-li nastavit styl tabulky a sloupce tabulky dat prostřednictvím kódu programu  
  
1.  Vytvořte nový styl tabulky a nastavte její vlastnosti.  
  
2.  Vytvořte styl sloupce a nastavte její vlastnosti.  
  
3.  Styl tabulky sloupec styly kolekce přidáte styl sloupce.  
  
4.  Styl tabulky přidáte do kolekce stylů mřížky dat tabulky.  
  
5.  V následujícím příkladu vytvoření instance nového <xref:System.Windows.Forms.DataGridTableStyle> a nastavit jeho <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost.  
  
6.  Vytvořit novou instanci třídy **GridColumnStyle** a nastavit jeho **MappingName** (a některé další vlastnosti rozložení a zobrazení).  
  
7.  Opakujte kroky 2 až 6 pro každý sloupec styl, kterou chcete vytvořit.  
  
     Následující příklad ukazuje, jak <xref:System.Windows.Forms.DataGridTextBoxColumn> je vytvořit, protože název je zobrazený ve sloupci. Kromě toho můžete přidat styl sloupec, který se <xref:System.Windows.Forms.GridColumnStylesCollection> stylu tabulky a přidejte styl tabulky na <xref:System.Windows.Forms.GridTableStylesCollection> dat mřížky.  
  
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
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
