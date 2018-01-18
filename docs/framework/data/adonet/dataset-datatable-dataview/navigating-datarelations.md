---
title: Navigace DataRelations
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 84272a24dde909205d01f4ced5a57450c5fdbd7f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="navigating-datarelations"></a><span data-ttu-id="ede01-102">Navigace DataRelations</span><span class="sxs-lookup"><span data-stu-id="ede01-102">Navigating DataRelations</span></span>
<span data-ttu-id="ede01-103">Jeden z primární funkce <xref:System.Data.DataRelation> je umožnit navigační z jednoho <xref:System.Data.DataTable> do jiné v rámci <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ede01-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ede01-104">To umožňuje načíst všechny související <xref:System.Data.DataRow> objektů v jednom **DataTable** li zadán jeden **DataRow** z související **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="ede01-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="ede01-105">Například po navázání **DataRelation** mezi tabulku zákazníků a tabulku objednávky, můžete načíst všechny řádky pořadí pro konkrétního zákazníka řádek pomocí **Metoda GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="ede01-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="ede01-106">Následující příklad kódu vytvoří **DataRelation** mezi **zákazníci** tabulky a **objednávky** tabulky **datovou sadu** a vrátí všechny objednávky pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="ede01-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="ede01-107">Další příklad vychází v předchozím příkladu, týkající se čtyři tabulky dohromady a navigace těchto relací.</span><span class="sxs-lookup"><span data-stu-id="ede01-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="ede01-108">Jako v předchozím příkladu **CustomerID** má vztah **zákazníci** a **objednávky** tabulky.</span><span class="sxs-lookup"><span data-stu-id="ede01-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="ede01-109">Pro každého zákazníka a to v **zákazníci** tabulky, všechny podřízené řádky v **objednávky** určuje tabulky, aby bylo možné vrátit číslo objednávky konkrétní zákazník má a jejich **OrderID** hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ede01-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="ede01-110">Rozšířené příklad také vrací hodnoty z **Rozpis objednávek** a **produkty** tabulky.</span><span class="sxs-lookup"><span data-stu-id="ede01-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="ede01-111">**Objednávky** tabulka souvisí s **Rozpis objednávek** tabulky pomocí **OrderID** k určení, pro každou pořadí zákazníka, jaké produktů a množství byly řazení.</span><span class="sxs-lookup"><span data-stu-id="ede01-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="ede01-112">Protože **Rozpis objednávek** tabulka obsahuje pouze **ProductID** seřazené produktu **Rozpis objednávek** souvisí s **produkty** pomocí **ProductID** cílem vrátit **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="ede01-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="ede01-113">V této relaci **produkty** tabulka je nadřazený a **pořadí podrobnosti** tabulka je podřízeným.</span><span class="sxs-lookup"><span data-stu-id="ede01-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="ede01-114">V důsledku toho, když iterace v rámci **Rozpis objednávek** tabulky, **GetParentRow** nazývá se načíst související **ProductName** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ede01-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="ede01-115">Všimněte si, že pokud **DataRelation** se vytvoří pro **zákazníci** a **objednávky** tabulky, pro není zadaná žádná hodnota **createConstraints**příznak (výchozí hodnota je **true**).</span><span class="sxs-lookup"><span data-stu-id="ede01-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="ede01-116">Toto předpokládá, že všechny řádky v **objednávky** tabulka mít **CustomerID** hodnotu, která existuje v nadřízeném **zákazníci** tabulky.</span><span class="sxs-lookup"><span data-stu-id="ede01-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="ede01-117">Pokud **CustomerID** existuje v **objednávky** tabulku, která neexistuje v **zákazníci** tabulky, <xref:System.Data.ForeignKeyConstraint> způsobí, že vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="ede01-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="ede01-118">Když podřízeného sloupce může obsahovat hodnoty, které nadřazený sloupec neobsahuje, nastavte **createConstraints** příznak, který **false** při přidávání **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="ede01-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="ede01-119">V příkladu **createConstraints** je příznak nastaven na **false** pro **DataRelation** mezi **objednávky** atabulky **Rozpis objednávek** tabulky.</span><span class="sxs-lookup"><span data-stu-id="ede01-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="ede01-120">To umožňuje aplikaci zobrazit všechny záznamy z **Rozpis objednávek** tabulky a pouze podmnožinu záznamů z **objednávky** tabulky bez generování událostí výjimky spuštění.</span><span class="sxs-lookup"><span data-stu-id="ede01-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="ede01-121">Rozšířené ukázka generuje výstupu v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="ede01-121">The expanded sample generates output in the following format.</span></span>  
  
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
  
 <span data-ttu-id="ede01-122">Následující příklad kódu je rozšířená ukázka kde hodnoty z **Rozpis objednávek** a **produkty** tabulky se vrátí se pouze podmnožinu záznamy v **objednávky**tabulky nebyl vrácen.</span><span class="sxs-lookup"><span data-stu-id="ede01-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ede01-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ede01-123">See Also</span></span>  
 [<span data-ttu-id="ede01-124">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="ede01-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="ede01-125">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="ede01-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
