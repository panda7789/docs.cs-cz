---
title: entity type
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 1dafce5f7f95ba6f391c8742944f40a9afa7dcf8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737814"
---
# <a name="entity-type"></a><span data-ttu-id="78f6c-102">entity type</span><span class="sxs-lookup"><span data-stu-id="78f6c-102">entity type</span></span>
<span data-ttu-id="78f6c-103">*Typ entity* je základní stavební blok pro popis struktury dat pomocí model EDM (Entity Data Model) (EDM).</span><span class="sxs-lookup"><span data-stu-id="78f6c-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="78f6c-104">V koncepčním modelu představuje typ entity strukturu konceptů nejvyšší úrovně, jako jsou například zákazníci nebo objednávky.</span><span class="sxs-lookup"><span data-stu-id="78f6c-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="78f6c-105">Typ entity je šablona pro instance typu entity.</span><span class="sxs-lookup"><span data-stu-id="78f6c-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="78f6c-106">Každá šablona obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="78f6c-106">Each template contains the following information:</span></span>  
  
- <span data-ttu-id="78f6c-107">Jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="78f6c-107">A unique name.</span></span> <span data-ttu-id="78f6c-108">(Povinné.)</span><span class="sxs-lookup"><span data-stu-id="78f6c-108">(Required.)</span></span>  
  
- <span data-ttu-id="78f6c-109">[Klíč entity](entity-key.md) definovaný jednou nebo více vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="78f6c-109">An [entity key](entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="78f6c-110">(Povinné.)</span><span class="sxs-lookup"><span data-stu-id="78f6c-110">(Required.)</span></span>  
  
- <span data-ttu-id="78f6c-111">Data ve formě [vlastností](property.md).</span><span class="sxs-lookup"><span data-stu-id="78f6c-111">Data in the form of [properties](property.md).</span></span> <span data-ttu-id="78f6c-112">(Volitelné.)</span><span class="sxs-lookup"><span data-stu-id="78f6c-112">(Optional.)</span></span>  
  
- <span data-ttu-id="78f6c-113">[Navigační vlastnosti](navigation-property.md) , které umožňují navigaci od jednoho [konce](association-end.md) [přidružení](association-type.md) k druhému konci.</span><span class="sxs-lookup"><span data-stu-id="78f6c-113">[Navigation properties](navigation-property.md) that allow for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="78f6c-114">Volitelné</span><span class="sxs-lookup"><span data-stu-id="78f6c-114">(Optional)</span></span>  
  
 <span data-ttu-id="78f6c-115">V aplikaci instance typu entity představuje konkrétní objekt (například konkrétního zákazníka nebo objednávky).</span><span class="sxs-lookup"><span data-stu-id="78f6c-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="78f6c-116">Každá instance typu entity musí mít v [sadě entit](entity-set.md)jedinečný [klíč entity](entity-key.md) .</span><span class="sxs-lookup"><span data-stu-id="78f6c-116">Each instance of an entity type must have a unique [entity key](entity-key.md) within an [entity set](entity-set.md).</span></span>  
  
 <span data-ttu-id="78f6c-117">Dvě instance typu entity jsou považovány za rovné pouze v případě, že jsou stejného typu a hodnoty jejich klíčů entit jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="78f6c-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78f6c-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="78f6c-118">Example</span></span>  
 <span data-ttu-id="78f6c-119">Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher`a `Author`:</span><span class="sxs-lookup"><span data-stu-id="78f6c-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![Vzorový model se třemi typy entit](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="78f6c-121">Všimněte si, že vlastnosti každého typu entity, který tvoří klíč entity, jsou označeny řetězcem "(Key)".</span><span class="sxs-lookup"><span data-stu-id="78f6c-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="78f6c-122">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="78f6c-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="78f6c-123">Následující CSDL definuje typ entity `Book` zobrazený v diagramu výše:</span><span class="sxs-lookup"><span data-stu-id="78f6c-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="78f6c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78f6c-124">See also</span></span>

- [<span data-ttu-id="78f6c-125">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="78f6c-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="78f6c-126">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="78f6c-126">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="78f6c-127">facet</span><span class="sxs-lookup"><span data-stu-id="78f6c-127">facet</span></span>](facet.md)
