---
title: Odvozování relací
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 7dc3fb0c6098d636e640aaf52b72a404c1486492
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492993"
---
# <a name="inferring-relationships"></a><span data-ttu-id="eabea-102">Odvozování relací</span><span class="sxs-lookup"><span data-stu-id="eabea-102">Inferring Relationships</span></span>
<span data-ttu-id="eabea-103">Pokud element, který je odvozený jako tabulka má podřízený element, který je také odvodit jako tabulku <xref:System.Data.DataRelation> mezi dvěma tabulkami se nevytvoří.</span><span class="sxs-lookup"><span data-stu-id="eabea-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="eabea-104">Nový sloupec s názvem **ParentTableName_Id** se přidají do tabulky vytvořené pro nadřazený element a tabulku vytvořenou pro podřízený element.</span><span class="sxs-lookup"><span data-stu-id="eabea-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="eabea-105">**ColumnMapping** vlastnost tohoto sloupce identity bude nastavena na **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="eabea-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="eabea-106">Sloupec bude automatické zvyšování hodnoty primárního klíče pro nadřazené tabulky a se použije pro **DataRelation** mezi dvěma tabulkami.</span><span class="sxs-lookup"><span data-stu-id="eabea-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="eabea-107">Datový typ sloupce identity přidání bude **System.Int32**, na rozdíl od datového typu všechny ostatní odvozené sloupců, což je **System.String**.</span><span class="sxs-lookup"><span data-stu-id="eabea-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="eabea-108">A <xref:System.Data.ForeignKeyConstraint> s **DeletRule** = **Cascade** také vytvoří nový sloupec v nadřazené a podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="eabea-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="eabea-109">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="eabea-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="eabea-110">Procesu odvození vytvoří dvě tabulky: **Element1** a **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="eabea-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="eabea-111">**Element1** tabulka bude mít dva sloupce: **Element1_Id** a **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="eabea-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="eabea-112">**ColumnMapping** vlastnost **Element1_Id** sloupec bude nastaven na **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="eabea-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="eabea-113">**ColumnMapping** vlastnost **ChildElement2** sloupec bude nastaven na **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="eabea-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="eabea-114">**Element1_Id** sloupec bude nastaven jako primární klíč **Element1** tabulky.</span><span class="sxs-lookup"><span data-stu-id="eabea-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="eabea-115">**ChildElement1** tabulka bude mít tři sloupce: **attr1**, **attr2** a **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="eabea-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="eabea-116">**ColumnMapping** vlastnost **attr1** a **attr2** sloupce se nastaví na **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="eabea-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="eabea-117">**ColumnMapping** vlastnost **Element1_Id** sloupec bude nastaven na **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="eabea-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="eabea-118">A **DataRelation** a **Objekt ForeignKeyConstraint** se vytvoří pomocí **Element1_Id** sloupců z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="eabea-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="eabea-119">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="eabea-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="eabea-120">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="eabea-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="eabea-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="eabea-121">Element1_Id</span></span>|<span data-ttu-id="eabea-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="eabea-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="eabea-123">0</span><span class="sxs-lookup"><span data-stu-id="eabea-123">0</span></span>|<span data-ttu-id="eabea-124">Text2</span><span class="sxs-lookup"><span data-stu-id="eabea-124">Text2</span></span>|  
  
 <span data-ttu-id="eabea-125">**Tabulka:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="eabea-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="eabea-126">attr1</span><span class="sxs-lookup"><span data-stu-id="eabea-126">attr1</span></span>|<span data-ttu-id="eabea-127">attr2</span><span class="sxs-lookup"><span data-stu-id="eabea-127">attr2</span></span>|<span data-ttu-id="eabea-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="eabea-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="eabea-129">Hodnota1</span><span class="sxs-lookup"><span data-stu-id="eabea-129">value1</span></span>|<span data-ttu-id="eabea-130">Hodnota2</span><span class="sxs-lookup"><span data-stu-id="eabea-130">value2</span></span>|<span data-ttu-id="eabea-131">0</span><span class="sxs-lookup"><span data-stu-id="eabea-131">0</span></span>|  
  
 <span data-ttu-id="eabea-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="eabea-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="eabea-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="eabea-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="eabea-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="eabea-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="eabea-135">**Tabulka:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="eabea-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="eabea-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="eabea-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="eabea-137">**Vnořené:** True</span><span class="sxs-lookup"><span data-stu-id="eabea-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="eabea-138">**Objekt ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="eabea-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="eabea-139">**Sloupec:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="eabea-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="eabea-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="eabea-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="eabea-141">**Tabulka:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="eabea-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="eabea-142">**DeletRule:** Cascade</span><span class="sxs-lookup"><span data-stu-id="eabea-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="eabea-143">**AcceptRejectRule:** None</span><span class="sxs-lookup"><span data-stu-id="eabea-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eabea-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="eabea-144">See Also</span></span>  
 [<span data-ttu-id="eabea-145">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="eabea-145">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="eabea-146">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="eabea-146">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="eabea-147">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="eabea-147">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="eabea-148">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="eabea-148">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [<span data-ttu-id="eabea-149">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="eabea-149">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="eabea-150">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="eabea-150">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="eabea-151">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="eabea-151">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
