---
title: association set end
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 48ba84d46e380462405551cc2d826d84368b351a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786928"
---
# <a name="association-set-end"></a><span data-ttu-id="c3f5a-102">association set end</span><span class="sxs-lookup"><span data-stu-id="c3f5a-102">association set end</span></span>
<span data-ttu-id="c3f5a-103">*Zakončení sady přidružení* identifikuje [typ entity](entity-type.md) a [sadu entit](entity-set.md) na konci [sady přidružení](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="c3f5a-103">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="c3f5a-104">Zakončení sady přidružení je definováno jako součást sady přidružení. sada přidružení musí mít zakončení přesně dvou sad přidružení.</span><span class="sxs-lookup"><span data-stu-id="c3f5a-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="c3f5a-105">Definice end sady přidružení obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="c3f5a-105">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="c3f5a-106">Jeden z typů entit zapojených do sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="c3f5a-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="c3f5a-107">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="c3f5a-107">(Required)</span></span>  
  
- <span data-ttu-id="c3f5a-108">Sada entit pro typ entity zapojená do sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="c3f5a-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="c3f5a-109">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="c3f5a-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3f5a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3f5a-110">Example</span></span>  
 <span data-ttu-id="c3f5a-111">Následující diagram znázorňuje koncepční model se dvěma přidruženími: `WrittenBy` a. `PublishedBy`</span><span class="sxs-lookup"><span data-stu-id="c3f5a-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Vzorový model se třemi typy entit](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="c3f5a-113">Následující diagram znázorňuje sadu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) na základě koncepčního modelu uvedeného výše.</span><span class="sxs-lookup"><span data-stu-id="c3f5a-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="c3f5a-114">Sada přidružení končí `Books` jako sady entit a `Publishers` .</span><span class="sxs-lookup"><span data-stu-id="c3f5a-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="c3f5a-115">BI v `Books` sadě entit představuje instanci `Book` typu entity v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c3f5a-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="c3f5a-116">Podobně PJ představuje `Publisher` instanci `Publishers` v sadě entit.</span><span class="sxs-lookup"><span data-stu-id="c3f5a-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="c3f5a-117">BiPj představuje instanci `PublishedBy` přidružení `PublishedBy` v sadě přidružení.</span><span class="sxs-lookup"><span data-stu-id="c3f5a-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje příklad sady.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="c3f5a-119">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů DSL označované jako konceptuální schéma Definition Language ([CSDL](./ef/language-reference/csdl-specification.md)).</span><span class="sxs-lookup"><span data-stu-id="c3f5a-119">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="c3f5a-120">Následující CSDL definuje kontejner entit s jednou sadou přidružení pro každé přidružení v diagramu výše.</span><span class="sxs-lookup"><span data-stu-id="c3f5a-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="c3f5a-121">Všimněte si, že zakončení sady přidružení je definováno jako součást každé definice sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="c3f5a-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="c3f5a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3f5a-122">See also</span></span>

- [<span data-ttu-id="c3f5a-123">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="c3f5a-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="c3f5a-124">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="c3f5a-124">Entity Data Model</span></span>](entity-data-model.md)
