---
title: Navigace v datových relacích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 73523297454be37716acedad13498954ef9a89a0
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040351"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="c1b80-102">Navigace v datových relacích</span><span class="sxs-lookup"><span data-stu-id="c1b80-102">Navigating DataRelations</span></span>
<span data-ttu-id="c1b80-103">Jednou z primárních funkcí <xref:System.Data.DataRelation> je umožnění navigace z jednoho <xref:System.Data.DataTable> do druhé v rámci <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c1b80-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c1b80-104">To umožňuje načíst všechny související <xref:System.Data.DataRow> objekty v jednom **objektu DataTable** , pokud je předána jedna třída **DataRow** ze souvisejícího **objektu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="c1b80-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="c1b80-105">Například po vytvoření **datarelace** mezi tabulkou zákazníků a tabulkou objednávky můžete načíst všechny řádky objednávky pro konkrétní řádek zákazníka pomocí **Metoda GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="c1b80-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="c1b80-106">Následující příklad kódu vytvoří datovou **relaci** mezi tabulkou **Customers** a tabulkou **objednávky** **datové sady** a vrátí všechny objednávky pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="c1b80-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="c1b80-107">Následující příklad sestaví v předchozím příkladu se souvisejícími čtyřmi tabulkami a naviguje se na tyto vztahy.</span><span class="sxs-lookup"><span data-stu-id="c1b80-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="c1b80-108">Jak je uvedeno v předchozím příkladu, pole **KódZákazníka** se týká tabulky **Customers** v tabulce **Orders** .</span><span class="sxs-lookup"><span data-stu-id="c1b80-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="c1b80-109">Pro každého zákazníka v tabulce **Customers (zákazníci** ) se určí všechny podřízené řádky v tabulce **Orders** , aby bylo možné vrátit počet objednávek, které konkrétní zákazník má, a jejich hodnoty **ČísloObjednávky** .</span><span class="sxs-lookup"><span data-stu-id="c1b80-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="c1b80-110">Rozbalený příklad také vrátí hodnoty z tabulek **OrderDetails** a **Products** .</span><span class="sxs-lookup"><span data-stu-id="c1b80-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="c1b80-111">Tabulka **Orders** se vztahuje k tabulce **OrderDetails** s využitím hodnoty **ČísloObjednávky** k určení, jaké produkty a množství byly objednány pro každé pořadí zákazníků.</span><span class="sxs-lookup"><span data-stu-id="c1b80-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="c1b80-112">Protože tabulka **OrderDetails** obsahuje pouze **ProductID** objednaného produktu, **OrderDetails** se vztahuje k **produktům** , které používají **ProductID** za účelem vrácení **NázevVýrobku**.</span><span class="sxs-lookup"><span data-stu-id="c1b80-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="c1b80-113">V této relaci je tabulka **Products** nadřazená a tabulka **Podrobnosti objednávky** je podřízená položka.</span><span class="sxs-lookup"><span data-stu-id="c1b80-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="c1b80-114">Výsledkem je, že při iteraci v tabulce **OrderDetails** se volá **Metoda GetParentRow** , aby se načetla související hodnota **NázevVýrobku** .</span><span class="sxs-lookup"><span data-stu-id="c1b80-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="c1b80-115">Všimněte si, že při vytvoření **Datarelationu** pro tabulky **zákazníci** a **objednávky** není pro příznak **createConstraints** zadána žádná hodnota (výchozí hodnota je **true**).</span><span class="sxs-lookup"><span data-stu-id="c1b80-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="c1b80-116">To předpokládá, že všechny řádky v tabulce **Orders** mají hodnotu **CustomerID** , která existuje v tabulce nadřazených **zákazníků** .</span><span class="sxs-lookup"><span data-stu-id="c1b80-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="c1b80-117">Pokud existuje **KódZákazníka** v tabulce **Orders** , která v tabulce **Customers** neexistuje, <xref:System.Data.ForeignKeyConstraint> způsobí vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="c1b80-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="c1b80-118">Pokud podřízený sloupec může obsahovat hodnoty, které nadřazený sloupec neobsahuje, nastavte příznak **createConstraints** na **hodnotu false** při přidávání objektu **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="c1b80-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="c1b80-119">V příkladu je příznak **createConstraints** nastaven na **hodnotu false** pro **DataRelation** mezi tabulkou **Orders** a tabulkou **OrderDetails** .</span><span class="sxs-lookup"><span data-stu-id="c1b80-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="c1b80-120">To umožňuje aplikaci vracet všechny záznamy z tabulky **OrderDetails** a pouze podmnožinu záznamů z tabulky **Orders** , aniž by generovaly výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="c1b80-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="c1b80-121">Rozbalený vzorek generuje výstup v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="c1b80-121">The expanded sample generates output in the following format.</span></span>  
  
```output  
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
  
 <span data-ttu-id="c1b80-122">Následující příklad kódu je rozbalený vzorek, ve kterém jsou vráceny hodnoty z tabulek **OrderDetails** a **Products** s vrácenou pouze podmnožinou záznamů v tabulce **Orders** .</span><span class="sxs-lookup"><span data-stu-id="c1b80-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c1b80-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1b80-123">See also</span></span>

- [<span data-ttu-id="c1b80-124">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="c1b80-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="c1b80-125">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c1b80-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
