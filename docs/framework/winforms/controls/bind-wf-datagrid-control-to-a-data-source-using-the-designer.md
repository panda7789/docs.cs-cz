---
title: 'Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí návrháře'
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
ms.openlocfilehash: 414c989d258ca4b7a9097afa2b7f2407505fb629
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687580"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="20ba2-102">Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="20ba2-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
>  <span data-ttu-id="20ba2-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="20ba2-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="20ba2-104">Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="20ba2-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="20ba2-105">Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek je navržená speciálně pro zobrazení informací ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="20ba2-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="20ba2-106">Vazbu ovládacího prvku v době návrhu tak, že nastavíte <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti, nebo za běhu pomocí volání <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="20ba2-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="20ba2-107">Přestože lze zobrazit data z různých zdrojů dat, obvykle zdroje jsou datové sady a data zobrazení.</span><span class="sxs-lookup"><span data-stu-id="20ba2-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
 <span data-ttu-id="20ba2-108">Pokud zdroj dat je k dispozici v době návrhu – například, pokud formulář obsahuje instance datové sady nebo zobrazení dat – mřížky můžete vázat na zdroj dat v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="20ba2-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="20ba2-109">Pak můžete zobrazit náhled dat bude vypadat v mřížce.</span><span class="sxs-lookup"><span data-stu-id="20ba2-109">You can then preview what the data will look like in the grid.</span></span>  
  
 <span data-ttu-id="20ba2-110">Můžete také navázat mřížky prostřednictvím kódu programu, v době běhu.</span><span class="sxs-lookup"><span data-stu-id="20ba2-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="20ba2-111">To je užitečné, když chcete nastavit zdroj dat na základě informací, které získáte v době běhu.</span><span class="sxs-lookup"><span data-stu-id="20ba2-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="20ba2-112">Například aplikace může uživatelům povolit, zadejte název tabulky. Chcete-li zobrazit.</span><span class="sxs-lookup"><span data-stu-id="20ba2-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="20ba2-113">Je také nutné v situacích, kde se zdroji dat neexistuje v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="20ba2-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="20ba2-114">To zahrnuje zdroje dat, jako je například pole, kolekcí, netypové datové sady a čtečky dat.</span><span class="sxs-lookup"><span data-stu-id="20ba2-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>  
  
 <span data-ttu-id="20ba2-115">Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGrid> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="20ba2-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="20ba2-116">Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [jak: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="20ba2-116">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="20ba2-117">V sadě Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> ovládací prvek není v **nástrojů** ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="20ba2-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="20ba2-118">Informace o jeho přidání, naleznete v tématu [jak: Přidání položek do panelu nástrojů](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).</span><span class="sxs-lookup"><span data-stu-id="20ba2-118">For information about adding it, see [How to: Add Items to the Toolbox](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).</span></span> <span data-ttu-id="20ba2-119">Kromě toho v sadě Visual Studio 2005, můžete použít **zdroje dat** okno pro vytvoření vazby dat doby návrhu.</span><span class="sxs-lookup"><span data-stu-id="20ba2-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="20ba2-120">Další informace najdete v části [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="20ba2-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20ba2-121">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="20ba2-121">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="20ba2-122">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="20ba2-122">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="20ba2-123">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="20ba2-123">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="20ba2-124">Chcete svázat data – ovládací prvek DataGrid jedné tabulky v Návrháři</span><span class="sxs-lookup"><span data-stu-id="20ba2-124">To data-bind the DataGrid control to a single table in the designer</span></span>  
  
1.  <span data-ttu-id="20ba2-125">Nastavit u tohoto prvku <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost na objekt obsahující data položky, které chcete vytvořit vazbu.</span><span class="sxs-lookup"><span data-stu-id="20ba2-125">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="20ba2-126">Pokud zdroj dat je datová sada, nastavte <xref:System.Windows.Forms.DataGrid.DataMember%2A> nastavte název tabulky k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="20ba2-126">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>  
  
3.  <span data-ttu-id="20ba2-127">Pokud je zdroj dat datové sady nebo zobrazení dat na základě tabulky datovou sadu, přidejte kód pro formulář k vyplnění datové sady.</span><span class="sxs-lookup"><span data-stu-id="20ba2-127">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="20ba2-128">Přesný kód, který používáte závisí na datové sady je kde získávají data.</span><span class="sxs-lookup"><span data-stu-id="20ba2-128">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="20ba2-129">Pokud probíhá naplňování datové sady přímo z databáze, obvykle volat `Fill` metoda adaptéru dat, stejně jako v následujícím příkladu kódu, který naplňuje datovou sadu s názvem `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="20ba2-129">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  <span data-ttu-id="20ba2-130">(Volitelné) Přidejte příslušné tabulky styly a styly sloupců do mřížky.</span><span class="sxs-lookup"><span data-stu-id="20ba2-130">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>  
  
     <span data-ttu-id="20ba2-131">Pokud neexistují žádné tabulky styly, zobrazí se v tabulce, ale s minimální formátování a všechny viditelné sloupce.</span><span class="sxs-lookup"><span data-stu-id="20ba2-131">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="20ba2-132">Chcete svázat data – ovládací prvek DataGrid více tabulek v datové sadě v Návrháři</span><span class="sxs-lookup"><span data-stu-id="20ba2-132">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>  
  
1.  <span data-ttu-id="20ba2-133">Nastavit u tohoto prvku <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost na objekt obsahující data položky, které chcete vytvořit vazbu.</span><span class="sxs-lookup"><span data-stu-id="20ba2-133">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="20ba2-134">Pokud datová sada obsahuje související tabulky (to znamená, pokud obsahuje objekt relace), můžete nastavit <xref:System.Windows.Forms.DataGrid.DataMember%2A> nastavte název nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="20ba2-134">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>  
  
3.  <span data-ttu-id="20ba2-135">Napište kód pro naplnění dataset.</span><span class="sxs-lookup"><span data-stu-id="20ba2-135">Write code to fill the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ba2-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20ba2-136">See also</span></span>
- [<span data-ttu-id="20ba2-137">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="20ba2-137">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="20ba2-138">Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="20ba2-138">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="20ba2-139">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="20ba2-139">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
- [<span data-ttu-id="20ba2-140">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="20ba2-140">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)
- [<span data-ttu-id="20ba2-141">Přístup k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="20ba2-141">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
