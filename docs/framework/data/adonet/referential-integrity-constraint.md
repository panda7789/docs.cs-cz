---
title: "omezení referenční integrity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 232098a4940e223fd8553eefa4964777b1695c5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="682d8-102">omezení referenční integrity</span><span class="sxs-lookup"><span data-stu-id="682d8-102">referential integrity constraint</span></span>
<span data-ttu-id="682d8-103">A *omezení referenční integrity* v Entity Data Model (EDM) je podobná omezení referenční integrity v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="682d8-103">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="682d8-104">Stejným způsobem, že sloupec (nebo sloupce) z tabulky databáze může odkazovat primární klíč jiné tabulky [vlastnost](../../../../docs/framework/data/adonet/property.md) (nebo vlastnosti) z [typ entity](../../../../docs/framework/data/adonet/entity-type.md) může odkazovat [klíč entity ](../../../../docs/framework/data/adonet/entity-key.md) jiného typu entity.</span><span class="sxs-lookup"><span data-stu-id="682d8-104">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](../../../../docs/framework/data/adonet/property.md) (or properties) of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) can reference the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span> <span data-ttu-id="682d8-105">Je volána typ entity, který se odkazuje *hlavní end* omezení.</span><span class="sxs-lookup"><span data-stu-id="682d8-105">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="682d8-106">Typ entity, který odkazuje na hlavní end je volána *ukončení závislosti* omezení.</span><span class="sxs-lookup"><span data-stu-id="682d8-106">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="682d8-107">Omezení referenční integrity je definován jako součást [přidružení](../../../../docs/framework/data/adonet/association-type.md) mezi dvěma typy entit.</span><span class="sxs-lookup"><span data-stu-id="682d8-107">A referential integrity constraint is defined as part of an [association](../../../../docs/framework/data/adonet/association-type.md) between two entity types.</span></span> <span data-ttu-id="682d8-108">Definice omezení referenční integrity určuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="682d8-108">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
-   <span data-ttu-id="682d8-109">Hlavní konec omezení.</span><span class="sxs-lookup"><span data-stu-id="682d8-109">The principal end of the constraint.</span></span> <span data-ttu-id="682d8-110">(Typ entity jejichž klíč entity odkazuje ukončení závislosti.)</span><span class="sxs-lookup"><span data-stu-id="682d8-110">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
-   <span data-ttu-id="682d8-111">Klíč entity hlavní konce.</span><span class="sxs-lookup"><span data-stu-id="682d8-111">The entity key of the principal end.</span></span>  
  
-   <span data-ttu-id="682d8-112">Závislého konce omezení.</span><span class="sxs-lookup"><span data-stu-id="682d8-112">The dependent end of the constraint.</span></span> <span data-ttu-id="682d8-113">(Typu entity, který má vlastnost nebo vlastnosti, které klíč entity hlavní konce.)</span><span class="sxs-lookup"><span data-stu-id="682d8-113">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
-   <span data-ttu-id="682d8-114">Odkazující vlastnost nebo vlastnosti ukončení závislosti.</span><span class="sxs-lookup"><span data-stu-id="682d8-114">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="682d8-115">Účelem omezení referenční integrity v modelu EDM je zajistit, vždy existují platný přidružení.</span><span class="sxs-lookup"><span data-stu-id="682d8-115">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="682d8-116">Další informace najdete v tématu [vlastností cizího klíče](../../../../docs/framework/data/adonet/foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="682d8-116">For more information, see [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="682d8-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="682d8-117">Example</span></span>  
 <span data-ttu-id="682d8-118">Následující diagram znázorňuje Koncepční model se dvě přidružení: `WrittenBy` a `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="682d8-118">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="682d8-119">`Book` Typ entity má vlastnosti, `PublisherId`, klíč entity, který odkazuje `Publisher` typ entity, když definujete omezení referenční integrity na `PublishedBy` přidružení.</span><span class="sxs-lookup"><span data-stu-id="682d8-119">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="682d8-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span><span class="sxs-lookup"><span data-stu-id="682d8-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span></span>  
  
 <span data-ttu-id="682d8-121">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="682d8-121">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="682d8-122">Následující CSDL definuje omezení referenční integrity na `PublishedBy` přidružení zobrazí v konceptuálním modelu výše.</span><span class="sxs-lookup"><span data-stu-id="682d8-122">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="682d8-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="682d8-123">See Also</span></span>  
 [<span data-ttu-id="682d8-124">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="682d8-124">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="682d8-125">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="682d8-125">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
