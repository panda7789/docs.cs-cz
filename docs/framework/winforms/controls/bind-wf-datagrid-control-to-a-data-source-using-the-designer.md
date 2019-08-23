---
title: 'Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí Návrháře'
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
ms.openlocfilehash: 665a1af990aaf615c763c1c2eae508024d9de5c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917831"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="c7eb5-102">Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="c7eb5-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="c7eb5-103">Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="c7eb5-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="c7eb5-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c7eb5-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

 <span data-ttu-id="c7eb5-105">Model Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek je speciálně navržen pro zobrazení informací ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="c7eb5-106">Ovládací prvek navážete v době návrhu nastavením <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastností a a <xref:System.Windows.Forms.DataGrid.DataMember%2A> v době <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> spuštění voláním metody.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="c7eb5-107">I když můžete zobrazit data z nejrůznějších zdrojů dat, nejdůležitější zdroje jsou datové sady a zobrazení dat.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>

 <span data-ttu-id="c7eb5-108">Pokud je zdroj dat k dispozici v době návrhu, například pokud formulář obsahuje instanci datové sady nebo zobrazení dat, můžete vytvořit vazby mezi mřížkou a zdrojem dat v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="c7eb5-109">Pak můžete zobrazit náhled toho, jak budou data vypadat v mřížce.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-109">You can then preview what the data will look like in the grid.</span></span>

 <span data-ttu-id="c7eb5-110">Mřížku lze také vytvořit pomocí kódu programu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="c7eb5-111">To je užitečné, pokud chcete nastavit zdroj dat na základě informací, které získáte v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="c7eb5-112">Aplikace může například uživateli umožnit zadání názvu tabulky, která se má zobrazit.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="c7eb5-113">Je také nutné v situacích, kdy zdroj dat neexistuje v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="c7eb5-114">To zahrnuje zdroje dat, jako jsou pole, kolekce, netypové datové sady a čtečky dat.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>

 <span data-ttu-id="c7eb5-115">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGrid> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="c7eb5-116">Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="c7eb5-117">V sadě Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> není ovládací prvek ve výchozím nastavení součástí **sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="c7eb5-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="c7eb5-118">Informace o jeho přidání naleznete v tématu [How to: Přidejte položky do sady nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c7eb5-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="c7eb5-119">Kromě toho v aplikaci Visual Studio 2005 můžete použít okno **zdroje dat** pro datovou vazbu při návrhu.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="c7eb5-120">Další informace najdete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="c7eb5-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="c7eb5-121">Pro datovou datovou vazby ovládacího prvku DataGrid k jedné tabulce v Návrháři</span><span class="sxs-lookup"><span data-stu-id="c7eb5-121">To data-bind the DataGrid control to a single table in the designer</span></span>

1. <span data-ttu-id="c7eb5-122">Nastavte <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost ovládacího prvku na objekt obsahující datové položky, se kterými chcete vytvořit vazby.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-122">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="c7eb5-123">Pokud je zdrojem dat datová sada, nastavte <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost na název tabulky, ke které se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-123">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>

3. <span data-ttu-id="c7eb5-124">Pokud je zdrojem dat datová sada nebo zobrazení dat založené na tabulce DataSet, přidejte do formuláře kód, který datovou sadu vyplní.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-124">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>

     <span data-ttu-id="c7eb5-125">Přesný kód, který použijete, závisí na tom, kde datová sada získává data.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-125">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="c7eb5-126">Pokud je datová sada naplněna přímo z databáze, obvykle zavoláte `Fill` metodu datového adaptéru, jak je uvedeno v následujícím příkladu kódu, který naplňuje datovou sadu s `DsCategories1`názvem:</span><span class="sxs-lookup"><span data-stu-id="c7eb5-126">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. <span data-ttu-id="c7eb5-127">Volitelné Přidejte do mřížky vhodné styly tabulek a sloupců.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-127">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>

     <span data-ttu-id="c7eb5-128">Pokud neexistují žádné styly tabulek, zobrazí se tabulka, ale s minimálním formátováním a všemi zobrazenými sloupci.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-128">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="c7eb5-129">Vazba ovládacího prvku DataGrid na více tabulek v datové sadě v Návrháři</span><span class="sxs-lookup"><span data-stu-id="c7eb5-129">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>

1. <span data-ttu-id="c7eb5-130">Nastavte <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost ovládacího prvku na objekt obsahující datové položky, se kterými chcete vytvořit vazby.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-130">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="c7eb5-131">Pokud datová sada obsahuje související tabulky (to znamená, pokud obsahuje objekt relace), nastavte <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost na název nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-131">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>

3. <span data-ttu-id="c7eb5-132">Zadejte kód, který bude datovou sadu vyplnit.</span><span class="sxs-lookup"><span data-stu-id="c7eb5-132">Write code to fill the dataset.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7eb5-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7eb5-133">See also</span></span>

- [<span data-ttu-id="c7eb5-134">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="c7eb5-134">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="c7eb5-135">Postupy: Přidání tabulek a sloupců do model Windows Forms ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="c7eb5-135">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="c7eb5-136">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="c7eb5-136">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="c7eb5-137">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="c7eb5-137">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="c7eb5-138">Přístup k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c7eb5-138">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
