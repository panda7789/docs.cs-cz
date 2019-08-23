---
title: Přidání existujících omezení do datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 05f95a9c4f250100ca97e3ab52e4073d027df1b8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932186"
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="960eb-102">Přidání existujících omezení do datové sady</span><span class="sxs-lookup"><span data-stu-id="960eb-102">Adding Existing Constraints to a DataSet</span></span>
<span data-ttu-id="960eb-103">Metoda **Fill** v metodě **DataAdapter** vyplní <xref:System.Data.DataSet> pouze sloupce tabulky a řádky ze zdroje dat; i když jsou omezení obvykle nastavena zdrojem dat, metoda **Fill** nepřidá tyto informace o schématu do  **Datová sada** ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="960eb-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="960eb-104">Chcete-li naplnit **datovou sadu** stávajícími informacemi o omezení primárního klíče ze zdroje dat, můžete buď zavolat metodu **FillSchema** objektu **DataAdapter**, nebo nastavit vlastnost **MissingSchemaAction** objektu **DataAdapter** do **AddWithKey** před voláním metody **Fill**.</span><span class="sxs-lookup"><span data-stu-id="960eb-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="960eb-105">Tím se zajistí, aby omezení primárního klíče v **datové sadě** odrážela ta, která jsou ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="960eb-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="960eb-106">Informace o omezeních cizích klíčů nejsou zahrnuty a je nutné je vytvořit explicitně, jak je znázorněno v [omezeních DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="960eb-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="960eb-107">Přidání informací o schématu do **datové sady** předtím, než je naplní data, zajistí, že omezení primárního <xref:System.Data.DataTable> klíče jsou zahrnuta s objekty v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="960eb-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="960eb-108">Výsledkem je, že když se vytvoří další volání pro vyplnění **datové sady** , použijí se informace o sloupci primárního klíče, aby se shodovaly s novými řádky ze zdroje dat s aktuálními řádky v každém **objektu DataTable**a aktuální data v tabulkách byly přepsána daty z zdroj dat</span><span class="sxs-lookup"><span data-stu-id="960eb-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="960eb-109">Bez informací o schématu se nové řádky ze zdroje dat připojí k **datové sadě**, což vede k duplicitním řádkům.</span><span class="sxs-lookup"><span data-stu-id="960eb-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="960eb-110">Pokud je sloupec ve zdroji dat identifikován jako Automatický přírůstek, metoda **FillSchema** nebo metoda **Fill** s **MissingSchemaAction** **AddWithKey**, vytvoří DataColumn s vlastností AutoIncrement. Nastavte na `true`.</span><span class="sxs-lookup"><span data-stu-id="960eb-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="960eb-111">Hodnoty **hodnota AutoIncrementStep** a **AutoIncrementSeed** ale budete muset nastavit sami.</span><span class="sxs-lookup"><span data-stu-id="960eb-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="960eb-112">Další informace o automatických přírůstcích sloupců najdete v tématu [vytváření sloupců AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span><span class="sxs-lookup"><span data-stu-id="960eb-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
 <span data-ttu-id="960eb-113">Použití **FillSchema** nebo nastavení **MissingSchemaAction** na **AddWithKey** vyžaduje dodatečné zpracování ve zdroji dat za účelem určení informací o sloupci primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="960eb-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="960eb-114">Toto dodatečné zpracování může bránit výkonu.</span><span class="sxs-lookup"><span data-stu-id="960eb-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="960eb-115">Pokud znáte informace o primárním klíči v době návrhu, doporučujeme explicitně zadat sloupec nebo sloupce primárního klíče, abyste dosáhli optimálního výkonu.</span><span class="sxs-lookup"><span data-stu-id="960eb-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="960eb-116">Informace o explicitním nastavení informací o primárním klíči pro tabulku najdete v tématu [Definování primárních klíčů](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="960eb-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="960eb-117">Následující příklad kódu ukazuje, jak přidat informace o schématu do **datové sady** pomocí **FillSchema**.</span><span class="sxs-lookup"><span data-stu-id="960eb-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 <span data-ttu-id="960eb-118">Následující příklad kódu ukazuje, jak přidat informace o schématu do **datové sady** pomocí vlastnosti **MissingSchemaAction. AddWithKey** metody **Fill** .</span><span class="sxs-lookup"><span data-stu-id="960eb-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="960eb-119">Zpracování více sad výsledků</span><span class="sxs-lookup"><span data-stu-id="960eb-119">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="960eb-120">Pokud modul **DataAdapter** narazí na více sad výsledků vrácených z vlastnosti **SelectCommand**, vytvoří v **datové sadě**více tabulek.</span><span class="sxs-lookup"><span data-stu-id="960eb-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="960eb-121">Tabulkám bude předána přírůstkový výchozí název **tabulky** *N*založený na nule, počínaje tabulkou namísto "Table0".</span><span class="sxs-lookup"><span data-stu-id="960eb-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="960eb-122">Pokud je název tabulky předán jako argument pro metodu **FillSchema** , tabulky budou předány s nulovým přírůstkovým názvem **TableName** *N*, počínaje hodnotou **TableName** namísto "TableName0".</span><span class="sxs-lookup"><span data-stu-id="960eb-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="960eb-123">Pokud je metoda **FillSchema** objektu **objektu OleDbDataAdapter** volána pro příkaz, který vrací více sad výsledků, vrátí se pouze informace o schématu z první sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="960eb-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="960eb-124">Při vracení informací o schématu pro více sad výsledků pomocí **objektu OleDbDataAdapter**se doporučuje zadat **MissingSchemaAction** **AddWithKey** a získat informace o schématu při volání **výplně** . Metoda.</span><span class="sxs-lookup"><span data-stu-id="960eb-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="960eb-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="960eb-125">See also</span></span>

- [<span data-ttu-id="960eb-126">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="960eb-126">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="960eb-127">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="960eb-127">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="960eb-128">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="960eb-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="960eb-129">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="960eb-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
