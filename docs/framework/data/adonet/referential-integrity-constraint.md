---
title: referential integrity constraint
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: ad35df7bcca62ffdbc3842b0817b22c5482a3d4d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738371"
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="e009d-102">referential integrity constraint</span><span class="sxs-lookup"><span data-stu-id="e009d-102">referential integrity constraint</span></span>
<span data-ttu-id="e009d-103">*Omezení referenční integrity* v model EDM (Entity Data Model) (EDM) se podobá omezení referenční integrity v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="e009d-103">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="e009d-104">Stejným způsobem, že sloupec (nebo sloupce) z tabulky databáze může odkazovat na primární klíč jiné tabulky, může [vlastnost](property.md) (nebo vlastnosti) [typu entity](entity-type.md) odkazovat na [klíč entity](entity-key.md) jiného typu entity.</span><span class="sxs-lookup"><span data-stu-id="e009d-104">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](property.md) (or properties) of an [entity type](entity-type.md) can reference the [entity key](entity-key.md) of another entity type.</span></span> <span data-ttu-id="e009d-105">Odkazovaný typ entity se nazývá *hlavní konec* omezení.</span><span class="sxs-lookup"><span data-stu-id="e009d-105">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="e009d-106">Typ entity, který odkazuje na hlavní konec, se nazývá *závislý konec* omezení.</span><span class="sxs-lookup"><span data-stu-id="e009d-106">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="e009d-107">Omezení referenční integrity je definováno jako součást [přidružení](association-type.md) mezi dvěma typy entit.</span><span class="sxs-lookup"><span data-stu-id="e009d-107">A referential integrity constraint is defined as part of an [association](association-type.md) between two entity types.</span></span> <span data-ttu-id="e009d-108">Definice omezení referenční integrity určuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="e009d-108">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
- <span data-ttu-id="e009d-109">Hlavní konec omezení</span><span class="sxs-lookup"><span data-stu-id="e009d-109">The principal end of the constraint.</span></span> <span data-ttu-id="e009d-110">(Typ entity, jejíž klíč entity odkazuje na závislý konec.)</span><span class="sxs-lookup"><span data-stu-id="e009d-110">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
- <span data-ttu-id="e009d-111">Klíč entity hlavního elementu end</span><span class="sxs-lookup"><span data-stu-id="e009d-111">The entity key of the principal end.</span></span>  
  
- <span data-ttu-id="e009d-112">Závislý konec omezení</span><span class="sxs-lookup"><span data-stu-id="e009d-112">The dependent end of the constraint.</span></span> <span data-ttu-id="e009d-113">(Typ entity, která má vlastnost nebo vlastnosti odkazující na klíč entity hlavního elementu end.)</span><span class="sxs-lookup"><span data-stu-id="e009d-113">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
- <span data-ttu-id="e009d-114">Odkazovaná vlastnost nebo vlastnosti závislého elementu end.</span><span class="sxs-lookup"><span data-stu-id="e009d-114">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="e009d-115">Účelem omezení referenční integrity v modelu EDM je zajistit, aby platná přidružení existovala vždy.</span><span class="sxs-lookup"><span data-stu-id="e009d-115">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="e009d-116">Další informace najdete v tématu [vlastnost cizího klíče](foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="e009d-116">For more information, see [foreign key property](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e009d-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e009d-117">Example</span></span>  
 <span data-ttu-id="e009d-118">Následující diagram znázorňuje koncepční model se dvěma přidruženími: `WrittenBy` a `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="e009d-118">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="e009d-119">Typ entity `Book` má vlastnost, `PublisherId`, která odkazuje na klíč entity `Publisher` typu entity, když v přidružení `PublishedBy` definujete omezení referenční integrity.</span><span class="sxs-lookup"><span data-stu-id="e009d-119">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="e009d-120">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Příklad modelu referenčního omezení")</span><span class="sxs-lookup"><span data-stu-id="e009d-120">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="e009d-121">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="e009d-121">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="e009d-122">Následující CSDL definuje omezení referenční integrity u `PublishedBy` přidružení uvedeného v koncepčním modelu výše.</span><span class="sxs-lookup"><span data-stu-id="e009d-122">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="e009d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e009d-123">See also</span></span>

- [<span data-ttu-id="e009d-124">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="e009d-124">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="e009d-125">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="e009d-125">Entity Data Model</span></span>](entity-data-model.md)
