---
title: "Odvození relace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 79f79c1dbc74b98cff10de81c2bd7bd32d7d286b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-relationships"></a><span data-ttu-id="afee4-102">Odvození relace</span><span class="sxs-lookup"><span data-stu-id="afee4-102">Inferring Relationships</span></span>
<span data-ttu-id="afee4-103">Pokud má element, který je používán jako tabulku podřízený element, který je také odvodit jako tabulku, <xref:System.Data.DataRelation> se vytvoří mezi dvěma tabulkami.</span><span class="sxs-lookup"><span data-stu-id="afee4-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="afee4-104">Nový sloupec s názvem **ParentTableName_Id** bude přidán do tabulky vytvořili pro nadřazený element i v tabulce pro podřízený element vytvořit.</span><span class="sxs-lookup"><span data-stu-id="afee4-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="afee4-105">**ColumnMapping** vlastnost v tomto sloupci identity bude nastavena pro **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="afee4-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="afee4-106">Sloupec bude automaticky rostoucí primární klíč pro nadřazenou tabulkou a bude použit pro **DataRelation** mezi dvěma tabulkami.</span><span class="sxs-lookup"><span data-stu-id="afee4-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="afee4-107">Datový typ sloupce identity přidané bude **System.Int32**, na rozdíl od všech ostatních odvozené sloupce datový typ, který je **System.String**.</span><span class="sxs-lookup"><span data-stu-id="afee4-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="afee4-108">A <xref:System.Data.ForeignKeyConstraint> s **DeletRule** = **Cascade** bude vytvořen také pomocí nového sloupce v nadřazené a podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="afee4-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="afee4-109">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="afee4-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="afee4-110">Proces odvození vytvoří dvě tabulky: **Element1** a **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="afee4-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="afee4-111">**Element1** tabulka bude mít dva sloupce: **Element1_Id** a **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="afee4-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="afee4-112">**ColumnMapping** vlastnost **Element1_Id** sloupec bude nastavena pro **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="afee4-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="afee4-113">**ColumnMapping** vlastnost **ChildElement2** sloupec bude nastavena pro **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="afee4-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="afee4-114">**Element1_Id** sloupec bude nastaven jako primární klíč **Element1** tabulky.</span><span class="sxs-lookup"><span data-stu-id="afee4-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="afee4-115">**ChildElement1** tabulka bude mít tři sloupce: **attr1**, **attr2** a **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="afee4-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="afee4-116">**ColumnMapping** vlastnost **attr1** a **attr2** sloupců bude nastavena pro **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="afee4-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="afee4-117">**ColumnMapping** vlastnost **Element1_Id** sloupec bude nastavena pro **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="afee4-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="afee4-118">A **DataRelation** a **vlastnosti ForeignKeyConstraint** se vytvoří pomocí **Element1_Id** sloupců z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="afee4-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="afee4-119">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="afee4-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="afee4-120">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="afee4-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="afee4-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="afee4-121">Element1_Id</span></span>|<span data-ttu-id="afee4-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="afee4-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="afee4-123">0</span><span class="sxs-lookup"><span data-stu-id="afee4-123">0</span></span>|<span data-ttu-id="afee4-124">Text2</span><span class="sxs-lookup"><span data-stu-id="afee4-124">Text2</span></span>|  
  
 <span data-ttu-id="afee4-125">**Tabulka:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="afee4-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="afee4-126">attr1</span><span class="sxs-lookup"><span data-stu-id="afee4-126">attr1</span></span>|<span data-ttu-id="afee4-127">attr2</span><span class="sxs-lookup"><span data-stu-id="afee4-127">attr2</span></span>|<span data-ttu-id="afee4-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="afee4-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="afee4-129">value1</span><span class="sxs-lookup"><span data-stu-id="afee4-129">value1</span></span>|<span data-ttu-id="afee4-130">value2</span><span class="sxs-lookup"><span data-stu-id="afee4-130">value2</span></span>|<span data-ttu-id="afee4-131">0</span><span class="sxs-lookup"><span data-stu-id="afee4-131">0</span></span>|  
  
 <span data-ttu-id="afee4-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="afee4-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="afee4-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="afee4-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="afee4-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="afee4-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="afee4-135">**Tabulka:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="afee4-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="afee4-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="afee4-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="afee4-137">**Vnořené:** True</span><span class="sxs-lookup"><span data-stu-id="afee4-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="afee4-138">**Objekt ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="afee4-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="afee4-139">**Sloupec:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="afee4-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="afee4-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="afee4-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="afee4-141">**Tabulka:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="afee4-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="afee4-142">**DeletRule:** Cascade</span><span class="sxs-lookup"><span data-stu-id="afee4-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="afee4-143">**AcceptRejectRule:** None</span><span class="sxs-lookup"><span data-stu-id="afee4-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afee4-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="afee4-144">See Also</span></span>  
 [<span data-ttu-id="afee4-145">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="afee4-145">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="afee4-146">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="afee4-146">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="afee4-147">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="afee4-147">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="afee4-148">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="afee4-148">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [<span data-ttu-id="afee4-149">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="afee4-149">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="afee4-150">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="afee4-150">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="afee4-151">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="afee4-151">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
