---
title: Odstranění nebo skrytí sloupců v ovládacím prvku DataGrid
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
ms.openlocfilehash: c730be934e9b978bdaf09bc7e668b4318077fba5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743293"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="9b05c-102">Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="9b05c-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="9b05c-103">Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="9b05c-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="9b05c-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9b05c-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="9b05c-105">Můžete programově odstranit nebo skrýt sloupce v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGrid> pomocí vlastností a metod objektů <xref:System.Windows.Forms.GridColumnStylesCollection> a <xref:System.Windows.Forms.DataGridColumnStyle> (které jsou členy třídy <xref:System.Windows.Forms.DataGridTableStyle>).</span><span class="sxs-lookup"><span data-stu-id="9b05c-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="9b05c-106">Odstraněné nebo skryté sloupce stále existují ve zdroji dat, ke kterému je mřížka vázána, a ke kterým lze nadále přistupovat programově.</span><span class="sxs-lookup"><span data-stu-id="9b05c-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="9b05c-107">Již nejsou viditelné v prvku DataGrid.</span><span class="sxs-lookup"><span data-stu-id="9b05c-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b05c-108">Pokud vaše aplikace nepřistupuje k určitým sloupcům dat a nechcete, aby se zobrazila v prvku DataGrid, je pravděpodobné, že je nebudete muset zahrnout do zdroje dat na prvním místě.</span><span class="sxs-lookup"><span data-stu-id="9b05c-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="9b05c-109">Postup při odstranění sloupce z tabulky DataGrid programově</span><span class="sxs-lookup"><span data-stu-id="9b05c-109">To delete a column from the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="9b05c-110">V oblasti deklarace ve formuláři deklarujte novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle>.</span><span class="sxs-lookup"><span data-stu-id="9b05c-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="9b05c-111">Vlastnost <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> nastavte na tabulku ve zdroji dat, pro kterou chcete styl použít.</span><span class="sxs-lookup"><span data-stu-id="9b05c-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="9b05c-112">V následujícím příkladu je použita vlastnost <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, která předpokládá, že je již nastavena.</span><span class="sxs-lookup"><span data-stu-id="9b05c-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="9b05c-113">Přidejte nový objekt <xref:System.Windows.Forms.DataGridTableStyle> do kolekce stylů tabulky DataGrid.</span><span class="sxs-lookup"><span data-stu-id="9b05c-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="9b05c-114">Zavolejte metodu <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> kolekce <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> <xref:System.Windows.Forms.DataGrid>a určete index sloupce sloupce, který se má odstranit.</span><span class="sxs-lookup"><span data-stu-id="9b05c-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="9b05c-115">Programové skrytí sloupce v ovládacím prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="9b05c-115">To hide a column in the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="9b05c-116">V oblasti deklarace ve formuláři deklarujte novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle>.</span><span class="sxs-lookup"><span data-stu-id="9b05c-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="9b05c-117">Nastavte vlastnost <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> <xref:System.Windows.Forms.DataGridTableStyle> na tabulku ve zdroji dat, pro kterou chcete styl použít.</span><span class="sxs-lookup"><span data-stu-id="9b05c-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="9b05c-118">Následující příklad kódu používá vlastnost <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, která předpokládá, že je již nastavena.</span><span class="sxs-lookup"><span data-stu-id="9b05c-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="9b05c-119">Přidejte nový objekt <xref:System.Windows.Forms.DataGridTableStyle> do kolekce stylů tabulky DataGrid.</span><span class="sxs-lookup"><span data-stu-id="9b05c-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="9b05c-120">Skryjte sloupec nastavením jeho vlastnosti `Width` na hodnotu 0 a určete index sloupce sloupce, který se má skrýt.</span><span class="sxs-lookup"><span data-stu-id="9b05c-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9b05c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b05c-121">See also</span></span>

- [<span data-ttu-id="9b05c-122">Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="9b05c-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [<span data-ttu-id="9b05c-123">Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="9b05c-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
