---
title: foreign key property
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: e2f41c2db9aea26c7954a99ebf3f40b03e8df735
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795038"
---
# <a name="foreign-key-property"></a><span data-ttu-id="21cdd-102">foreign key property</span><span class="sxs-lookup"><span data-stu-id="21cdd-102">foreign key property</span></span>
<span data-ttu-id="21cdd-103">*Vlastnost cizího klíče* v model EDM (Entity Data Model) (EDM) je [vlastnost](property.md) primitivního typu (nebo sada vlastností primitivního typu) pro [typ entity](entity-type.md) , který obsahuje [klíč entity](entity-key.md) jiného typu entity.</span><span class="sxs-lookup"><span data-stu-id="21cdd-103">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](property.md) (or a set of primitive type properties) on an [entity type](entity-type.md) that contains the [entity key](entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="21cdd-104">Vlastnost cizího klíče je analogická jako sloupec cizího klíče v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="21cdd-104">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="21cdd-105">Stejným způsobem, jakým se používají sloupce cizího klíče v relační databázi k vytváření vztahů mezi řádky v tabulkách, se vlastnosti cizích klíčů v koncepčním modelu používají k navázání [přidružení](association-type.md) mezi typy entit.</span><span class="sxs-lookup"><span data-stu-id="21cdd-105">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](association-type.md) between entity types.</span></span> <span data-ttu-id="21cdd-106">[Omezení referenční integrity](referential-integrity-constraint.md) slouží k definování přidružení mezi dvěma typy entit, pokud jeden z typů má vlastnost cizího klíče.</span><span class="sxs-lookup"><span data-stu-id="21cdd-106">A [referential integrity constraint](referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21cdd-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="21cdd-107">Example</span></span>  
 <span data-ttu-id="21cdd-108">Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher` `Author`a.</span><span class="sxs-lookup"><span data-stu-id="21cdd-108">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="21cdd-109">Typ entity má vlastnost, `PublisherId`která odkazuje `Publisher` na klíč entity typu entity při definování omezení referenční integrity u `PublishedBy` přidružení. `Book`</span><span class="sxs-lookup"><span data-stu-id="21cdd-109">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="21cdd-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Příklad modelu referenčního omezení")</span><span class="sxs-lookup"><span data-stu-id="21cdd-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="21cdd-111">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="21cdd-111">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="21cdd-112">Následující CSDL používá vlastnost `PublisherId` cizího klíče k definování omezení referenční integrity `PublishedBy` u přidružení uvedeného v koncepčním modelu uvedeném výše.</span><span class="sxs-lookup"><span data-stu-id="21cdd-112">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="21cdd-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21cdd-113">See also</span></span>

- [<span data-ttu-id="21cdd-114">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="21cdd-114">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="21cdd-115">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="21cdd-115">Entity Data Model</span></span>](entity-data-model.md)
