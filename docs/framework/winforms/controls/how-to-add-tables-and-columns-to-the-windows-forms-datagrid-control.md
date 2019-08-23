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
ms.openlocfilehash: 55e30744f57364fb37c9fde5b6bade6bab60fa26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925092"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="449da-102">Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="449da-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="449da-103">Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="449da-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="449da-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="449da-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="449da-105">Můžete zobrazit data v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGrid> v tabulkách a sloupcích vytvořením objektů **Styl DataGridTableStyle** a jejich přidáním do objektu **GridTableStylesCollection** <xref:System.Windows.Forms.DataGrid> , který je k dispozici prostřednictvím ovládacího prvku Vlastnost **TableStyles**</span><span class="sxs-lookup"><span data-stu-id="449da-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="449da-106">Každý styl tabulky zobrazuje obsah libovolné tabulky dat, která je zadána ve vlastnosti **Mapping** **Styl DataGridTableStyle** objektu.</span><span class="sxs-lookup"><span data-stu-id="449da-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="449da-107">Ve výchozím nastavení zobrazí styl tabulky bez zadaných stylů sloupců všechny sloupce v této tabulce dat.</span><span class="sxs-lookup"><span data-stu-id="449da-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="449da-108">Můžete omezit, které sloupce z tabulky se zobrazí přidáním objektů **styl DataGridColumnStyle** do objektu **kolekce GridColumnStylesCollection** , který je k dispozici prostřednictvím vlastnosti **GridColumnStyles** každého **Styl DataGridTableStyle** předmětů.</span><span class="sxs-lookup"><span data-stu-id="449da-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="449da-109">Přidání tabulky a sloupce do DataGrid programově</span><span class="sxs-lookup"><span data-stu-id="449da-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="449da-110">Aby bylo možné zobrazit data v tabulce, je nutné nejprve navazovat <xref:System.Windows.Forms.DataGrid> ovládací prvek na datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="449da-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="449da-111">Další informace najdete v tématu [jak: Navažte model Windows Forms ovládací prvek DataGrid na zdroj](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)dat.</span><span class="sxs-lookup"><span data-stu-id="449da-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="449da-112">Při programovém zadání stylů sloupců vždy vytvořit objekty **styl DataGridColumnStyle** a přidat je do objektu **kolekce GridColumnStylesCollection** před přidáním objektů **Styl DataGridTableStyle** do  **Objekt GridTableStylesCollection**</span><span class="sxs-lookup"><span data-stu-id="449da-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="449da-113">Když do kolekce přidáte prázdný objekt **Styl DataGridTableStyle** , automaticky se vygenerují objekty **styl DataGridColumnStyle** .</span><span class="sxs-lookup"><span data-stu-id="449da-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="449da-114">V důsledku toho bude vyvolána výjimka, pokud se pokusíte přidat nové objekty **styl DataGridColumnStyle** s duplicitními hodnotami **mapování** na objekt **kolekce GridColumnStylesCollection** .</span><span class="sxs-lookup"><span data-stu-id="449da-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2. <span data-ttu-id="449da-115">Deklarujete nový styl tabulky a nastavte jeho název mapování.</span><span class="sxs-lookup"><span data-stu-id="449da-115">Declare a new table style and set its mapping name.</span></span>  
  
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
  
3. <span data-ttu-id="449da-116">Deklarujete nový styl sloupce a nastavte jeho název mapování a další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="449da-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
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
  
4. <span data-ttu-id="449da-117">Voláním metody **Add** objektu **kolekce GridColumnStylesCollection** přidejte sloupec do stylu tabulky.</span><span class="sxs-lookup"><span data-stu-id="449da-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5. <span data-ttu-id="449da-118">Voláním metody **Add** objektu **GridTableStylesCollection** přidejte do datové mřížky styl tabulky.</span><span class="sxs-lookup"><span data-stu-id="449da-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="449da-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="449da-119">See also</span></span>

- [<span data-ttu-id="449da-120">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="449da-120">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="449da-121">Postupy: Odstranění nebo skrytí sloupců v model Windows Forms ovládacím prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="449da-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
