---
title: complex type
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 0d9b8efd08cc0dfba5b26a70773b614b0d63d74f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786757"
---
# <a name="complex-type"></a><span data-ttu-id="73444-102">complex type</span><span class="sxs-lookup"><span data-stu-id="73444-102">complex type</span></span>
<span data-ttu-id="73444-103">*Komplexní typ* je šablona pro definování bohatě strukturovaných vlastností na [typech entit](entity-type.md) nebo na jiných komplexních typech.</span><span class="sxs-lookup"><span data-stu-id="73444-103">A *complex type* is a template for defining rich, structured properties on [entity types](entity-type.md) or on other complex types.</span></span> <span data-ttu-id="73444-104">Každá šablona obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="73444-104">Each template contains the following:</span></span>  
  
- <span data-ttu-id="73444-105">Jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="73444-105">A unique name.</span></span> <span data-ttu-id="73444-106">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="73444-106">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="73444-107">Název komplexního typu nemůže být stejný jako název typu entity v rámci stejného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="73444-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="73444-108">Data ve formě jedné nebo více [vlastností](property.md).</span><span class="sxs-lookup"><span data-stu-id="73444-108">Data in the form of one or more [properties](property.md).</span></span> <span data-ttu-id="73444-109">(Volitelné.)</span><span class="sxs-lookup"><span data-stu-id="73444-109">(Optional.)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="73444-110">Vlastnost komplexního typu může být jiný komplexní typ.</span><span class="sxs-lookup"><span data-stu-id="73444-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="73444-111">Komplexní typ je podobný jako typ entity v tom, že komplexní typ může mít datovou datovou část ve formě vlastností primitivního typu nebo jiných komplexních typů.</span><span class="sxs-lookup"><span data-stu-id="73444-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="73444-112">Existují však některé klíčové rozdíly mezi komplexními typy a typy entit:</span><span class="sxs-lookup"><span data-stu-id="73444-112">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="73444-113">Komplexní typy nemají identity, a proto nemohou existovat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="73444-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="73444-114">Komplexní typy mohou existovat pouze jako vlastnosti u typů entit nebo jiných komplexních typů.</span><span class="sxs-lookup"><span data-stu-id="73444-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="73444-115">Komplexní typy se nemůžou účastnit [přidružení](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="73444-115">Complex types cannot participate in [associations](association-type.md).</span></span> <span data-ttu-id="73444-116">Ani konec přidružení může být komplexní typ, a proto nelze definovat [vlastnosti navigace](navigation-property.md) pro komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="73444-116">Neither end of an association can be a complex type, and therefore [navigation properties](navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73444-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="73444-117">Example</span></span>  
 <span data-ttu-id="73444-118">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="73444-118">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="73444-119">Následující CSDL definuje komplexní typ, adresu `StreetAddress`s vlastnostmi `City` `StateOrProvince` `Country`primitivního typu,,, a `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="73444-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="73444-120">Chcete-li definovat komplexní `Address` typ (výše) jako vlastnost typu entity, je nutné deklarovat typ vlastnosti v definici typu entity.</span><span class="sxs-lookup"><span data-stu-id="73444-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="73444-121">Následující CSDL deklaruje `Address` vlastnost jako komplexní typ pro typ entity (Publisher):</span><span class="sxs-lookup"><span data-stu-id="73444-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="73444-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73444-122">See also</span></span>

- [<span data-ttu-id="73444-123">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="73444-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="73444-124">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="73444-124">Entity Data Model</span></span>](entity-data-model.md)
