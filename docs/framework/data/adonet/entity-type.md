---
title: Typ entity
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 3955de1873d80e85df713a557750e34e76efeb41
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502881"
---
# <a name="entity-type"></a><span data-ttu-id="1b6c8-102">Typ entity</span><span class="sxs-lookup"><span data-stu-id="1b6c8-102">entity type</span></span>
<span data-ttu-id="1b6c8-103">*Typ entity* je základním stavebním blokem pro popis struktury data pomocí modelu Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="1b6c8-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="1b6c8-104">Typ entity v konceptuálním modelu reprezentuje strukturu těchto koncepty nejvyšší úrovně, jako je například Zákazníci a objednávky.</span><span class="sxs-lookup"><span data-stu-id="1b6c8-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="1b6c8-105">Typ entity je šablona pro instance typu entity.</span><span class="sxs-lookup"><span data-stu-id="1b6c8-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="1b6c8-106">Každá šablona obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="1b6c8-106">Each template contains the following information:</span></span>  
  
-   <span data-ttu-id="1b6c8-107">Jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="1b6c8-107">A unique name.</span></span> <span data-ttu-id="1b6c8-108">(Povinné).</span><span class="sxs-lookup"><span data-stu-id="1b6c8-108">(Required.)</span></span>  
  
-   <span data-ttu-id="1b6c8-109">[Klíč entity](../../../../docs/framework/data/adonet/entity-key.md) určené jednu nebo více vlastností.</span><span class="sxs-lookup"><span data-stu-id="1b6c8-109">An [entity key](../../../../docs/framework/data/adonet/entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="1b6c8-110">(Povinné).</span><span class="sxs-lookup"><span data-stu-id="1b6c8-110">(Required.)</span></span>  
  
-   <span data-ttu-id="1b6c8-111">Data ve formě [vlastnosti](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="1b6c8-111">Data in the form of [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="1b6c8-112">(Volitelné).</span><span class="sxs-lookup"><span data-stu-id="1b6c8-112">(Optional.)</span></span>  
  
-   <span data-ttu-id="1b6c8-113">[Navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) , která umožňují navigaci z jednoho [end](../../../../docs/framework/data/adonet/association-end.md) ze [přidružení](../../../../docs/framework/data/adonet/association-type.md) na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="1b6c8-113">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) that allow for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="1b6c8-114">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="1b6c8-114">(Optional)</span></span>  
  
 <span data-ttu-id="1b6c8-115">V aplikaci, která představuje instance typu entity na konkrétní objekt (například konkrétního zákazníka nebo pořadí).</span><span class="sxs-lookup"><span data-stu-id="1b6c8-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="1b6c8-116">Každá instance typu entity musí mít jedinečnou [klíč entity](../../../../docs/framework/data/adonet/entity-key.md) v rámci [sadu entit](../../../../docs/framework/data/adonet/entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="1b6c8-116">Each instance of an entity type must have a unique [entity key](../../../../docs/framework/data/adonet/entity-key.md) within an [entity set](../../../../docs/framework/data/adonet/entity-set.md).</span></span>  
  
 <span data-ttu-id="1b6c8-117">Dvě instance typu entity se považovat za rovné pouze v případě, že jsou stejného typu a hodnoty jejich klíče entity jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="1b6c8-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b6c8-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b6c8-118">Example</span></span>  
 <span data-ttu-id="1b6c8-119">Následující diagram znázorňuje Koncepční model s tři typy entit: `Book`, `Publisher`, a `Author`:</span><span class="sxs-lookup"><span data-stu-id="1b6c8-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 <span data-ttu-id="1b6c8-120">![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="1b6c8-120">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="1b6c8-121">Všimněte si, že vlastnosti každého typu entity, které tvoří jeho klíč entity, jsou označeny "(klíč)".</span><span class="sxs-lookup"><span data-stu-id="1b6c8-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="1b6c8-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů.</span><span class="sxs-lookup"><span data-stu-id="1b6c8-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="1b6c8-123">Definuje následující CSDL `Book` typ entity, které jsou zobrazeny ve výše uvedeném diagramu:</span><span class="sxs-lookup"><span data-stu-id="1b6c8-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="1b6c8-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b6c8-124">See also</span></span>
- [<span data-ttu-id="1b6c8-125">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="1b6c8-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="1b6c8-126">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="1b6c8-126">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="1b6c8-127">facet</span><span class="sxs-lookup"><span data-stu-id="1b6c8-127">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)
