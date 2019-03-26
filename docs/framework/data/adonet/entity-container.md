---
title: kontejner entit
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: d2ad565ce73b2de4b10d2f15406b283a13bbef6e
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409884"
---
# <a name="entity-container"></a><span data-ttu-id="5d45d-102">kontejner entit</span><span class="sxs-lookup"><span data-stu-id="5d45d-102">entity container</span></span>
<span data-ttu-id="5d45d-103">*Kontejneru entity* je logické seskupení [sad entit](../../../../docs/framework/data/adonet/entity-set.md), [sad přidružení](../../../../docs/framework/data/adonet/association-set.md), a [importů funkci](../../../../docs/framework/data/adonet/model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="5d45d-103">An *entity container* is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md), [association sets](../../../../docs/framework/data/adonet/association-set.md), and [function imports](../../../../docs/framework/data/adonet/model-declared-function.md).</span></span>  
  
 <span data-ttu-id="5d45d-104">Musí být splněné tyto požadavky definované v konceptuálním modelu entity kontejneru:</span><span class="sxs-lookup"><span data-stu-id="5d45d-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
-   <span data-ttu-id="5d45d-105">Minimálně jednu entitu kontejneru musí být definován v každé koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="5d45d-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
-   <span data-ttu-id="5d45d-106">Kontejner entit musí mít jedinečný název v rámci každé koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="5d45d-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="5d45d-107">Kontejner entit můžete definovat, sad entit a sad přidružení, které používají typy entit a přidružení, které jsou definovány v jedné nebo více oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="5d45d-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="5d45d-108">Další informace najdete v tématu [modelu Entity Data Model: Obory názvů](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="5d45d-108">For more information, see [Entity Data Model: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d45d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d45d-109">Example</span></span>  
 <span data-ttu-id="5d45d-110">Následující diagram znázorňuje Koncepční model s tři typy entit: `Book`, `Publisher`, a `Author`.</span><span class="sxs-lookup"><span data-stu-id="5d45d-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="5d45d-111">Podívejte se na další příklad pro další informace.</span><span class="sxs-lookup"><span data-stu-id="5d45d-111">See the next example for more information.</span></span>  
  
 ![Příklad modelu s tři typy entit](./media/entity-container/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="5d45d-113">I když diagramu neznamená informací o entitách kontejneru, musí definovat konceptuálního modelu kontejnerem entity.</span><span class="sxs-lookup"><span data-stu-id="5d45d-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="5d45d-114">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá DSL volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů.</span><span class="sxs-lookup"><span data-stu-id="5d45d-114">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="5d45d-115">Následující CSDL definuje kontejneru entity pro koncepční model je vidět na obrázku výše.</span><span class="sxs-lookup"><span data-stu-id="5d45d-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="5d45d-116">Všimněte si, že název kontejneru entity je definován v atributu XML.</span><span class="sxs-lookup"><span data-stu-id="5d45d-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="5d45d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d45d-117">See also</span></span>
- [<span data-ttu-id="5d45d-118">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="5d45d-118">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="5d45d-119">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="5d45d-119">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
