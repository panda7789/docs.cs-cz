---
title: "Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65257ec5f9ca51a795abca119e5449d6219042bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="b7d56-102">Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="b7d56-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="b7d56-103"><xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="b7d56-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b7d56-104">Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b7d56-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="b7d56-105">Prostřednictvím kódu programu můžete odstranit nebo skrytí sloupců v modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku pomocí vlastnosti a metody <xref:System.Windows.Forms.GridColumnStylesCollection> a <xref:System.Windows.Forms.DataGridColumnStyle> objekty (které jsou členy <xref:System.Windows.Forms.DataGridTableStyle> třídy).</span><span class="sxs-lookup"><span data-stu-id="b7d56-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="b7d56-106">Odstraněné nebo skrytých sloupců stále existují ve zdroji dat je vázán k mřížce a stále je možné programově přistupovat.</span><span class="sxs-lookup"><span data-stu-id="b7d56-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="b7d56-107">Právě již nejsou viditelné v objektu datagrid.</span><span class="sxs-lookup"><span data-stu-id="b7d56-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7d56-108">Pokud vaše aplikace není přístup k určité sloupce dat, a nechcete zobrazovat v objektu datagrid, pak je pravděpodobně není potřeba zahrnout je do zdroje dat na prvním místě.</span><span class="sxs-lookup"><span data-stu-id="b7d56-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="b7d56-109">Chcete odstranit sloupec z objektu DataGrid prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="b7d56-109">To delete a column from the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="b7d56-110">V oblasti deklarace formuláře deklarovat novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle> třídy.</span><span class="sxs-lookup"><span data-stu-id="b7d56-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="b7d56-111">Nastavte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> do tabulky ve zdroji dat, který chcete použít styl pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b7d56-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="b7d56-112">Následující příklad používá <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> vlastnosti, která předpokládá, že je již nastaven.</span><span class="sxs-lookup"><span data-stu-id="b7d56-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="b7d56-113">Přidejte nové <xref:System.Windows.Forms.DataGridTableStyle> objekt, který má kolekce stylů tabulek v kolekci datagrid.</span><span class="sxs-lookup"><span data-stu-id="b7d56-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="b7d56-114">Volání <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> metodu <xref:System.Windows.Forms.DataGrid>na <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolekce, zadání index sloupce sloupce, který se odstranit.</span><span class="sxs-lookup"><span data-stu-id="b7d56-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="b7d56-115">Skrytí sloupců v objektu DataGrid prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="b7d56-115">To hide a column in the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="b7d56-116">V oblasti deklarace formuláře deklarovat novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle> třídy.</span><span class="sxs-lookup"><span data-stu-id="b7d56-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="b7d56-117">Nastavte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost <xref:System.Windows.Forms.DataGridTableStyle> do tabulky ve zdroji dat, který chcete použít styl pro.</span><span class="sxs-lookup"><span data-stu-id="b7d56-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="b7d56-118">Následující příklad kódu používá <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> vlastnosti, která předpokládá, že je již nastaven.</span><span class="sxs-lookup"><span data-stu-id="b7d56-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="b7d56-119">Přidejte nové <xref:System.Windows.Forms.DataGridTableStyle> objekt, který má kolekce stylů tabulek v kolekci datagrid.</span><span class="sxs-lookup"><span data-stu-id="b7d56-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="b7d56-120">Skrýt sloupce nastavením jeho `Width` vlastnost na hodnotu 0, zadání index sloupce sloupce, který se skrýt.</span><span class="sxs-lookup"><span data-stu-id="b7d56-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7d56-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7d56-121">See Also</span></span>  
 [<span data-ttu-id="b7d56-122">Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="b7d56-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 [<span data-ttu-id="b7d56-123">Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="b7d56-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
