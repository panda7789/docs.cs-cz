---
title: Vytvoření datové tabulky
description: Naučte se vytvářet DataTable v ADO.NET, která představuje jednu tabulku relačních dat v paměti pro použití nezávisle nebo jinými .NET Framework objekty.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 335137eeef02e590539c6d83e46cb39901a1e03f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286918"
---
# <a name="creating-a-datatable"></a><span data-ttu-id="7a453-103">Vytvoření datové tabulky</span><span class="sxs-lookup"><span data-stu-id="7a453-103">Creating a DataTable</span></span>
<span data-ttu-id="7a453-104"><xref:System.Data.DataTable>, Který představuje jednu tabulku relačních dat v paměti, lze vytvořit a použít nezávisle, nebo mohou být použity jinými .NET Framework objekty, nejčastěji jako člen <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="7a453-104">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="7a453-105">Objekt **DataTable** lze vytvořit pomocí příslušného konstruktoru **DataTable** .</span><span class="sxs-lookup"><span data-stu-id="7a453-105">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="7a453-106">Můžete ji přidat do **datové sady** pomocí metody **Add** pro její přidání do kolekce **tabulek** objektu **DataTable** .</span><span class="sxs-lookup"><span data-stu-id="7a453-106">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="7a453-107">Můžete také vytvořit objekty **DataTable** v rámci **datové sady** pomocí metod **Fill** nebo **FillSchema** objektu **DataAdapter** nebo z předdefinovaného nebo odvozeného schématu XML pomocí metod **ReadXml**, **ReadXmlSchema**a **InferXmlSchema** objektu **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7a453-107">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="7a453-108">Všimněte si, že poté, co jste přidali **DataTable** jako člena kolekce **Tables** jedné **datové sady**, nelze ji přidat do kolekce tabulek žádné jiné **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="7a453-108">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="7a453-109">Při prvním vytvoření **objektu DataTable**nemá schéma (to znamená struktury).</span><span class="sxs-lookup"><span data-stu-id="7a453-109">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="7a453-110">Chcete-li definovat schéma tabulky, je nutné vytvořit a přidat <xref:System.Data.DataColumn> objekty do kolekce **Columns** v tabulce.</span><span class="sxs-lookup"><span data-stu-id="7a453-110">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="7a453-111">Můžete také definovat sloupec primárního klíče pro tabulku a vytvořit a přidat objekty **omezení** do kolekce **omezení** v tabulce.</span><span class="sxs-lookup"><span data-stu-id="7a453-111">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="7a453-112">Po definování schématu pro **objekt DataTable**můžete do tabulky přidat řádky dat přidáním objektů **DataRow** do kolekce **řádků** tabulky.</span><span class="sxs-lookup"><span data-stu-id="7a453-112">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="7a453-113"><xref:System.Data.DataTable.TableName%2A>Při vytváření **objektu DataTable**není nutné zadávat hodnotu vlastnosti. vlastnost lze zadat v jinou dobu nebo ji můžete ponechat prázdnou.</span><span class="sxs-lookup"><span data-stu-id="7a453-113">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="7a453-114">Pokud však přidáte tabulku bez hodnoty **TableName** do **datové sady**, bude se tabulce předávat přírůstkový výchozí název tabulky*N*, počínaje "Table" pro TABLE0.</span><span class="sxs-lookup"><span data-stu-id="7a453-114">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a453-115">Doporučujeme vyhnout se konvenci pojmenování tabulky*N*při zadání hodnoty **TableName** , protože název, který zadáte, může být v konfliktu s existujícím názvem výchozí tabulky v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="7a453-115">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="7a453-116">Pokud zadaný název již existuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="7a453-116">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="7a453-117">Následující příklad vytvoří instanci objektu **DataTable** a přiřadí mu název "Customers".</span><span class="sxs-lookup"><span data-stu-id="7a453-117">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="7a453-118">Následující příklad vytvoří instanci **objektu DataTable** přidáním do kolekce **Tables** **objektu DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7a453-118">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a453-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a453-119">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [<span data-ttu-id="7a453-120">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="7a453-120">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="7a453-121">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="7a453-121">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="7a453-122">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="7a453-122">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="7a453-123">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="7a453-123">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="7a453-124">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7a453-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
