---
title: Svázání ovládacího prvku DataGrid ke zdroji dat pomocí návrháře
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: cc0a74eca40e34f06b065980d25d922b919b0c3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744085"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="6bca3-102">Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="6bca3-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="6bca3-103">Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="6bca3-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="6bca3-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6bca3-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

 <span data-ttu-id="6bca3-105">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DataGrid> je speciálně navržený tak, aby zobrazoval informace ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="6bca3-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="6bca3-106">Ovládací prvek navážete v době návrhu nastavením vlastností <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> nebo v době spuštění voláním metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="6bca3-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="6bca3-107">I když můžete zobrazit data z nejrůznějších zdrojů dat, nejdůležitější zdroje jsou datové sady a zobrazení dat.</span><span class="sxs-lookup"><span data-stu-id="6bca3-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>

 <span data-ttu-id="6bca3-108">Pokud je zdroj dat k dispozici v době návrhu, například pokud formulář obsahuje instanci datové sady nebo zobrazení dat, můžete vytvořit vazby mezi mřížkou a zdrojem dat v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="6bca3-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="6bca3-109">Pak můžete zobrazit náhled toho, jak budou data vypadat v mřížce.</span><span class="sxs-lookup"><span data-stu-id="6bca3-109">You can then preview what the data will look like in the grid.</span></span>

 <span data-ttu-id="6bca3-110">Mřížku lze také vytvořit pomocí kódu programu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6bca3-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="6bca3-111">To je užitečné, pokud chcete nastavit zdroj dat na základě informací, které získáte v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6bca3-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="6bca3-112">Aplikace může například uživateli umožnit zadání názvu tabulky, která se má zobrazit.</span><span class="sxs-lookup"><span data-stu-id="6bca3-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="6bca3-113">Je také nutné v situacích, kdy zdroj dat neexistuje v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="6bca3-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="6bca3-114">To zahrnuje zdroje dat, jako jsou pole, kolekce, netypové datové sady a čtečky dat.</span><span class="sxs-lookup"><span data-stu-id="6bca3-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>

 <span data-ttu-id="6bca3-115">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="6bca3-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="6bca3-116">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6bca3-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="6bca3-117">V sadě Visual Studio 2005 není ovládací prvek <xref:System.Windows.Forms.DataGrid> ve výchozím nastavení součástí **sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="6bca3-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="6bca3-118">Informace o jeho přidání naleznete v tématu [How to: Add Items to a panel nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6bca3-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="6bca3-119">Kromě toho v aplikaci Visual Studio 2005 můžete použít okno **zdroje dat** pro datovou vazbu při návrhu.</span><span class="sxs-lookup"><span data-stu-id="6bca3-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="6bca3-120">Další informace najdete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="6bca3-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="6bca3-121">Pro datovou datovou vazby ovládacího prvku DataGrid k jedné tabulce v Návrháři</span><span class="sxs-lookup"><span data-stu-id="6bca3-121">To data-bind the DataGrid control to a single table in the designer</span></span>

1. <span data-ttu-id="6bca3-122">Nastavte vlastnost <xref:System.Windows.Forms.DataGrid.DataSource%2A> ovládacího prvku na objekt obsahující datové položky, se kterými chcete vytvořit vazby.</span><span class="sxs-lookup"><span data-stu-id="6bca3-122">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="6bca3-123">Pokud je zdrojem dat datová sada, nastavte vlastnost <xref:System.Windows.Forms.DataGrid.DataMember%2A> na název tabulky, ke které se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="6bca3-123">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>

3. <span data-ttu-id="6bca3-124">Pokud je zdrojem dat datová sada nebo zobrazení dat založené na tabulce DataSet, přidejte do formuláře kód, který datovou sadu vyplní.</span><span class="sxs-lookup"><span data-stu-id="6bca3-124">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>

     <span data-ttu-id="6bca3-125">Přesný kód, který použijete, závisí na tom, kde datová sada získává data.</span><span class="sxs-lookup"><span data-stu-id="6bca3-125">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="6bca3-126">Pokud je datová sada naplněna přímo z databáze, obvykle zavoláte metodu `Fill` datového adaptéru, jak je uvedeno v následujícím příkladu kódu, který naplňuje datovou sadu s názvem `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="6bca3-126">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. <span data-ttu-id="6bca3-127">Volitelné Přidejte do mřížky vhodné styly tabulek a sloupců.</span><span class="sxs-lookup"><span data-stu-id="6bca3-127">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>

     <span data-ttu-id="6bca3-128">Pokud neexistují žádné styly tabulek, zobrazí se tabulka, ale s minimálním formátováním a všemi zobrazenými sloupci.</span><span class="sxs-lookup"><span data-stu-id="6bca3-128">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="6bca3-129">Vazba ovládacího prvku DataGrid na více tabulek v datové sadě v Návrháři</span><span class="sxs-lookup"><span data-stu-id="6bca3-129">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>

1. <span data-ttu-id="6bca3-130">Nastavte vlastnost <xref:System.Windows.Forms.DataGrid.DataSource%2A> ovládacího prvku na objekt obsahující datové položky, se kterými chcete vytvořit vazby.</span><span class="sxs-lookup"><span data-stu-id="6bca3-130">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="6bca3-131">Pokud datová sada obsahuje související tabulky (to znamená, pokud obsahuje objekt relace), nastavte vlastnost <xref:System.Windows.Forms.DataGrid.DataMember%2A> na název nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="6bca3-131">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>

3. <span data-ttu-id="6bca3-132">Zadejte kód, který bude datovou sadu vyplnit.</span><span class="sxs-lookup"><span data-stu-id="6bca3-132">Write code to fill the dataset.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bca3-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bca3-133">See also</span></span>

- [<span data-ttu-id="6bca3-134">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="6bca3-134">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="6bca3-135">Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="6bca3-135">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="6bca3-136">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="6bca3-136">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="6bca3-137">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="6bca3-137">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="6bca3-138">Přístup k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6bca3-138">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
