---
title: referential integrity constraint
description: Seznamte se s omezeními referenční integrity v model EDM (Entity Data Model), která zajistí, aby platná přidružení existovala vždycky mezi typy entit.
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 65c811b2a12a64870107ff771d5acc64e86f2c1f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286621"
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="6ec82-103">referential integrity constraint</span><span class="sxs-lookup"><span data-stu-id="6ec82-103">referential integrity constraint</span></span>
<span data-ttu-id="6ec82-104">*Omezení referenční integrity* v model EDM (Entity Data Model) (EDM) se podobá omezení referenční integrity v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="6ec82-104">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="6ec82-105">Stejným způsobem, že sloupec (nebo sloupce) z tabulky databáze může odkazovat na primární klíč jiné tabulky, může [vlastnost](property.md) (nebo vlastnosti) [typu entity](entity-type.md) odkazovat na [klíč entity](entity-key.md) jiného typu entity.</span><span class="sxs-lookup"><span data-stu-id="6ec82-105">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](property.md) (or properties) of an [entity type](entity-type.md) can reference the [entity key](entity-key.md) of another entity type.</span></span> <span data-ttu-id="6ec82-106">Odkazovaný typ entity se nazývá *hlavní konec* omezení.</span><span class="sxs-lookup"><span data-stu-id="6ec82-106">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="6ec82-107">Typ entity, který odkazuje na hlavní konec, se nazývá *závislý konec* omezení.</span><span class="sxs-lookup"><span data-stu-id="6ec82-107">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="6ec82-108">Omezení referenční integrity je definováno jako součást [přidružení](association-type.md) mezi dvěma typy entit.</span><span class="sxs-lookup"><span data-stu-id="6ec82-108">A referential integrity constraint is defined as part of an [association](association-type.md) between two entity types.</span></span> <span data-ttu-id="6ec82-109">Definice omezení referenční integrity určuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="6ec82-109">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
- <span data-ttu-id="6ec82-110">Hlavní konec omezení</span><span class="sxs-lookup"><span data-stu-id="6ec82-110">The principal end of the constraint.</span></span> <span data-ttu-id="6ec82-111">(Typ entity, jejíž klíč entity odkazuje na závislý konec.)</span><span class="sxs-lookup"><span data-stu-id="6ec82-111">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
- <span data-ttu-id="6ec82-112">Klíč entity hlavního elementu end</span><span class="sxs-lookup"><span data-stu-id="6ec82-112">The entity key of the principal end.</span></span>  
  
- <span data-ttu-id="6ec82-113">Závislý konec omezení</span><span class="sxs-lookup"><span data-stu-id="6ec82-113">The dependent end of the constraint.</span></span> <span data-ttu-id="6ec82-114">(Typ entity, která má vlastnost nebo vlastnosti odkazující na klíč entity hlavního elementu end.)</span><span class="sxs-lookup"><span data-stu-id="6ec82-114">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
- <span data-ttu-id="6ec82-115">Odkazovaná vlastnost nebo vlastnosti závislého elementu end.</span><span class="sxs-lookup"><span data-stu-id="6ec82-115">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="6ec82-116">Účelem omezení referenční integrity v modelu EDM je zajistit, aby platná přidružení existovala vždy.</span><span class="sxs-lookup"><span data-stu-id="6ec82-116">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="6ec82-117">Další informace najdete v tématu [vlastnost cizího klíče](foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="6ec82-117">For more information, see [foreign key property](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ec82-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ec82-118">Example</span></span>  
 <span data-ttu-id="6ec82-119">Následující diagram znázorňuje koncepční model se dvěma přidruženími: `WrittenBy` a `PublishedBy` .</span><span class="sxs-lookup"><span data-stu-id="6ec82-119">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="6ec82-120">`Book`Typ entity má vlastnost, `PublisherId` která odkazuje na klíč entity `Publisher` typu entity při definování omezení referenční integrity u `PublishedBy` přidružení.</span><span class="sxs-lookup"><span data-stu-id="6ec82-120">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="6ec82-121">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Příklad modelu referenčního omezení")</span><span class="sxs-lookup"><span data-stu-id="6ec82-121">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="6ec82-122">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="6ec82-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="6ec82-123">Následující CSDL definuje omezení referenční integrity u `PublishedBy` přidružení uvedeného výše v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="6ec82-123">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="6ec82-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ec82-124">See also</span></span>

- [<span data-ttu-id="6ec82-125">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="6ec82-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="6ec82-126">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="6ec82-126">Entity Data Model</span></span>](entity-data-model.md)
