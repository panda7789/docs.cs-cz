---
title: 'Postupy: Odstranit nebo skrytí sloupců v ovládacím prvku Windows Forms DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: 635fbc112a241c4c8b17d2b49c22042c6bd59a21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653941"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="70d3b-102">Postupy: Odstranit nebo skrytí sloupců v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="70d3b-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="70d3b-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="70d3b-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="70d3b-104">Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="70d3b-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="70d3b-105">Programově můžete odstranit nebo skrytí sloupců v modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku pomocí vlastnosti a metody <xref:System.Windows.Forms.GridColumnStylesCollection> a <xref:System.Windows.Forms.DataGridColumnStyle> objekty (které jsou členy objektu <xref:System.Windows.Forms.DataGridTableStyle> třídy).</span><span class="sxs-lookup"><span data-stu-id="70d3b-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="70d3b-106">Odstraněné nebo skryté sloupce stále existují ve zdroji dat je vázán na mřížky a i nadále přístupný prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="70d3b-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="70d3b-107">Stačí už nejsou viditelné v mřížce datagrid.</span><span class="sxs-lookup"><span data-stu-id="70d3b-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70d3b-108">Pokud vaše aplikace není přístup k určité sloupce dat, a nechcete zobrazovat v mřížce datagrid, pak je pravděpodobně není nutné zahrnout je do zdroje dat na prvním místě.</span><span class="sxs-lookup"><span data-stu-id="70d3b-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="70d3b-109">Chcete-li odstranit sloupce z mřížky DataGrid prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="70d3b-109">To delete a column from the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="70d3b-110">V oblasti formuláře deklarace deklarovat novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle> třídy.</span><span class="sxs-lookup"><span data-stu-id="70d3b-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="70d3b-111">Nastavte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> vlastnost do tabulky ve zdroji dat, který chcete použít styl.</span><span class="sxs-lookup"><span data-stu-id="70d3b-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="70d3b-112">V následujícím příkladu <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> vlastnost, která předpokládá, že je již nastaven.</span><span class="sxs-lookup"><span data-stu-id="70d3b-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="70d3b-113">Přidejte nové <xref:System.Windows.Forms.DataGridTableStyle> objekt kolekce stylů tabulek mřížce datagrid.</span><span class="sxs-lookup"><span data-stu-id="70d3b-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="70d3b-114">Volání <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> metodu <xref:System.Windows.Forms.DataGrid>společnosti <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolekci index sloupce sloupce, který se odstranit zadání.</span><span class="sxs-lookup"><span data-stu-id="70d3b-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="70d3b-115">Chcete-li skrýt sloupec v mřížce DataGrid prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="70d3b-115">To hide a column in the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="70d3b-116">V oblasti formuláře deklarace deklarovat novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle> třídy.</span><span class="sxs-lookup"><span data-stu-id="70d3b-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="70d3b-117">Nastavte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost <xref:System.Windows.Forms.DataGridTableStyle> do tabulky ve zdroji dat, který chcete použít styl.</span><span class="sxs-lookup"><span data-stu-id="70d3b-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="70d3b-118">Následující příklad kódu používá <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> vlastnost, která předpokládá, že je již nastaven.</span><span class="sxs-lookup"><span data-stu-id="70d3b-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="70d3b-119">Přidejte nové <xref:System.Windows.Forms.DataGridTableStyle> objekt kolekce stylů tabulek mřížce datagrid.</span><span class="sxs-lookup"><span data-stu-id="70d3b-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="70d3b-120">Skrýt sloupec tak, že nastavíte její `Width` vlastnost na hodnotu 0, určení sloupcový index sloupce, který se skrýt.</span><span class="sxs-lookup"><span data-stu-id="70d3b-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="70d3b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70d3b-121">See also</span></span>
- [<span data-ttu-id="70d3b-122">Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="70d3b-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)
- [<span data-ttu-id="70d3b-123">Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="70d3b-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
