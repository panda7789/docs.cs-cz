---
title: 'Postupy: Přizpůsobení tříd entit pomocí editoru kódu'
ms.date: 03/30/2017
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
ms.openlocfilehash: 67a0e17b6a81d804ce101bf56d8da82fe330479c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743421"
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="39591-102">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="39591-102">How to: Customize Entity Classes by Using the Code Editor</span></span>
<span data-ttu-id="39591-103">Vývojáři, kteří používají Visual Studio můžete použít Návrháře relací objektů pokud chcete vytvořit nebo přizpůsobit jejich tříd entit.</span><span class="sxs-lookup"><span data-stu-id="39591-103">Developers using Visual Studio can use the Object Relational Designer to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="39591-104">Editor kódu sady Visual Studio můžete použít také napsat vlastní kód mapování nebo přizpůsobit kód, který již byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="39591-104">You can also use the Visual Studio code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="39591-105">Další informace najdete v tématu [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="39591-105">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="39591-106">Témata v této části popisují, jak přizpůsobit objektový model.</span><span class="sxs-lookup"><span data-stu-id="39591-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="39591-107">Postupy: Zadání databázových názvů</span><span class="sxs-lookup"><span data-stu-id="39591-107">How to: Specify Database Names</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 <span data-ttu-id="39591-108">Popisuje způsob použití <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="39591-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="39591-109">Postupy: Znázornění tabulek jako tříd</span><span class="sxs-lookup"><span data-stu-id="39591-109">How to: Represent Tables as Classes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="39591-110">Popisuje způsob použití <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="39591-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="39591-111">Postupy: Znázornění sloupců jako členů tříd</span><span class="sxs-lookup"><span data-stu-id="39591-111">How to: Represent Columns as Class Members</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="39591-112">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="39591-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="39591-113">Postupy: Znázornění primárních klíčů</span><span class="sxs-lookup"><span data-stu-id="39591-113">How to: Represent Primary Keys</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 <span data-ttu-id="39591-114">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="39591-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="39591-115">Postupy: Mapování databázových relace</span><span class="sxs-lookup"><span data-stu-id="39591-115">How to: Map Database Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 <span data-ttu-id="39591-116">Poskytuje příklady použití <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="39591-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="39591-117">Postupy: Znázornění sloupců jako generovaných databází</span><span class="sxs-lookup"><span data-stu-id="39591-117">How to: Represent Columns as Database-Generated</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="39591-118">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="39591-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="39591-119">Postupy: Znázornění sloupců jako časové razítko nebo verze sloupce</span><span class="sxs-lookup"><span data-stu-id="39591-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="39591-120">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="39591-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="39591-121">Postupy: Zadejte databázi datové typy</span><span class="sxs-lookup"><span data-stu-id="39591-121">How to: Specify Database Data Types</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 <span data-ttu-id="39591-122">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="39591-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="39591-123">Postupy: Znázornění vypočítaných sloupců</span><span class="sxs-lookup"><span data-stu-id="39591-123">How to: Represent Computed Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 <span data-ttu-id="39591-124">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="39591-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="39591-125">Postupy: Zadání polí privátního úložiště</span><span class="sxs-lookup"><span data-stu-id="39591-125">How to: Specify Private Storage Fields</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="39591-126">Popisuje způsob použití <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="39591-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="39591-127">Postupy: Znázornění sloupců jako povolujících hodnoty Null</span><span class="sxs-lookup"><span data-stu-id="39591-127">How to: Represent Columns as Allowing Null Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="39591-128">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="39591-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="39591-129">Postupy: Mapování hierarchií dědičnosti</span><span class="sxs-lookup"><span data-stu-id="39591-129">How to: Map Inheritance Hierarchies</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="39591-130">Popisuje mapování k zadání hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="39591-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="39591-131">Postupy: Zadejte kontroly konfliktů souběžnosti</span><span class="sxs-lookup"><span data-stu-id="39591-131">How to: Specify Concurrency-Conflict Checking</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="39591-132">Popisuje způsob použití <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="39591-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39591-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39591-133">See also</span></span>

- [<span data-ttu-id="39591-134">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="39591-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
