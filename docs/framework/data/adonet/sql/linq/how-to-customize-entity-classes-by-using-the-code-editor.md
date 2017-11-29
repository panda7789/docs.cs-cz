---
title: "Postupy: přizpůsobení tříd entit pomocí editoru kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d5586e28e784c43488245db814abf32d863232fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="2e1f0-102">Postupy: přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="2e1f0-102">How to: Customize Entity Classes by Using the Code Editor</span></span>
<span data-ttu-id="2e1f0-103">Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vytvořit nebo upravit jejich tříd entit.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-103">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="2e1f0-104">Můžete také [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] editor kódu napsat vlastní kód mapování nebo přizpůsobit kód, který již byl vygenerován.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-104">You can also use the [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="2e1f0-105">Další informace najdete v tématu [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="2e1f0-105">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="2e1f0-106">Témata v této části popisují postup přizpůsobení modelu objektu.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="2e1f0-107">Postupy: Zadejte názvy databází</span><span class="sxs-lookup"><span data-stu-id="2e1f0-107">How to: Specify Database Names</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 <span data-ttu-id="2e1f0-108">Popisuje způsob použití <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="2e1f0-109">Postupy: představují tabulky jako třídy</span><span class="sxs-lookup"><span data-stu-id="2e1f0-109">How to: Represent Tables as Classes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="2e1f0-110">Popisuje způsob použití <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="2e1f0-111">Postupy: představují sloupce jako členy třídy</span><span class="sxs-lookup"><span data-stu-id="2e1f0-111">How to: Represent Columns as Class Members</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="2e1f0-112">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="2e1f0-113">Postupy: představují primární klíče</span><span class="sxs-lookup"><span data-stu-id="2e1f0-113">How to: Represent Primary Keys</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 <span data-ttu-id="2e1f0-114">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="2e1f0-115">Postupy: mapování relace databáze</span><span class="sxs-lookup"><span data-stu-id="2e1f0-115">How to: Map Database Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 <span data-ttu-id="2e1f0-116">Obsahuje příklady použití <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="2e1f0-117">Postupy: představují sloupce jako generované databáze</span><span class="sxs-lookup"><span data-stu-id="2e1f0-117">How to: Represent Columns as Database-Generated</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="2e1f0-118">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="2e1f0-119">Postupy: představují sloupce jako časové razítko nebo verze sloupce</span><span class="sxs-lookup"><span data-stu-id="2e1f0-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="2e1f0-120">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="2e1f0-121">Postupy: určení typů dat databáze</span><span class="sxs-lookup"><span data-stu-id="2e1f0-121">How to: Specify Database Data Types</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 <span data-ttu-id="2e1f0-122">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="2e1f0-123">Postupy: představují vypočítaného sloupce</span><span class="sxs-lookup"><span data-stu-id="2e1f0-123">How to: Represent Computed Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 <span data-ttu-id="2e1f0-124">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="2e1f0-125">Postupy: Zadejte privátní úložiště polí</span><span class="sxs-lookup"><span data-stu-id="2e1f0-125">How to: Specify Private Storage Fields</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="2e1f0-126">Popisuje způsob použití <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="2e1f0-127">Postupy: představují sloupce tak, aby umožňoval hodnoty Null</span><span class="sxs-lookup"><span data-stu-id="2e1f0-127">How to: Represent Columns as Allowing Null Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="2e1f0-128">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="2e1f0-129">Postupy: mapování hierarchie dědičnosti</span><span class="sxs-lookup"><span data-stu-id="2e1f0-129">How to: Map Inheritance Hierarchies</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="2e1f0-130">Popisuje mapování zapotřebí zadat hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="2e1f0-131">Postupy: Zadejte Kontrola konfliktu souběžnosti</span><span class="sxs-lookup"><span data-stu-id="2e1f0-131">How to: Specify Concurrency-Conflict Checking</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="2e1f0-132">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e1f0-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e1f0-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e1f0-133">See Also</span></span>  
 [<span data-ttu-id="2e1f0-134">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="2e1f0-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
