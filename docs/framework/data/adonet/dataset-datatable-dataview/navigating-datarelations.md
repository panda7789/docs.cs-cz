---
title: Navigace v datových relacích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 1819d468d12c03ce0c4faac11f4b20b8fe0f9c33
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482003"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="b1a11-102">Navigace v datových relacích</span><span class="sxs-lookup"><span data-stu-id="b1a11-102">Navigating DataRelations</span></span>
<span data-ttu-id="b1a11-103">Jednou z primárních funkcí <xref:System.Data.DataRelation> je umožnit navigace z jednoho <xref:System.Data.DataTable> do jiného v rámci <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b1a11-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b1a11-104">To umožňuje načíst všechny související <xref:System.Data.DataRow> objektů v jednom **DataTable** při jediném **DataRow** z se souvisejícím **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="b1a11-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="b1a11-105">Například po vytvoření **DataRelation** mezi tabulku zákazníků a tabulku objednávek, můžete načíst všechny objednávky řádky pro konkrétní zákazníky řádku pomocí **GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="b1a11-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="b1a11-106">Následující příklad kódu vytvoří **DataRelation** mezi **zákazníkům** tabulky a **objednávky** tabulku **datovou sadu** a vrátí všechny objednávky pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="b1a11-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="b1a11-107">Následující příklad je založen na předchozím příkladu společně týkající se čtyřmi tabulkami a procházení těchto relací.</span><span class="sxs-lookup"><span data-stu-id="b1a11-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="b1a11-108">Stejně jako v předchozím příkladu **CustomerID** se vztahuje **zákazníkům** tabulky **objednávky** tabulky.</span><span class="sxs-lookup"><span data-stu-id="b1a11-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="b1a11-109">Pro každého zákazníka v **zákazníkům** všechny podřízené řádky v tabulky **objednávky** tabulky jsou určeny, aby mohla vrátit číslo objednávky určitého zákazníka má a jejich **OrderID** hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b1a11-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="b1a11-110">Rozšířené příkladu také vrátí hodnoty z **OrderDetails** a **produkty** tabulky.</span><span class="sxs-lookup"><span data-stu-id="b1a11-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="b1a11-111">**Objednávky** tabulka má vztah k **OrderDetails** tabulky pomocí **OrderID** určit pro jednotlivé objednávky zákazníka, jaké produktů a množství byly seřazeny.</span><span class="sxs-lookup"><span data-stu-id="b1a11-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="b1a11-112">Protože **OrderDetails** tabulka obsahuje pouze **ProductID** seřazený produktu **OrderDetails** souvisí s **produkty** pomocí **ProductID** cílem vrátit **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="b1a11-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="b1a11-113">V této relaci **produkty** je nadřazená tabulka a **OrderDetails** je podřízená tabulka.</span><span class="sxs-lookup"><span data-stu-id="b1a11-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="b1a11-114">V důsledku toho při iterace **OrderDetails** tabulky, **GetParentRow** je volána k získání související **ProductName** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b1a11-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="b1a11-115">Všimněte si, že **DataRelation** se vytvoří pro **zákazníkům** a **objednávky** tabulky, není zadána žádná hodnota pro **createConstraints**příznak (výchozí hodnota je **true**).</span><span class="sxs-lookup"><span data-stu-id="b1a11-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="b1a11-116">Předpokladem je, že všechny řádky v tabulce **objednávky** tabulka obsahovat **CustomerID** hodnotu, která existuje v nadřazeném prvku **zákazníkům** tabulky.</span><span class="sxs-lookup"><span data-stu-id="b1a11-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="b1a11-117">Pokud **CustomerID** existuje v **objednávky** tabulku, která neexistuje v **zákazníkům** tabulky, <xref:System.Data.ForeignKeyConstraint> způsobí vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="b1a11-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="b1a11-118">Pokud podřízený sloupec může obsahovat hodnoty, které nebude obsahovat nadřazený sloupec, nastavit **createConstraints** příznak **false** při přidávání **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="b1a11-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="b1a11-119">V tomto příkladu **createConstraints** příznak je nastaven na **false** pro **DataRelation** mezi **objednávky** tabulky a  **OrderDetails** tabulky.</span><span class="sxs-lookup"><span data-stu-id="b1a11-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="b1a11-120">To umožňuje aplikaci vrátí všechny záznamy z **OrderDetails** tabulky a pouze podmnožinu záznamů z **objednávky** tabulky bez generování událostí výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="b1a11-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="b1a11-121">Rozšířené ukázka generuje výstup ve formátu.</span><span class="sxs-lookup"><span data-stu-id="b1a11-121">The expanded sample generates output in the following format.</span></span>  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 <span data-ttu-id="b1a11-122">Následující příklad kódu je rozbalený ukázka kde hodnoty z **OrderDetails** a **produkty** tabulky jsou vráceny pomocí pouze podmnožinu záznamů v **objednávky**tabulky se vrací.</span><span class="sxs-lookup"><span data-stu-id="b1a11-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b1a11-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1a11-123">See Also</span></span>  
 [<span data-ttu-id="b1a11-124">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="b1a11-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="b1a11-125">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b1a11-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
