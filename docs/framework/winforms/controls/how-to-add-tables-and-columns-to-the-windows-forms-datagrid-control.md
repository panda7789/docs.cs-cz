---
title: 'Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: fc8161ea29da92f5dcc2e76f956f3fecd6140acc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527716"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="293ce-102">Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="293ce-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="293ce-103"><xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="293ce-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="293ce-104">Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="293ce-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="293ce-105">Data můžete zobrazit v modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku tabulky a sloupce vytvořením **styl DataGridTableStyle** objekty a jejich přidání **GridTableStylesCollection** objekt, který je přistupovat prostřednictvím <xref:System.Windows.Forms.DataGrid> ovládacího prvku **TableStyles** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="293ce-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="293ce-106">Každý styl tabulky zobrazí obsah ať tabulky dat je zadán v **styl DataGridTableStyle** objektu **MappingName** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="293ce-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="293ce-107">Ve výchozím nastavení zobrazí styl tabulky se žádné sloupce styly definované všechny sloupce v této tabulce data.</span><span class="sxs-lookup"><span data-stu-id="293ce-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="293ce-108">Můžete omezit, které sloupce z tabulky se objeví přidáním **Styl DataGridColumnStyle** objekty ke **kolekce GridColumnStylesCollection** objekt, který je přístupný prostřednictvím  **GridColumnStyles** vlastnost jednotlivých **styl DataGridTableStyle** objektu.</span><span class="sxs-lookup"><span data-stu-id="293ce-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="293ce-109">Přidání tabulek a sloupců do ovládacího prvku DataGrid prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="293ce-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="293ce-110">Chcete-li zobrazit data v tabulce, je třeba nejprve svázat <xref:System.Windows.Forms.DataGrid> ovládacího prvku do datové sady.</span><span class="sxs-lookup"><span data-stu-id="293ce-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="293ce-111">Další informace najdete v tématu [postupy: vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="293ce-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="293ce-112">Při zadávání prostřednictvím kódu programu styly sloupců, vždycky vytvořte **Styl DataGridColumnStyle** objekty a přidat je do **kolekce GridColumnStylesCollection** objekt před přidáním  **Styl DataGridTableStyle** objekty ke **GridTableStylesCollection** objektu.</span><span class="sxs-lookup"><span data-stu-id="293ce-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="293ce-113">Když přidáte prázdnou **styl DataGridTableStyle** objektu do kolekce, **Styl DataGridColumnStyle** objekty vygenerují automaticky.</span><span class="sxs-lookup"><span data-stu-id="293ce-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="293ce-114">V důsledku toho se výjimka vyvolána, pokud se pokusíte přidat nové **Styl DataGridColumnStyle** objekty s duplicitní **MappingName** hodnoty k **kolekce GridColumnStylesCollection**objektu.</span><span class="sxs-lookup"><span data-stu-id="293ce-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2.  <span data-ttu-id="293ce-115">Deklarování nový styl tabulky a nastavit jeho název mapování.</span><span class="sxs-lookup"><span data-stu-id="293ce-115">Declare a new table style and set its mapping name.</span></span>  
  
    ```vb  
    Dim ts1 As New DataGridTableStyle()  
    ts1.MappingName = "Customers"  
    ```  
  
    ```csharp  
    DataGridTableStyle ts1 = new DataGridTableStyle();  
    ts1.MappingName = "Customers";  
    ```  
  
    ```cpp  
    DataGridTableStyle* ts1 = new DataGridTableStyle();  
    ts1->MappingName = S"Customers";  
    ```  
  
3.  <span data-ttu-id="293ce-116">Deklarace styl nové sloupce a nastavit jeho název mapování a další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="293ce-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
    ```vb  
    Dim myDataCol As New DataGridBoolColumn()  
    myDataCol.HeaderText = "My New Column"  
    myDataCol.MappingName = "Current"  
    ```  
  
    ```csharp  
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();  
    myDataCol.HeaderText = "My New Column";  
    myDataCol.MappingName = "Current";  
    ```  
  
    ```cpp  
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();  
    myDataCol->HeaderText = "My New Column";  
    myDataCol->MappingName = "Current";  
    ```  
  
4.  <span data-ttu-id="293ce-117">Volání **přidat** metodu **kolekce GridColumnStylesCollection** objekt, který chcete přidat sloupce do tabulky styl</span><span class="sxs-lookup"><span data-stu-id="293ce-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  <span data-ttu-id="293ce-118">Volání **přidat** metodu **GridTableStylesCollection** objekt, který chcete přidat styl tabulky k mřížce data.</span><span class="sxs-lookup"><span data-stu-id="293ce-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="293ce-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="293ce-119">See Also</span></span>  
 [<span data-ttu-id="293ce-120">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="293ce-120">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="293ce-121">Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="293ce-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
