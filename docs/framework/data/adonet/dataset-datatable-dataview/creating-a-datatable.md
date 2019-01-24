---
title: Vytvoření datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: f40a04156bee5ceee7490cf7bd941dc11a99b880
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608309"
---
# <a name="creating-a-datatable"></a><span data-ttu-id="ebf10-102">Vytvoření datové tabulky</span><span class="sxs-lookup"><span data-stu-id="ebf10-102">Creating a DataTable</span></span>
<span data-ttu-id="ebf10-103">A <xref:System.Data.DataTable>, která představuje jednu tabulku relační data v paměti, lze vytvořit a používat samostatně nebo mohou využívat jiné objekty rozhraní .NET Framework nejčastěji jako člen <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ebf10-103">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="ebf10-104">Můžete vytvořit **DataTable** s použitím příslušná **DataTable** konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ebf10-104">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="ebf10-105">Můžete přidat tak **datovou sadu** pomocí **přidat** metoda a přidejte ji tak **DataTable** objektu **tabulky** kolekce.</span><span class="sxs-lookup"><span data-stu-id="ebf10-105">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="ebf10-106">Můžete také vytvořit **DataTable** objekty v rámci **datovou sadu** pomocí **vyplnit** nebo **FillSchema** metody  **Vlastnost DataAdapter** objektu, nebo z předdefinovaných nebo odvozené XML schématu pomocí **ReadXml**, **ReadXmlSchema**, nebo **InferXmlSchema** metody **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="ebf10-106">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="ebf10-107">Všimněte si, že po přidání **DataTable** jako člen **tabulky** kolekce jednoho **datovou sadu**, ho nemůžete přidat do kolekce tabulek jiných **Datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="ebf10-107">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="ebf10-108">Při prvním vytvoření **DataTable**, nemá schématu (to znamená, že struktura).</span><span class="sxs-lookup"><span data-stu-id="ebf10-108">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="ebf10-109">Definovat schéma tabulky, můžete vytvořit a přidat <xref:System.Data.DataColumn> objektů **sloupce** kolekce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="ebf10-109">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="ebf10-110">Můžete také definujte sloupec primárního klíče pro tabulku a vytvoříte a přidáte **omezení** objektů **omezení** kolekce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="ebf10-110">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="ebf10-111">Po definování schématu **DataTable**, řádky dat do tabulky můžete přidat tak, že přidáte **DataRow** objektů **řádky** kolekce tabulky.</span><span class="sxs-lookup"><span data-stu-id="ebf10-111">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="ebf10-112">Není nutné zadat hodnotu <xref:System.Data.DataTable.TableName%2A> vlastnost při vytváření **DataTable**; můžete zadat vlastnost později, nebo můžete nechat prázdné.</span><span class="sxs-lookup"><span data-stu-id="ebf10-112">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="ebf10-113">Ale při přidání tabulky bez **TableName** hodnota, která se **datovou sadu**, tabulce dostanou přírůstkové výchozí název tabulky*N*počínaje "Table" pro Table0.</span><span class="sxs-lookup"><span data-stu-id="ebf10-113">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebf10-114">Doporučujeme, abyste "tabulky*N*" zásady vytváření názvů, když zadáte **TableName** hodnotu, protože název zadáte dojít ke konfliktu s existujícím názvem výchozí tabulky v **datové sady** .</span><span class="sxs-lookup"><span data-stu-id="ebf10-114">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="ebf10-115">Pokud zadaný název již existuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ebf10-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="ebf10-116">Následující příklad vytvoří instanci **DataTable** objektu a přiřazuje mu název "Zákazníků."</span><span class="sxs-lookup"><span data-stu-id="ebf10-116">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="ebf10-117">Následující příklad vytvoří instanci **DataTable** tak, že ji přidáte **tabulky** kolekce **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="ebf10-117">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebf10-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebf10-118">See also</span></span>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [<span data-ttu-id="ebf10-119">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="ebf10-119">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="ebf10-120">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="ebf10-120">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="ebf10-121">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="ebf10-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="ebf10-122">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="ebf10-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="ebf10-123">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ebf10-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
