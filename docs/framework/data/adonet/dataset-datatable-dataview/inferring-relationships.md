---
title: Odvozování relací
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 4c9c13453e4a830fcda337e8163649ba6491a995
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785373"
---
# <a name="inferring-relationships"></a><span data-ttu-id="28e1b-102">Odvozování relací</span><span class="sxs-lookup"><span data-stu-id="28e1b-102">Inferring Relationships</span></span>
<span data-ttu-id="28e1b-103">Pokud prvek, který je odvozen jako tabulka, má podřízený element, který je také odvozen jako tabulka, <xref:System.Data.DataRelation> vytvoří se mezi těmito dvěma tabulkami.</span><span class="sxs-lookup"><span data-stu-id="28e1b-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="28e1b-104">Nový sloupec s názvem **ParentTableName_Id** se přidá do tabulky vytvořené pro nadřazený element a vytvoří se tabulka vytvořená pro podřízený element.</span><span class="sxs-lookup"><span data-stu-id="28e1b-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="28e1b-105">Vlastnost **ColumnMapping** tohoto sloupce identity bude nastavena na **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="28e1b-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="28e1b-106">Sloupec bude automaticky zvyšovat primární klíč pro nadřazenou tabulku a bude použit pro **relaci DataRelation** mezi oběma tabulkami.</span><span class="sxs-lookup"><span data-stu-id="28e1b-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="28e1b-107">Datový typ sloupce přidáno identity bude **System. Int32**, na rozdíl od datového typu všech ostatních odvozených sloupců, což je **System. String**.</span><span class="sxs-lookup"><span data-stu-id="28e1b-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="28e1b-108">A <xref:System.Data.ForeignKeyConstraint> s **DeleteRule** = **Cascade** se vytvoří také pomocí nového sloupce v nadřazené i podřízené tabulce.</span><span class="sxs-lookup"><span data-stu-id="28e1b-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="28e1b-109">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="28e1b-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="28e1b-110">Proces odvození vytvoří dvě tabulky: **Element1** a **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="28e1b-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="28e1b-111">Tabulka **Element1** bude mít dva sloupce: **Element1_Id** a **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="28e1b-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="28e1b-112">Vlastnost **ColumnMapping** sloupce **Element1_Id** bude nastavena na **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="28e1b-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="28e1b-113">Vlastnost **ColumnMapping** sloupce **ChildElement2** bude nastavena na **MappingType. element**.</span><span class="sxs-lookup"><span data-stu-id="28e1b-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="28e1b-114">Sloupec **Element1_Id** se nastaví jako primární klíč tabulky **Element1** .</span><span class="sxs-lookup"><span data-stu-id="28e1b-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="28e1b-115">Tabulka **ChildElement1** bude mít tři sloupce: **attr1**, **attr2** a **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="28e1b-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="28e1b-116">Vlastnost **ColumnMapping** pro sloupce **attr1** a **attr2** se nastaví na **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="28e1b-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="28e1b-117">Vlastnost **ColumnMapping** sloupce **Element1_Id** bude nastavena na **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="28e1b-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="28e1b-118">**DataRelation** a **Objekt ForeignKeyConstraint** se vytvoří pomocí sloupců **Element1_Id** z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="28e1b-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="28e1b-119">**Integrován** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="28e1b-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="28e1b-120">**Stolní** Element1</span><span class="sxs-lookup"><span data-stu-id="28e1b-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="28e1b-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="28e1b-121">Element1_Id</span></span>|<span data-ttu-id="28e1b-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="28e1b-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="28e1b-123">0</span><span class="sxs-lookup"><span data-stu-id="28e1b-123">0</span></span>|<span data-ttu-id="28e1b-124">Text2</span><span class="sxs-lookup"><span data-stu-id="28e1b-124">Text2</span></span>|  
  
 <span data-ttu-id="28e1b-125">**Stolní** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="28e1b-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="28e1b-126">attr1</span><span class="sxs-lookup"><span data-stu-id="28e1b-126">attr1</span></span>|<span data-ttu-id="28e1b-127">attr2</span><span class="sxs-lookup"><span data-stu-id="28e1b-127">attr2</span></span>|<span data-ttu-id="28e1b-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="28e1b-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="28e1b-129">Hodnota1</span><span class="sxs-lookup"><span data-stu-id="28e1b-129">value1</span></span>|<span data-ttu-id="28e1b-130">Argument</span><span class="sxs-lookup"><span data-stu-id="28e1b-130">value2</span></span>|<span data-ttu-id="28e1b-131">0</span><span class="sxs-lookup"><span data-stu-id="28e1b-131">0</span></span>|  
  
 <span data-ttu-id="28e1b-132">**DataRelation** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="28e1b-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="28e1b-133">**Nadřazená tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="28e1b-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="28e1b-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="28e1b-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="28e1b-135">**Podřízená tabulka:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="28e1b-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="28e1b-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="28e1b-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="28e1b-137">**Vnořen** Pravda</span><span class="sxs-lookup"><span data-stu-id="28e1b-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="28e1b-138">**Objekt ForeignKeyConstraint** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="28e1b-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="28e1b-139">**Kolo** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="28e1b-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="28e1b-140">**Nadřazená tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="28e1b-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="28e1b-141">**Podřízená tabulka:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="28e1b-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="28e1b-142">**DeleteRule:** Nášejí</span><span class="sxs-lookup"><span data-stu-id="28e1b-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="28e1b-143">**AcceptRejectRule:** Žádné</span><span class="sxs-lookup"><span data-stu-id="28e1b-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e1b-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28e1b-144">See also</span></span>

- [<span data-ttu-id="28e1b-145">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="28e1b-145">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="28e1b-146">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="28e1b-146">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="28e1b-147">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="28e1b-147">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="28e1b-148">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="28e1b-148">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="28e1b-149">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="28e1b-149">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="28e1b-150">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="28e1b-150">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="28e1b-151">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="28e1b-151">ADO.NET Overview</span></span>](../ado-net-overview.md)
