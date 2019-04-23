---
title: 'Postupy: Vytvoření vyhledávací tabulky s komponentou Windows Forms BindingSource'
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: 481774e9127531bb38df0cc71ac8e7eab76da695
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321897"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="fba5f-102">Postupy: Vytvoření vyhledávací tabulky s komponentou Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="fba5f-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="fba5f-103">Vyhledávací tabulka je tabulka dat, která má sloupec, který zobrazuje data ze záznamů v související tabulce.</span><span class="sxs-lookup"><span data-stu-id="fba5f-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="fba5f-104">V následujících postupech <xref:System.Windows.Forms.ComboBox> ovládacího prvku se používá k zobrazení pole relace cizího klíče z nadřazené do podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="fba5f-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="fba5f-105">Pomáhají vizualizovat tyto dvě tabulky a tento vztah, tady je příklad nadřazené a podřízené tabulky:</span><span class="sxs-lookup"><span data-stu-id="fba5f-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="fba5f-106">CustomersTable (nadřazené tabulky)</span><span class="sxs-lookup"><span data-stu-id="fba5f-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="fba5f-107">ID zákazníka</span><span class="sxs-lookup"><span data-stu-id="fba5f-107">CustomerID</span></span>|<span data-ttu-id="fba5f-108">Zákazníka</span><span class="sxs-lookup"><span data-stu-id="fba5f-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="fba5f-109">712</span><span class="sxs-lookup"><span data-stu-id="fba5f-109">712</span></span>|<span data-ttu-id="fba5f-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="fba5f-110">Paul Koch</span></span>|  
|<span data-ttu-id="fba5f-111">713</span><span class="sxs-lookup"><span data-stu-id="fba5f-111">713</span></span>|<span data-ttu-id="fba5f-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="fba5f-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="fba5f-113">OrdersTable (podřízenou tabulku)</span><span class="sxs-lookup"><span data-stu-id="fba5f-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="fba5f-114">ID objednávky</span><span class="sxs-lookup"><span data-stu-id="fba5f-114">OrderID</span></span>|<span data-ttu-id="fba5f-115">OrderDate</span><span class="sxs-lookup"><span data-stu-id="fba5f-115">OrderDate</span></span>|<span data-ttu-id="fba5f-116">ID zákazníka</span><span class="sxs-lookup"><span data-stu-id="fba5f-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="fba5f-117">903</span><span class="sxs-lookup"><span data-stu-id="fba5f-117">903</span></span>|<span data-ttu-id="fba5f-118">12. února 2004</span><span class="sxs-lookup"><span data-stu-id="fba5f-118">February 12, 2004</span></span>|<span data-ttu-id="fba5f-119">712</span><span class="sxs-lookup"><span data-stu-id="fba5f-119">712</span></span>|  
|<span data-ttu-id="fba5f-120">904</span><span class="sxs-lookup"><span data-stu-id="fba5f-120">904</span></span>|<span data-ttu-id="fba5f-121">13. února 2004</span><span class="sxs-lookup"><span data-stu-id="fba5f-121">February 13, 2004</span></span>|<span data-ttu-id="fba5f-122">713</span><span class="sxs-lookup"><span data-stu-id="fba5f-122">713</span></span>|  
  
 <span data-ttu-id="fba5f-123">V tomto scénáři jedné tabulky, CustomersTable, ukládá informace, které chcete zobrazit a uložte.</span><span class="sxs-lookup"><span data-stu-id="fba5f-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="fba5f-124">Ale pro úsporu místa, v tabulce ponechá si data, která se přidá na srozumitelnosti.</span><span class="sxs-lookup"><span data-stu-id="fba5f-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="fba5f-125">Dalších table OrdersTable, obsahuje pouze vzhled související informace o zákazníkovi, který je ekvivalentní k které data objednávky a pořadí ID. identifikační číslo</span><span class="sxs-lookup"><span data-stu-id="fba5f-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="fba5f-126">Není k dispozici žádnou zmínku o názvy zákazníků.</span><span class="sxs-lookup"><span data-stu-id="fba5f-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="fba5f-127">Čtyři důležité vlastnosti jsou nastaveny na [ovládacího prvku ComboBox](combobox-control-windows-forms.md) ovládacího prvku k vytvoření vyhledávací tabulky.</span><span class="sxs-lookup"><span data-stu-id="fba5f-127">Four important properties are set on the [ComboBox Control](combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
-   <span data-ttu-id="fba5f-128"><xref:System.Windows.Forms.ComboBox.DataSource%2A> Vlastnosti obsahuje název tabulky.</span><span class="sxs-lookup"><span data-stu-id="fba5f-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
-   <span data-ttu-id="fba5f-129"><xref:System.Windows.Forms.ListControl.DisplayMember%2A> Vlastnost obsahuje sloupce dat této tabulky, kterou chcete zobrazit pro ovládací prvek text (jméno zákazníka).</span><span class="sxs-lookup"><span data-stu-id="fba5f-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
-   <span data-ttu-id="fba5f-130"><xref:System.Windows.Forms.ListControl.ValueMember%2A> Vlastnost obsahuje sloupce dat této tabulky s uložené informace (číslo ID nadřazené tabulky).</span><span class="sxs-lookup"><span data-stu-id="fba5f-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
-   <span data-ttu-id="fba5f-131"><xref:System.Windows.Forms.ListControl.SelectedValue%2A> Vlastnost obsahuje hodnotu vyhledávání pro podřízené tabulky, na základě <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="fba5f-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="fba5f-132">Následující postupy ukazují, jak Rozvrhněte svůj formulář jako vyhledávací tabulky a vytvoření vazby dat k ovládacím prvkům v něm.</span><span class="sxs-lookup"><span data-stu-id="fba5f-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="fba5f-133">Pro úspěšné dokončení procedury, musí mít zdroj dat s nadřazenými a podřízenými tabulkami, které existuje vztah cizího klíče, jak již bylo zmíněno dříve.</span><span class="sxs-lookup"><span data-stu-id="fba5f-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="fba5f-134">Vytvoření uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fba5f-134">To create the user interface</span></span>  
  
1. <span data-ttu-id="fba5f-135">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.ComboBox> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="fba5f-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="fba5f-136">Tento ovládací prvek zobrazí sloupec z nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="fba5f-136">This control will display the column from parent table.</span></span>  
  
2. <span data-ttu-id="fba5f-137">Přetáhněte jiných ovládacích prvků pro zobrazení podrobností z podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="fba5f-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="fba5f-138">Formát dat v tabulce byste určit, jaké ovládací prvky, které zvolíte.</span><span class="sxs-lookup"><span data-stu-id="fba5f-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="fba5f-139">Další informace najdete v tématu [ovládacích prvků Windows Forms podle funkce](windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="fba5f-139">For more information, see [Windows Forms Controls by Function](windows-forms-controls-by-function.md).</span></span>  
  
3. <span data-ttu-id="fba5f-140">Přetáhněte <xref:System.Windows.Forms.BindingNavigator> ovládací prvek do formuláře; to vám umožní procházet data v podřízené tabulce.</span><span class="sxs-lookup"><span data-stu-id="fba5f-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="fba5f-141">Připojte se k datům a svázat ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="fba5f-141">To connect to the data and bind it to controls</span></span>  
  
1. <span data-ttu-id="fba5f-142">Vyberte <xref:System.Windows.Forms.ComboBox> a klikněte na inteligentní úloh glyfů pro zobrazení dialogového okna inteligentních úlohu.</span><span class="sxs-lookup"><span data-stu-id="fba5f-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2. <span data-ttu-id="fba5f-143">Vyberte **položky vázané na data použijte**.</span><span class="sxs-lookup"><span data-stu-id="fba5f-143">Select **Use data bound items**.</span></span>  
  
3. <span data-ttu-id="fba5f-144">Klikněte na šipku vedle položky **zdroj dat** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="fba5f-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="fba5f-145">Pokud zdroj dat byl dříve nakonfigurován pro projekt nebo formuláře, zobrazí se; v opačném případě proveďte následující kroky (Tento příklad používá tabulky Zákazníci a objednávky v ukázkové databázi Northwind a odkazuje na ně v závorkách).</span><span class="sxs-lookup"><span data-stu-id="fba5f-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1.  <span data-ttu-id="fba5f-146">Klikněte na tlačítko **přidat zdroj dat projektu** vytvořit zdroj dat a připojte se k datům.</span><span class="sxs-lookup"><span data-stu-id="fba5f-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2.  <span data-ttu-id="fba5f-147">Na **Průvodce konfigurací zdroje dat** úvodní stránka, klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="fba5f-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3.  <span data-ttu-id="fba5f-148">Vyberte **databáze** na **zvolte typ zdroje dat** stránky.</span><span class="sxs-lookup"><span data-stu-id="fba5f-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4.  <span data-ttu-id="fba5f-149">Vybrat datové připojení ze seznamu dostupných připojení na **vyberte datové připojení** stránky.</span><span class="sxs-lookup"><span data-stu-id="fba5f-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="fba5f-150">Pokud požadované datové připojení není k dispozici, vyberte **nové připojení** k vytvoření nové datové připojení.</span><span class="sxs-lookup"><span data-stu-id="fba5f-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5.  <span data-ttu-id="fba5f-151">Klikněte na tlačítko **Ano, uložit připojení** uložit připojovací řetězec do konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="fba5f-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6.  <span data-ttu-id="fba5f-152">Vyberte databázové objekty do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fba5f-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="fba5f-153">V tomto případě vyberte tabulky nadřazené a podřízené tabulky (například Zákazníci a objednávky) se vztahu cizího klíče.</span><span class="sxs-lookup"><span data-stu-id="fba5f-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7.  <span data-ttu-id="fba5f-154">Nahraďte výchozí název datové sady, chcete-li.</span><span class="sxs-lookup"><span data-stu-id="fba5f-154">Replace the default dataset name if you want.</span></span>  
  
    8.  <span data-ttu-id="fba5f-155">Klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="fba5f-155">Click **Finish**.</span></span>  
  
4. <span data-ttu-id="fba5f-156">V **členem zobrazení** rozevíracího seznamu vyberte název sloupce (například jméno kontaktu) který se má zobrazit v poli se seznamem.</span><span class="sxs-lookup"><span data-stu-id="fba5f-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5. <span data-ttu-id="fba5f-157">V **člen s hodnotou** rozevíracího seznamu vyberte sloupce (například ID zákazníka) k provedení této operace vyhledávání v podřízené tabulce.</span><span class="sxs-lookup"><span data-stu-id="fba5f-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6. <span data-ttu-id="fba5f-158">V **vybraná hodnota** rozevíracího seznamu, přejděte na **zdroje dat projektu** a datovou sadu jste právě vytvořili, který obsahuje nadřazené a podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="fba5f-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="fba5f-159">Vyberte stejnou vlastnost u podřízené tabulky, který je členem hodnotu nadřazené tabulky (například Orders.CustomerID).</span><span class="sxs-lookup"><span data-stu-id="fba5f-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="fba5f-160">Odpovídající <xref:System.Windows.Forms.BindingSource> sadu dat a tabulka adaptér součásti bude vytvořen a přidán do formuláře.</span><span class="sxs-lookup"><span data-stu-id="fba5f-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7. <span data-ttu-id="fba5f-161">Vytvoření vazby <xref:System.Windows.Forms.BindingNavigator> ovládací prvek <xref:System.Windows.Forms.BindingSource> podřízené tabulky (například `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="fba5f-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8. <span data-ttu-id="fba5f-162">Jiné než vytvoření vazby ovládacích prvků <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku pro pole podrobnosti z podřízené tabulky <xref:System.Windows.Forms.BindingSource> (například `OrdersBindingSource`), který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="fba5f-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba5f-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fba5f-163">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="fba5f-164">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="fba5f-164">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="fba5f-165">Ovládací prvek ComboBox</span><span class="sxs-lookup"><span data-stu-id="fba5f-165">ComboBox Control</span></span>](combobox-control-windows-forms.md)
- [<span data-ttu-id="fba5f-166">Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fba5f-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
