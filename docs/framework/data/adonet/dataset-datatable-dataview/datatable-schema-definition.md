---
title: "Definice schématu DataTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: be5969bf8653512da27785479ac7feae1f6c09a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-schema-definition"></a><span data-ttu-id="1e4f6-102">Definice schématu DataTable</span><span class="sxs-lookup"><span data-stu-id="1e4f6-102">DataTable Schema Definition</span></span>
<span data-ttu-id="1e4f6-103">Schéma a struktura tabulky je reprezentována sloupce a omezení.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-103">The schema, or structure, of a table is represented by columns and constraints.</span></span> <span data-ttu-id="1e4f6-104">Můžete definovat schéma <xref:System.Data.DataTable> pomocí <xref:System.Data.DataColumn> objekty a také <xref:System.Data.ForeignKeyConstraint> a <xref:System.Data.UniqueConstraint> objekty.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-104">You define the schema of a <xref:System.Data.DataTable> using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="1e4f6-105">Sloupce v tabulce můžete mapovat na sloupce ve zdroji dat, obsahují počítané hodnoty z výrazů, automaticky zvýšit jejich hodnoty nebo obsahovat hodnot primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-105">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="1e4f6-106">Odkazy na název sloupce, vztahy a omezení v tabulce rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-106">References by name to columns, relations, and constraints in a table are case-sensitive.</span></span> <span data-ttu-id="1e4f6-107">V tabulce, která mají stejný název, ale které se liší v případě může proto existovat dvě nebo více sloupců, vztahů nebo omezení.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-107">Two or more columns, relations, or constraints can therefore exist in a table that have the same name, but that differ in case.</span></span> <span data-ttu-id="1e4f6-108">Například můžete mít **Sloupec1** a **Sloupec1**.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-108">For example, you can have **Col1** and **col1**.</span></span> <span data-ttu-id="1e4f6-109">V například případě odkaz na některý ze sloupců podle názvu musí v případě názvu sloupce přesně shodovat; v opačném případě je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-109">In such as case, a reference to one of the columns by name must match the case of the column name exactly; otherwise an exception is thrown.</span></span> <span data-ttu-id="1e4f6-110">Například pokud tabulka **myTable** obsahuje sloupce **Sloupec1** a **Sloupec1**, by odkazujete **Sloupec1** podle názvu jako  **myTable.Columns["Col1"]**, a **Sloupec1** jako **myTable.Columns["col1"]**.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-110">For example, if the table **myTable** contains the columns **Col1** and **col1**, you would reference **Col1** by name as **myTable.Columns["Col1"]**, and **col1** as **myTable.Columns["col1"]**.</span></span> <span data-ttu-id="1e4f6-111">Pokus o buď sloupců jako odkaz na **myTable.Columns["COL1"]** by generovat výjimku.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-111">Attempting to reference either of the columns as **myTable.Columns["COL1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="1e4f6-112">Pravidlo rozlišování neplatí, pokud jen jeden sloupec, relaci nebo omezení s konkrétním názvem existuje.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-112">The case-sensitivity rule does not apply if only one column, relation, or constraint  with a particular name exists.</span></span> <span data-ttu-id="1e4f6-113">To znamená pokud žádný sloupec, relace nebo objektů omezení v tabulce odpovídá názvu této konkrétní sloupec, relace nebo objektů omezení, může odkaz na objekt podle názvu pomocí jakékoli případ a nedojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-113">That is, if no other column, relation, or constraint object in the table matches the name of that particular column, relation, or constraint object, you may reference the object by name using any case, and no exception is thrown.</span></span> <span data-ttu-id="1e4f6-114">Například, pokud tabulka obsahuje pouze **Sloupec1**, můžete odkazovat pomocí **Moje. Sloupce ["Sloupec1"]**.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-114">For example, if the table has only **Col1**, you can reference it using **my.Columns["COL1"]**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e4f6-115"><xref:System.Data.DataTable.CaseSensitive%2A> Vlastnost **DataTable** nemá vliv na toto chování.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-115">The <xref:System.Data.DataTable.CaseSensitive%2A> property of the **DataTable** does not affect this behavior.</span></span> <span data-ttu-id="1e4f6-116">**CaseSensitive** vlastnost se vztahuje na data v tabulce a ovlivňuje řazení, vyhledávání a filtrování, vynucení omezení a tak dále, ale ne na odkazy na sloupce, vztahy a omezení.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-116">The **CaseSensitive** property applies to the data in a table and affects sorting, searching, filtering, enforcing constraints, and so on, but not to references to the columns, relations, and constraints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e4f6-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1e4f6-117">In This Section</span></span>  
 [<span data-ttu-id="1e4f6-118">Přidávání sloupců do DataTable</span><span class="sxs-lookup"><span data-stu-id="1e4f6-118">Adding Columns to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 <span data-ttu-id="1e4f6-119">Popisuje, jak definovat sloupce tabulky pomocí **DataColumn** objekty.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-119">Describes how to define the columns of a table using **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="1e4f6-120">Vytváření výraz sloupce</span><span class="sxs-lookup"><span data-stu-id="1e4f6-120">Creating Expression Columns</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 <span data-ttu-id="1e4f6-121">Vysvětluje, jak **výraz** vlastnost sloupce lze použít k výpočtu hodnot na základě hodnot z ostatních sloupců v řádku.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-121">Explains how the **Expression** property of a column can be used to calculate values based on the values from other columns in the row.</span></span>  
  
 [<span data-ttu-id="1e4f6-122">Vytváření AutoIncrement sloupců</span><span class="sxs-lookup"><span data-stu-id="1e4f6-122">Creating AutoIncrement Columns</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 <span data-ttu-id="1e4f6-123">Popisuje, jak lze nastavit sloupec se automaticky zvýší číselné hodnoty zajistit jedinečný sloupec hodnotu na řádek.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-123">Describes how a column can be set to automatically increment numerical values to ensure a unique column value per row.</span></span>  
  
 [<span data-ttu-id="1e4f6-124">Definování primárních klíčů</span><span class="sxs-lookup"><span data-stu-id="1e4f6-124">Defining Primary Keys</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 <span data-ttu-id="1e4f6-125">Popisuje, jak určit primární klíč tabulky z jedné nebo více **DataColumn** objekty.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-125">Describes how to specify the primary key of a table from one or more **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="1e4f6-126">Omezení DataTable</span><span class="sxs-lookup"><span data-stu-id="1e4f6-126">DataTable Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 <span data-ttu-id="1e4f6-127">Popisuje, jak definovat cizí klíč a jedinečná omezení pro sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="1e4f6-127">Describes how to define foreign key and unique constraints for columns in a table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e4f6-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e4f6-128">See Also</span></span>  
 [<span data-ttu-id="1e4f6-129">DataTables</span><span class="sxs-lookup"><span data-stu-id="1e4f6-129">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="1e4f6-130">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="1e4f6-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
