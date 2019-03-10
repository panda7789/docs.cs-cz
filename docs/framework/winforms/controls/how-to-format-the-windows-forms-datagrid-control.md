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
ms.openlocfilehash: 696fdc09d285e0a04148e82b0cece6108b7d5a45
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705906"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Postupy: Formátování ovládacího prvku Windows Forms DataGrid
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Rozlišení barvami různých částí <xref:System.Windows.Forms.DataGrid> ovládací prvek může pomoct usnadňují informace v něm přečíst a interpretovat. Barva lze použít k řádků a sloupců. Řádky a sloupce můžete také skrytí nebo zobrazení na vašem uvážení.  
  
 Existují tři základní aspekty formátování <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Můžete nastavit vlastnosti, které chcete vytvořit výchozí styl, ve kterém se zobrazí data. Z této základní třídě potom můžete přizpůsobit způsob, jakým některé tabulky se zobrazí v době běhu. Nakonec můžete upravit sloupce, které se zobrazí v mřížce dat, jakož i barvy a další formátování, které se zobrazí.  
  
 Jako první krok v datové mřížce formátování, můžete nastavit vlastnosti <xref:System.Windows.Forms.DataGrid> samotný. Tyto možnosti barvu a formát tvoří základ, ze kterého můžete pak provádět změny v závislosti na datových tabulek a sloupců zobrazených.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Stanovit výchozí styl ovládacího prvku DataGrid  
  
1.  Podle potřeby nastavte následující vlastnosti:  
  
    |Vlastnost|Popis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> Vlastnost určuje barvu sudých řádků mřížky. Při nastavení <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> na jinou barvu, každý řádek je nastavena na tuto novou barvu (řádky 1, 3, 5 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Barva pozadí sudých řádků mřížky (řádky, 0, 2, 4, 6 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Vzhledem k tomu <xref:System.Windows.Forms.DataGrid.BackColor%2A> a <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> vlastnosti určuje barvu řádků v mřížce <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> vlastnost určuje barvu nonrow oblast, která je viditelná pouze když přesunut do dolní části oblasti mřížky, nebo jestli se jenom pár řádků jsou obsaženy v Mřížka.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl ohraničení mřížky, jeden z <xref:System.Windows.Forms.BorderStyle> hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Barva pozadí titulek okna mřížky, které se zobrazí okamžitě nad mřížkou.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Písmo záhlaví v horní části stránky mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Barva pozadí titulek okna mřížky.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Písmo použité k zobrazení textu v mřížce.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Barva písma, zobrazí data v řádcích datové mřížce.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Barva čar mřížky dat mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl čar oddělujících buňky ovládacího prvku mřížky, jeden z <xref:System.Windows.Forms.DataGridLineStyle> hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Barva pozadí záhlaví řádků a sloupců.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Písmo použité pro záhlaví sloupců.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Barva popředí záhlaví sloupců mřížky, včetně textu záhlaví sloupce a glyfy plus a minus (Chcete-li rozbalit řádků při zobrazení více souvisejícími tabulkami).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Barva textu na odkazy v datové mřížce, včetně odkazů na podřízené tabulky, název relace a tak dále.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|V podřízené tabulce je to barvu pozadí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|V podřízené tabulce je to barvu popředí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Určuje, zda názvy tabulek a sloupců se zobrazí v řádku nadřazené prostřednictvím <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Výchozí šířku (v pixelech) sloupce v mřížce. Tuto vlastnost nastavte před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti (buď samostatně, nebo prostřednictvím <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), nebo vlastnost nebude mít žádný efekt.<br /><br /> Vlastnost nelze nastavit na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Výška řádku řádků v mřížce (v pixelech). Tuto vlastnost nastavte před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti (buď samostatně, nebo prostřednictvím <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), nebo vlastnost nebude mít žádný efekt.<br /><br /> Vlastnost nelze nastavit na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Šířka záhlaví řádků mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Při výběru řádku nebo buňky, to je barvu pozadí.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Při výběru řádku nebo buňky, to je barvu popředí.|  
  
    > [!NOTE]
    >  Mějte na paměti, když upravujete barvy ovládacích prvků, aby bylo možné nastavit ovládací prvek není přístupný z špatná barva výběru (například red a zelená). Použití barev, které jsou k dispozici na **systémové barvy** palety chcete vyhnout tomuto problému.  
  
     Následující postupy předpokládají, že váš formulář má <xref:System.Windows.Forms.DataGrid> ovládací prvek vázán na data tabulky. Další informace najdete v tématu [vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Nastavit styl tabulky a sloupce z tabulky dat prostřednictvím kódu programu  
  
1.  Vytvořit nový styl tabulky a nastavte jeho vlastnosti.  
  
2.  Vytvořit styl sloupce a nastavte jeho vlastnosti.  
  
3.  Styl sloupce přidáte do kolekce stylů sloupců styl tabulky.  
  
4.  Styl tabulky přidáte do kolekce stylů tabulek datové mřížky.  
  
5.  V následujícím příkladu vytvoření instance nového <xref:System.Windows.Forms.DataGridTableStyle> a nastavte jeho <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost.  
  
6.  Vytvořit novou instanci třídy **GridColumnStyle** a nastavte jeho **MappingName** (a některé další vlastnosti rozložení a zobrazení).  
  
7.  Opakujte kroky 2 až 6 pro každý sloupec styl, který chcete vytvořit.  
  
     Následující příklad ukazuje, jak <xref:System.Windows.Forms.DataGridTextBoxColumn> je vytvořen, protože je název, který se zobrazí ve sloupci. Kromě toho přidat sloupec styl, který má <xref:System.Windows.Forms.GridColumnStylesCollection> stylu tabulky a přidat styl tabulky, který <xref:System.Windows.Forms.GridTableStylesCollection> datové mřížky.  
  
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
- [Postupy: Odstranit nebo skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
