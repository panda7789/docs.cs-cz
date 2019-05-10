---
title: complex type
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: a6a7190a144280930d67f179373f29f6b19e98cc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583665"
---
# <a name="complex-type"></a><span data-ttu-id="50af2-102">complex type</span><span class="sxs-lookup"><span data-stu-id="50af2-102">complex type</span></span>
<span data-ttu-id="50af2-103">A *komplexní typ* je šablonu pro definování bohatých a strukturované vlastnosti na [typy entit](../../../../docs/framework/data/adonet/entity-type.md) nebo jiné komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="50af2-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="50af2-104">Každá šablona obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="50af2-104">Each template contains the following:</span></span>  
  
- <span data-ttu-id="50af2-105">Jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="50af2-105">A unique name.</span></span> <span data-ttu-id="50af2-106">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="50af2-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50af2-107">Název komplexního typu nemůže být stejný jako název typu entity v rámci stejného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="50af2-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="50af2-108">Data ve formě jednoho nebo více [vlastnosti](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="50af2-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="50af2-109">(Volitelné).</span><span class="sxs-lookup"><span data-stu-id="50af2-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50af2-110">Vlastnost komplexní typ může být jiného komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="50af2-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="50af2-111">Komplexní typ je podobný typ entity, komplexní typ mohou obsahovat datové ve formě vlastnosti primitivní typ nebo jiné komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="50af2-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="50af2-112">Existují však některé hlavní rozdíly mezi typy entit a komplexní typy:</span><span class="sxs-lookup"><span data-stu-id="50af2-112">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="50af2-113">Komplexní typy není identity a proto nemůže existovat nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="50af2-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="50af2-114">Komplexní typy může existovat pouze jako vlastnosti na typy entit nebo jiné komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="50af2-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="50af2-115">Komplexní typy se nemůže podílet na [přidružení](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="50af2-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="50af2-116">Ani jedna end přidružení může být komplexní typ a proto [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) nelze zadat u komplexních typů.</span><span class="sxs-lookup"><span data-stu-id="50af2-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50af2-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="50af2-117">Example</span></span>  
 <span data-ttu-id="50af2-118">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů.</span><span class="sxs-lookup"><span data-stu-id="50af2-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="50af2-119">Komplexní typ, adresa, s vlastnostmi primitivní typ definuje následující CSDL `StreetAddress`, `City`, `StateOrProvince`, `Country`, a `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="50af2-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="50af2-120">Chcete-li definovat komplexní typ `Address` (výše) jako vlastnost v typu entity, je třeba deklarovat typ vlastnosti v definici typu entity.</span><span class="sxs-lookup"><span data-stu-id="50af2-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="50af2-121">Deklaruje následující CSDL `Address` vlastnost jako komplexní typ na typ entity (vydavatel):</span><span class="sxs-lookup"><span data-stu-id="50af2-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="50af2-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50af2-122">See also</span></span>

- [<span data-ttu-id="50af2-123">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="50af2-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="50af2-124">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="50af2-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
