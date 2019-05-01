---
title: Přidání datových relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 9cefc97e571f315a6a644e0a058d4283168ecb9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034508"
---
# <a name="adding-datarelations"></a><span data-ttu-id="0cce6-102">Přidání datových relací</span><span class="sxs-lookup"><span data-stu-id="0cce6-102">Adding DataRelations</span></span>
<span data-ttu-id="0cce6-103">V <xref:System.Data.DataSet> s několika <xref:System.Data.DataTable> objekty, můžete použít <xref:System.Data.DataRelation> objekty k jedné tabulky do druhé, procházení tabulky a vrátí podřízeného nebo nadřazeného řádky ze související tabulky.</span><span class="sxs-lookup"><span data-stu-id="0cce6-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="0cce6-104">Argumenty potřebné k vytvoření **DataRelation** jsou název **DataRelation** vytváří a pole jednoho nebo víc <xref:System.Data.DataColumn> odkazy na sloupce, které slouží jako nadřazené a podřízené sloupce v relaci.</span><span class="sxs-lookup"><span data-stu-id="0cce6-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="0cce6-105">Po vytvoření **DataRelation**, slouží k navigaci mezi tabulkami a k načítání hodnot.</span><span class="sxs-lookup"><span data-stu-id="0cce6-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="0cce6-106">Přidávání **DataRelation** k <xref:System.Data.DataSet> přidá ve výchozím nastavení, <xref:System.Data.UniqueConstraint> do nadřazené tabulky a <xref:System.Data.ForeignKeyConstraint> podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="0cce6-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="0cce6-107">Další informace o těchto výchozích omezeních najdete v tématu [omezení datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="0cce6-107">For more information about these default constraints, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="0cce6-108">Následující příklad kódu vytvoří **DataRelation** pomocí dvou <xref:System.Data.DataTable> objekty v <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="0cce6-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="0cce6-109">Každý <xref:System.Data.DataTable> obsahuje sloupec s názvem **CustID**, který slouží jako propojení mezi těmito dvěma <xref:System.Data.DataTable> objekty.</span><span class="sxs-lookup"><span data-stu-id="0cce6-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="0cce6-110">Příklad přidá jeden **DataRelation** k **vztahy** kolekce <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="0cce6-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="0cce6-111">Určuje název prvního argumentu v příkladu **DataRelation** vytváří.</span><span class="sxs-lookup"><span data-stu-id="0cce6-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="0cce6-112">Druhý argument nastaví nadřazeného **DataColumn** a třetí argument nastaví podřízené **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="0cce6-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
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
  
 <span data-ttu-id="0cce6-113">A **DataRelation** má také **vnořené** vlastnost, která pokud je nastavena na **true**, způsobí, že řádky z podřízených tabulka, která má být vnořen v rámci řádku přidružené z nadřazené tabulky Při zápisu jako elementů XML pomocí <xref:System.Data.DataSet.WriteXml%2A> .</span><span class="sxs-lookup"><span data-stu-id="0cce6-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="0cce6-114">Další informace najdete v tématu [použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="0cce6-114">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cce6-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0cce6-115">See also</span></span>

- [<span data-ttu-id="0cce6-116">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="0cce6-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="0cce6-117">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="0cce6-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
