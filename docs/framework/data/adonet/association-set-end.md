---
title: association set end
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: f7ec1ca6fcdf299b9fcfc78f299ea4c6c5267cd3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738626"
---
# <a name="association-set-end"></a><span data-ttu-id="bb5fb-102">association set end</span><span class="sxs-lookup"><span data-stu-id="bb5fb-102">association set end</span></span>
<span data-ttu-id="bb5fb-103">*Zakončení sady přidružení* identifikuje [typ entity](entity-type.md) a [sadu entit](entity-set.md) na konci [sady přidružení](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="bb5fb-103">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="bb5fb-104">Zakončení sady přidružení je definováno jako součást sady přidružení. sada přidružení musí mít zakončení přesně dvou sad přidružení.</span><span class="sxs-lookup"><span data-stu-id="bb5fb-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="bb5fb-105">Definice end sady přidružení obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="bb5fb-105">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="bb5fb-106">Jeden z typů entit zapojených do sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="bb5fb-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="bb5fb-107">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="bb5fb-107">(Required)</span></span>  
  
- <span data-ttu-id="bb5fb-108">Sada entit pro typ entity zapojená do sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="bb5fb-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="bb5fb-109">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="bb5fb-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb5fb-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb5fb-110">Example</span></span>  
 <span data-ttu-id="bb5fb-111">Následující diagram znázorňuje koncepční model se dvěma přidruženími: `WrittenBy` a `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="bb5fb-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Vzorový model se třemi typy entit](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="bb5fb-113">Následující diagram znázorňuje sadu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) na základě koncepčního modelu uvedeného výše.</span><span class="sxs-lookup"><span data-stu-id="bb5fb-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="bb5fb-114">Sada přidružení končí jako `Books` a `Publishers` sady entit.</span><span class="sxs-lookup"><span data-stu-id="bb5fb-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="bb5fb-115">BI v `Books` sadě entit představuje instanci `Book` typu entity v době běhu.</span><span class="sxs-lookup"><span data-stu-id="bb5fb-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="bb5fb-116">Podobně PJ představuje instanci `Publisher` v sadě entit `Publishers`.</span><span class="sxs-lookup"><span data-stu-id="bb5fb-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="bb5fb-117">BiPj představuje instanci přidružení `PublishedBy` v sadě přidružení `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="bb5fb-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje příklad sady.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="bb5fb-119">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů DSL označované jako konceptuální schéma Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)).</span><span class="sxs-lookup"><span data-stu-id="bb5fb-119">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="bb5fb-120">Následující CSDL definuje kontejner entit s jednou sadou přidružení pro každé přidružení v diagramu výše.</span><span class="sxs-lookup"><span data-stu-id="bb5fb-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="bb5fb-121">Všimněte si, že zakončení sady přidružení je definováno jako součást každé definice sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="bb5fb-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="bb5fb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb5fb-122">See also</span></span>

- [<span data-ttu-id="bb5fb-123">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="bb5fb-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="bb5fb-124">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="bb5fb-124">Entity Data Model</span></span>](entity-data-model.md)
