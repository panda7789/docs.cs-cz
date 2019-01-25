---
title: Nastavit konec asociace
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 9a71fd434bea87a75e259a3d5caa902fbecf8a57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701635"
---
# <a name="association-set-end"></a><span data-ttu-id="ed5cb-102">Nastavit konec asociace</span><span class="sxs-lookup"><span data-stu-id="ed5cb-102">association set end</span></span>
<span data-ttu-id="ed5cb-103">*Přidružení nastavit konec* identifikuje [typ entity](../../../../docs/framework/data/adonet/entity-type.md) a [sadu entit](../../../../docs/framework/data/adonet/entity-set.md) na konci [sada přidružení](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="ed5cb-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="ed5cb-104">Zakončení sady jsou definované jako součást sady přidružení; skupinu přidružení musí mít přesně dva zakončení sady.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="ed5cb-105">Definici sady end přidružení obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="ed5cb-105">An association set end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="ed5cb-106">Jeden z typů entity účastnící se přidružení nastavení.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="ed5cb-107">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="ed5cb-107">(Required)</span></span>  
  
-   <span data-ttu-id="ed5cb-108">Sada entit pro typ entity účastnící se sada přidružení.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="ed5cb-109">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="ed5cb-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed5cb-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed5cb-110">Example</span></span>  
 <span data-ttu-id="ed5cb-111">Následující diagram znázorňuje Koncepční model se dvěma přidružení: `WrittenBy` a `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 <span data-ttu-id="ed5cb-112">![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="ed5cb-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="ed5cb-113">Následující diagram znázorňuje skupinu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) založené na konceptuální model, uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="ed5cb-114">Jsou sady zakončení `Books` a `Publishers` sady entit.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="ed5cb-115">BI v `Books` sadu entit představuje instanci `Book` typ entity v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="ed5cb-116">Obdobně Pj představuje `Publisher` instance v `Publishers` sady entit.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="ed5cb-117">BiPj představuje instanci `PublishedBy` přidružení v `PublishedBy` sada přidružení.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="ed5cb-118">![Nastaví příklad](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="ed5cb-118">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="ed5cb-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá DSL volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ed5cb-120">Následující CSDL definuje kontejneru entity s jeden přidružení nastavení pro každé přidružení ve výše uvedeném diagramu.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="ed5cb-121">Všimněte si, že Sada zakončení jsou definované jako součást každé definice sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="ed5cb-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="ed5cb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed5cb-122">See also</span></span>
- [<span data-ttu-id="ed5cb-123">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="ed5cb-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="ed5cb-124">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="ed5cb-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
