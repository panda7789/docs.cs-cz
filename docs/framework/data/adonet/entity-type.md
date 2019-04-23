---
title: entity type
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 026b0aef7cf2de8fe222721191afa459859701ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108261"
---
# <a name="entity-type"></a><span data-ttu-id="00bad-102">entity type</span><span class="sxs-lookup"><span data-stu-id="00bad-102">entity type</span></span>
<span data-ttu-id="00bad-103">*Typ entity* je základním stavebním blokem pro popis struktury data pomocí modelu Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="00bad-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="00bad-104">Typ entity v konceptuálním modelu reprezentuje strukturu těchto koncepty nejvyšší úrovně, jako je například Zákazníci a objednávky.</span><span class="sxs-lookup"><span data-stu-id="00bad-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="00bad-105">Typ entity je šablona pro instance typu entity.</span><span class="sxs-lookup"><span data-stu-id="00bad-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="00bad-106">Každá šablona obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="00bad-106">Each template contains the following information:</span></span>  
  
-   <span data-ttu-id="00bad-107">Jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="00bad-107">A unique name.</span></span> <span data-ttu-id="00bad-108">(Povinné).</span><span class="sxs-lookup"><span data-stu-id="00bad-108">(Required.)</span></span>  
  
-   <span data-ttu-id="00bad-109">[Klíč entity](../../../../docs/framework/data/adonet/entity-key.md) určené jednu nebo více vlastností.</span><span class="sxs-lookup"><span data-stu-id="00bad-109">An [entity key](../../../../docs/framework/data/adonet/entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="00bad-110">(Povinné).</span><span class="sxs-lookup"><span data-stu-id="00bad-110">(Required.)</span></span>  
  
-   <span data-ttu-id="00bad-111">Data ve formě [vlastnosti](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="00bad-111">Data in the form of [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="00bad-112">(Volitelné).</span><span class="sxs-lookup"><span data-stu-id="00bad-112">(Optional.)</span></span>  
  
-   <span data-ttu-id="00bad-113">[Navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) , která umožňují navigaci z jednoho [end](../../../../docs/framework/data/adonet/association-end.md) ze [přidružení](../../../../docs/framework/data/adonet/association-type.md) na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="00bad-113">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) that allow for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="00bad-114">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="00bad-114">(Optional)</span></span>  
  
 <span data-ttu-id="00bad-115">V aplikaci, která představuje instance typu entity na konkrétní objekt (například konkrétního zákazníka nebo pořadí).</span><span class="sxs-lookup"><span data-stu-id="00bad-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="00bad-116">Každá instance typu entity musí mít jedinečnou [klíč entity](../../../../docs/framework/data/adonet/entity-key.md) v rámci [sadu entit](../../../../docs/framework/data/adonet/entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="00bad-116">Each instance of an entity type must have a unique [entity key](../../../../docs/framework/data/adonet/entity-key.md) within an [entity set](../../../../docs/framework/data/adonet/entity-set.md).</span></span>  
  
 <span data-ttu-id="00bad-117">Dvě instance typu entity se považovat za rovné pouze v případě, že jsou stejného typu a hodnoty jejich klíče entity jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="00bad-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00bad-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="00bad-118">Example</span></span>  
 <span data-ttu-id="00bad-119">Následující diagram znázorňuje Koncepční model s tři typy entit: `Book`, `Publisher`, a `Author`:</span><span class="sxs-lookup"><span data-stu-id="00bad-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![Příklad modelu s tři typy entit](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="00bad-121">Všimněte si, že vlastnosti každého typu entity, které tvoří jeho klíč entity, jsou označeny "(klíč)".</span><span class="sxs-lookup"><span data-stu-id="00bad-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="00bad-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů.</span><span class="sxs-lookup"><span data-stu-id="00bad-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="00bad-123">Definuje následující CSDL `Book` typ entity, které jsou zobrazeny ve výše uvedeném diagramu:</span><span class="sxs-lookup"><span data-stu-id="00bad-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="00bad-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00bad-124">See also</span></span>

- [<span data-ttu-id="00bad-125">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="00bad-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="00bad-126">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="00bad-126">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="00bad-127">facet</span><span class="sxs-lookup"><span data-stu-id="00bad-127">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)
