---
title: Komplexní typ
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 8daeac8309434b3c4e090d8e75f2de02d63e8b11
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="complex-type"></a><span data-ttu-id="29c63-102">Komplexní typ</span><span class="sxs-lookup"><span data-stu-id="29c63-102">complex type</span></span>
<span data-ttu-id="29c63-103">A *komplexní typ* o šablonu pro definování vlastností formátovaných, strukturovaných na [typy entit](../../../../docs/framework/data/adonet/entity-type.md) nebo na jiné komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="29c63-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="29c63-104">Každá šablona obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="29c63-104">Each template contains the following:</span></span>  
  
-   <span data-ttu-id="29c63-105">Jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="29c63-105">A unique name.</span></span> <span data-ttu-id="29c63-106">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="29c63-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29c63-107">Název pro komplexní typ nemůže být stejný jako název typu entity v rámci stejného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="29c63-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
-   <span data-ttu-id="29c63-108">Data ve formě jednoho nebo více [vlastnosti](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="29c63-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="29c63-109">(Volitelné).</span><span class="sxs-lookup"><span data-stu-id="29c63-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29c63-110">Vlastnost komplexního typu, může být jiná komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="29c63-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="29c63-111">Komplexní typ je podobná typ entity, pro komplexní typ přenášet datovou částí v podobě vlastnosti primitivní typ nebo jiné komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="29c63-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="29c63-112">Existují však některé hlavní rozdíly mezi typy entit a komplexní typy:</span><span class="sxs-lookup"><span data-stu-id="29c63-112">However, there are some key differences between complex types and entity types:</span></span>  
  
-   <span data-ttu-id="29c63-113">Komplexní typy nemají identit a proto nemůže existovat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="29c63-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="29c63-114">Komplexní typy může existovat pouze jako vlastnosti na typy entit a jiné komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="29c63-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
-   <span data-ttu-id="29c63-115">Komplexní typy nemůže se podílet na [přidružení](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="29c63-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="29c63-116">Ani konec přidružení může být komplexního typu a proto [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) nelze definovat na komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="29c63-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29c63-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="29c63-117">Example</span></span>  
 <span data-ttu-id="29c63-118">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="29c63-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="29c63-119">Následující CSDL definuje komplexní typ, adresu, s vlastnostmi primitivní typ `StreetAddress`, `City`, `StateOrProvince`, `Country`, a `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="29c63-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="29c63-120">Chcete-li definovat komplexní typ `Address` (nahoře) jako vlastnost na typ entity, je potřeba deklarovat vlastnost typu v definici typu entity.</span><span class="sxs-lookup"><span data-stu-id="29c63-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="29c63-121">Následující CSDL deklaruje `Address` vlastnost jako komplexní typ. na typ entity (vydavatel):</span><span class="sxs-lookup"><span data-stu-id="29c63-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="29c63-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="29c63-122">See Also</span></span>  
 [<span data-ttu-id="29c63-123">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="29c63-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="29c63-124">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="29c63-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
