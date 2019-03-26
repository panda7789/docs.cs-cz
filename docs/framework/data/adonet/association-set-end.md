---
title: Nastavit konec asociace
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 61dc00e6c349a25767f6221bed56ef8b65f823d9
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412003"
---
# <a name="association-set-end"></a><span data-ttu-id="681da-102">Nastavit konec asociace</span><span class="sxs-lookup"><span data-stu-id="681da-102">association set end</span></span>
<span data-ttu-id="681da-103">*Přidružení nastavit konec* identifikuje [typ entity](../../../../docs/framework/data/adonet/entity-type.md) a [sadu entit](../../../../docs/framework/data/adonet/entity-set.md) na konci [sada přidružení](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="681da-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="681da-104">Zakončení sady jsou definované jako součást sady přidružení; skupinu přidružení musí mít přesně dva zakončení sady.</span><span class="sxs-lookup"><span data-stu-id="681da-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="681da-105">Definici sady end přidružení obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="681da-105">An association set end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="681da-106">Jeden z typů entity účastnící se přidružení nastavení.</span><span class="sxs-lookup"><span data-stu-id="681da-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="681da-107">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="681da-107">(Required)</span></span>  
  
-   <span data-ttu-id="681da-108">Sada entit pro typ entity účastnící se sada přidružení.</span><span class="sxs-lookup"><span data-stu-id="681da-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="681da-109">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="681da-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="681da-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="681da-110">Example</span></span>  
 <span data-ttu-id="681da-111">Následující diagram znázorňuje Koncepční model se dvěma přidružení: `WrittenBy` a `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="681da-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Příklad modelu s tři typy entit](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="681da-113">Následující diagram znázorňuje skupinu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) založené na konceptuální model, uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="681da-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="681da-114">Jsou sady zakončení `Books` a `Publishers` sady entit.</span><span class="sxs-lookup"><span data-stu-id="681da-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="681da-115">BI v `Books` sadu entit představuje instanci `Book` typ entity v době běhu.</span><span class="sxs-lookup"><span data-stu-id="681da-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="681da-116">Obdobně Pj představuje `Publisher` instance v `Publishers` sady entit.</span><span class="sxs-lookup"><span data-stu-id="681da-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="681da-117">BiPj představuje instanci `PublishedBy` přidružení v `PublishedBy` sada přidružení.</span><span class="sxs-lookup"><span data-stu-id="681da-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Snímek obrazovky zobrazující příklad sady.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="681da-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá DSL volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů.</span><span class="sxs-lookup"><span data-stu-id="681da-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="681da-120">Následující CSDL definuje kontejneru entity s jeden přidružení nastavení pro každé přidružení ve výše uvedeném diagramu.</span><span class="sxs-lookup"><span data-stu-id="681da-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="681da-121">Všimněte si, že Sada zakončení jsou definované jako součást každé definice sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="681da-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="681da-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="681da-122">See also</span></span>
- [<span data-ttu-id="681da-123">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="681da-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="681da-124">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="681da-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
