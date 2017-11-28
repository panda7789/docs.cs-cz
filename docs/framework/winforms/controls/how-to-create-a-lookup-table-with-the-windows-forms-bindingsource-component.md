---
title: "Postupy: Vytváření vyhledávacích tabulek s komponentou Windows Forms BindingSource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27c1c6cd0e617c0940a734e7e16a3ec5d12f920d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="cfa2b-102">Postupy: Vytváření vyhledávacích tabulek s komponentou Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="cfa2b-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="cfa2b-103">Vyhledávací tabulky je tabulka dat, která má sloupec, který zobrazí data z záznamy související tabulky.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="cfa2b-104">V následujících postupech <xref:System.Windows.Forms.ComboBox> řízení se používá k zobrazení pole s relace cizího klíče z nadřazené do podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="cfa2b-105">Pomoc při vizualizovat tyto dvě tabulky a tuto relaci, tady je příklad nadřazenou a podřízenou tabulku:</span><span class="sxs-lookup"><span data-stu-id="cfa2b-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="cfa2b-106">CustomersTable (nadřazenou tabulkou)</span><span class="sxs-lookup"><span data-stu-id="cfa2b-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="cfa2b-107">CustomerID</span><span class="sxs-lookup"><span data-stu-id="cfa2b-107">CustomerID</span></span>|<span data-ttu-id="cfa2b-108">JménoZákazníka</span><span class="sxs-lookup"><span data-stu-id="cfa2b-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="cfa2b-109">712</span><span class="sxs-lookup"><span data-stu-id="cfa2b-109">712</span></span>|<span data-ttu-id="cfa2b-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="cfa2b-110">Paul Koch</span></span>|  
|<span data-ttu-id="cfa2b-111">713</span><span class="sxs-lookup"><span data-stu-id="cfa2b-111">713</span></span>|<span data-ttu-id="cfa2b-112">Johnstonův Tamare</span><span class="sxs-lookup"><span data-stu-id="cfa2b-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="cfa2b-113">OrdersTable (podřízené tabulky)</span><span class="sxs-lookup"><span data-stu-id="cfa2b-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="cfa2b-114">OrderID</span><span class="sxs-lookup"><span data-stu-id="cfa2b-114">OrderID</span></span>|<span data-ttu-id="cfa2b-115">OrderDate</span><span class="sxs-lookup"><span data-stu-id="cfa2b-115">OrderDate</span></span>|<span data-ttu-id="cfa2b-116">CustomerID</span><span class="sxs-lookup"><span data-stu-id="cfa2b-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="cfa2b-117">903</span><span class="sxs-lookup"><span data-stu-id="cfa2b-117">903</span></span>|<span data-ttu-id="cfa2b-118">12. února 2004</span><span class="sxs-lookup"><span data-stu-id="cfa2b-118">February 12, 2004</span></span>|<span data-ttu-id="cfa2b-119">712</span><span class="sxs-lookup"><span data-stu-id="cfa2b-119">712</span></span>|  
|<span data-ttu-id="cfa2b-120">904</span><span class="sxs-lookup"><span data-stu-id="cfa2b-120">904</span></span>|<span data-ttu-id="cfa2b-121">13. února 2004</span><span class="sxs-lookup"><span data-stu-id="cfa2b-121">February 13, 2004</span></span>|<span data-ttu-id="cfa2b-122">713</span><span class="sxs-lookup"><span data-stu-id="cfa2b-122">713</span></span>|  
  
 <span data-ttu-id="cfa2b-123">V tomto scénáři jedna tabulka, CustomersTable, ukládá informace, které chcete zobrazit a uložit.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="cfa2b-124">Ale ušetřit místo, v tabulce ponechá data, která přidává přehlednost.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="cfa2b-125">Jiné tabulky, OrdersTable, obsahuje pouze týkající se vzhledu informace o zákazníkovi, který je ekvivalentní které datu objednávky a pořadí ID číslo ID</span><span class="sxs-lookup"><span data-stu-id="cfa2b-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="cfa2b-126">Neexistuje žádné zmínky názvů zákazníků.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="cfa2b-127">Čtyři důležité vlastnosti jsou nastaveny na [ComboBox – ovládací prvek](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) řízení se vytvořit vyhledávací tabulku.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-127">Four important properties are set on the [ComboBox Control](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
-   <span data-ttu-id="cfa2b-128"><xref:System.Windows.Forms.ComboBox.DataSource%2A> Vlastnost obsahuje název tabulky.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
-   <span data-ttu-id="cfa2b-129"><xref:System.Windows.Forms.ListControl.DisplayMember%2A> Vlastnost obsahuje sloupce dat z této tabulky, které chcete zobrazit pro ovládací prvek text (název zákazníka).</span><span class="sxs-lookup"><span data-stu-id="cfa2b-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
-   <span data-ttu-id="cfa2b-130"><xref:System.Windows.Forms.ListControl.ValueMember%2A> Vlastnost obsahuje sloupce dat této tabulky s uložené informace (číslo ID v nadřazené tabulce).</span><span class="sxs-lookup"><span data-stu-id="cfa2b-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
-   <span data-ttu-id="cfa2b-131"><xref:System.Windows.Forms.ListControl.SelectedValue%2A> Vlastnost poskytuje vyhledávací hodnota pro podřízené tabulky, na základě <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="cfa2b-132">Následující postupy ukazují, jak Rozvrhněte svůj formulář jako vyhledávací tabulky a vytvoření vazby dat k ovládacím prvkům v něm.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="cfa2b-133">Úspěšné dokončení postupů, musíte mít k datovému zdroji prostřednictvím nadřazené a podřízené tabulky, které mají relaci cizího klíče, jak je uvedeno nahoře.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="cfa2b-134">Vytvoření uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfa2b-134">To create the user interface</span></span>  
  
1.  <span data-ttu-id="cfa2b-135">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.ComboBox> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="cfa2b-136">Tento ovládací prvek zobrazí sloupce z tabulky nadřazené.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-136">This control will display the column from parent table.</span></span>  
  
2.  <span data-ttu-id="cfa2b-137">Přetáhněte další ovládací prvky a zobrazte detaily z podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="cfa2b-138">Formát dat v tabulce měli určit ovládacích prvků, které zvolíte.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="cfa2b-139">Další informace najdete v tématu [ovládacích prvků Windows Forms podle funkce](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="cfa2b-139">For more information, see [Windows Forms Controls by Function](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).</span></span>  
  
3.  <span data-ttu-id="cfa2b-140">Přetažení <xref:System.Windows.Forms.BindingNavigator> na formuláři ovládací prvek; to vám umožní procházení dat v podřízené tabulce.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="cfa2b-141">Připojte se k datům a navázat jej na ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="cfa2b-141">To connect to the data and bind it to controls</span></span>  
  
1.  <span data-ttu-id="cfa2b-142">Vyberte <xref:System.Windows.Forms.ComboBox> a klikněte na inteligentní úloh glyfy k zobrazení dialogového okna inteligentní úlohu.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2.  <span data-ttu-id="cfa2b-143">Vyberte **používat data vázaný položky**.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-143">Select **Use data bound items**.</span></span>  
  
3.  <span data-ttu-id="cfa2b-144">Klikněte na šipku vedle položky **zdroj dat** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="cfa2b-145">Pokud zdroj dat byl dříve nakonfigurován pro projekt nebo formuláře, zobrazí se; jinak proveďte následující kroky (Tento příklad používá zákazníci a objednávky tabulky ukázková databáze Northwind a odkazuje na ně v závorkách).</span><span class="sxs-lookup"><span data-stu-id="cfa2b-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1.  <span data-ttu-id="cfa2b-146">Klikněte na tlačítko **přidat zdroj dat projektu** vytvořte zdroj dat a připojte se k datům.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2.  <span data-ttu-id="cfa2b-147">Na **Průvodce konfigurací zdroje dat** úvodní stránce, klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3.  <span data-ttu-id="cfa2b-148">Vyberte **databáze** na **zvolte typ zdroje dat** stránky.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4.  <span data-ttu-id="cfa2b-149">Vybrat datové připojení ze seznamu dostupných připojení na **vybrat datové připojení** stránky.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="cfa2b-150">Pokud není k dispozici připojení k požadovaným datům, vyberte **nové připojení** k vytvoření nové datové připojení.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5.  <span data-ttu-id="cfa2b-151">Klikněte na tlačítko **Ano, uložte připojení** uložení připojovací řetězec v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6.  <span data-ttu-id="cfa2b-152">Vyberte objekty databáze zařazení do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="cfa2b-153">V takovém případě vyberte nadřazenou tabulkou a podřízenou tabulku (například Zákazníci a objednávky) s relace cizího klíče.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7.  <span data-ttu-id="cfa2b-154">Pokud chcete, nahradí výchozí název datové sady.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-154">Replace the default dataset name if you want.</span></span>  
  
    8.  <span data-ttu-id="cfa2b-155">Klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-155">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="cfa2b-156">V **zobrazení člen** rozevíracího seznamu, vyberte název sloupce (například kontakt) má být zobrazen v poli se seznamem.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5.  <span data-ttu-id="cfa2b-157">V **hodnotu člena** rozevíracího seznamu vyberte sloupec (například CustomerID) k provedení operace vyhledávání v podřízené tabulce.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6.  <span data-ttu-id="cfa2b-158">V **vybraná hodnota** rozevíracího pole, přejděte na **zdroje dat projektu** a datové jste právě vytvořili, který obsahuje nadřazenou a podřízenou tabulkou.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="cfa2b-159">Vyberte stejnou vlastnost podřízené tabulky, který je členem hodnotu v nadřazené tabulce (například Orders.CustomerID).</span><span class="sxs-lookup"><span data-stu-id="cfa2b-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="cfa2b-160">Odpovídající <xref:System.Windows.Forms.BindingSource> , sadu dat a tabulka adaptér součásti bude vytvořen a přidán do formuláře.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7.  <span data-ttu-id="cfa2b-161">Vytvoření vazby <xref:System.Windows.Forms.BindingNavigator> řídit k <xref:System.Windows.Forms.BindingSource> podřízené tabulky (například `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="cfa2b-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8.  <span data-ttu-id="cfa2b-162">Vytvoření vazby ovládacích prvků jiné než <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku na podrobnosti o pole z podřízené tabulky <xref:System.Windows.Forms.BindingSource> (například `OrdersBindingSource`), kterou chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="cfa2b-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa2b-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfa2b-163">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="cfa2b-164">BindingSource – komponenta</span><span class="sxs-lookup"><span data-stu-id="cfa2b-164">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="cfa2b-165">ComboBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="cfa2b-165">ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)  
 [<span data-ttu-id="cfa2b-166">Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cfa2b-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
