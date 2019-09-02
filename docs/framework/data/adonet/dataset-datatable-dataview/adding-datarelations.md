---
title: Přidání datových relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: fde1e2ace09e31234d199876ae7f063e01e7a7e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203977"
---
# <a name="adding-datarelations"></a><span data-ttu-id="4e7e5-102">Přidání datových relací</span><span class="sxs-lookup"><span data-stu-id="4e7e5-102">Adding DataRelations</span></span>
<span data-ttu-id="4e7e5-103">V případě <xref:System.Data.DataSet> více <xref:System.Data.DataTable> objektů lze pomocí <xref:System.Data.DataRelation> objektů propojit jednu tabulku s druhou, procházet tabulky a vracet podřízené nebo nadřazené řádky ze související tabulky.</span><span class="sxs-lookup"><span data-stu-id="4e7e5-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="4e7e5-104">Argumenty vyžadované k vytvoření **relace DataRelation** jsou název pro vytvoření datarelationship a pole jednoho nebo více <xref:System.Data.DataColumn> odkazů na sloupce, které slouží jako nadřazené a podřízené sloupce v relaci.</span><span class="sxs-lookup"><span data-stu-id="4e7e5-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="4e7e5-105">Po vytvoření **relace DataRelation**ji můžete použít k navigaci mezi tabulkami a k načtení hodnot.</span><span class="sxs-lookup"><span data-stu-id="4e7e5-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="4e7e5-106">Přidání objektu **DataRelation** do <xref:System.Data.DataSet> přidat, <xref:System.Data.UniqueConstraint> ve výchozím nastavení do nadřazené tabulky a <xref:System.Data.ForeignKeyConstraint> do podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="4e7e5-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="4e7e5-107">Další informace o těchto výchozích omezeních naleznete v tématu [omezení DataTable](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="4e7e5-107">For more information about these default constraints, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="4e7e5-108">Následující příklad kódu vytvoří datovou **relaci** pomocí dvou <xref:System.Data.DataTable> objektů v <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4e7e5-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="4e7e5-109">Každý <xref:System.Data.DataTable> obsahuje sloupec s názvem **custid**, který slouží jako propojení mezi dvěma <xref:System.Data.DataTable> objekty.</span><span class="sxs-lookup"><span data-stu-id="4e7e5-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="4e7e5-110">Tento příklad přidá jeden objekt **DataRelation** do kolekce **Relations** v <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4e7e5-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="4e7e5-111">První argument v příkladu určuje název datarelationu, který se vytváří.</span><span class="sxs-lookup"><span data-stu-id="4e7e5-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="4e7e5-112">Druhý argument nastaví nadřazený datový sloupec a třetí argument nastaví podřízený **sloupec DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="4e7e5-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 <span data-ttu-id="4e7e5-113">Objekt **DataRelation** má také vnořenou vlastnost, která při nastavení na **hodnotu true**způsobí, že řádky z podřízené tabulky budou vnořeny do přidruženého řádku z nadřazené tabulky při zápisu jako XML prvky pomocí <xref:System.Data.DataSet.WriteXml%2A> .</span><span class="sxs-lookup"><span data-stu-id="4e7e5-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="4e7e5-114">Další informace naleznete v tématu [using XML in a DataSet](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="4e7e5-114">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7e5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e7e5-115">See also</span></span>

- [<span data-ttu-id="4e7e5-116">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="4e7e5-116">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="4e7e5-117">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="4e7e5-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
