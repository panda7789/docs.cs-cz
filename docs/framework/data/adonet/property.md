---
title: property
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c052c53488fde0ea767a46f51ef349dd6a7d2766
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="property"></a><span data-ttu-id="99fd3-102">property</span><span class="sxs-lookup"><span data-stu-id="99fd3-102">property</span></span>
<span data-ttu-id="99fd3-103">*Vlastnosti* jsou základní stavební kameny [typy entit](../../../../docs/framework/data/adonet/entity-type.md) a [komplexní typy](../../../../docs/framework/data/adonet/complex-type.md).</span><span class="sxs-lookup"><span data-stu-id="99fd3-103">*Properties* are the fundamental building blocks of [entity types](../../../../docs/framework/data/adonet/entity-type.md) and [complex types](../../../../docs/framework/data/adonet/complex-type.md).</span></span> <span data-ttu-id="99fd3-104">Vlastnosti definovat tvar a vlastnosti dat, která bude obsahovat instance typu entity nebo komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="99fd3-104">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="99fd3-105">Vlastnosti v konceptuálním modelu jsou podobná vlastnosti definované na třídu.</span><span class="sxs-lookup"><span data-stu-id="99fd3-105">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="99fd3-106">Stejným způsobem, že vlastnosti třídy definovat tvaru třídy a provádění informace o objektech vlastnosti v konceptuálním modelu definovat obrazce typu entity a provádění informace o instancích typu entity.</span><span class="sxs-lookup"><span data-stu-id="99fd3-106">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99fd3-107">Vlastnosti, jak je popsáno v tomto tématu se liší od navigační vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99fd3-107">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="99fd3-108">Další informace najdete v tématu [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md).</span><span class="sxs-lookup"><span data-stu-id="99fd3-108">For more information, see [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md).</span></span>  
  
 <span data-ttu-id="99fd3-109">Definici vlastnosti obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="99fd3-109">A property definition contains the following information:</span></span>  
  
-   <span data-ttu-id="99fd3-110">Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99fd3-110">A property name.</span></span> <span data-ttu-id="99fd3-111">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="99fd3-111">(Required)</span></span>  
  
-   <span data-ttu-id="99fd3-112">Typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99fd3-112">A property type.</span></span> <span data-ttu-id="99fd3-113">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="99fd3-113">(Required)</span></span>  
  
-   <span data-ttu-id="99fd3-114">Sadu [omezující vlastnosti](../../../../docs/framework/data/adonet/facet.md).</span><span class="sxs-lookup"><span data-stu-id="99fd3-114">A set of [facets](../../../../docs/framework/data/adonet/facet.md).</span></span> <span data-ttu-id="99fd3-115">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="99fd3-115">(Optional)</span></span>  
  
 <span data-ttu-id="99fd3-116">Vlastnost může obsahovat primitivní datové (například řetězec, celé číslo nebo logická hodnota) nebo strukturovaná data (například komplexního typu).</span><span class="sxs-lookup"><span data-stu-id="99fd3-116">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="99fd3-117">Vlastnosti, které jsou primitivního typu se také označují jako skalární vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99fd3-117">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="99fd3-118">Další informace najdete v tématu [datového modelu Entity: primitivní datové typy](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="99fd3-118">For more information, see [Entity Data Model: Primitive Data Types](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99fd3-119">Komplexní typ můžou mít sama, vlastnosti, které jsou komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="99fd3-119">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99fd3-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="99fd3-120">Example</span></span>  
 <span data-ttu-id="99fd3-121">Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`.</span><span class="sxs-lookup"><span data-stu-id="99fd3-121">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="99fd3-122">Každý typ entity má několik vlastností, i když bude v diagramu není předávat informace o typu pro každou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="99fd3-122">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="99fd3-123">Vlastnosti, které jsou [klíče entit](../../../../docs/framework/data/adonet/entity-key.md) , jsou označeny (klíč).</span><span class="sxs-lookup"><span data-stu-id="99fd3-123">Properties that are [entity keys](../../../../docs/framework/data/adonet/entity-key.md) are denoted with (Key).</span></span>  
  
 <span data-ttu-id="99fd3-124">![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="99fd3-124">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="99fd3-125">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="99fd3-125">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="99fd3-126">Definuje následující CSDL `Book` entity zadejte (jak je znázorněno na obrázku výš) a určuje typ a název každé vlastnosti pomocí atributů jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="99fd3-126">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="99fd3-127">Volitelné omezující vlastnosti, `Nullable`, je také definován pomocí atribut XML.</span><span class="sxs-lookup"><span data-stu-id="99fd3-127">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="99fd3-128">Je možné, že jedna z vlastností vidět na obrázku je vlastnost komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="99fd3-128">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="99fd3-129">Například `Address` vlastnost `Publisher` typ entity může být komplexní typ vlastnosti, který se skládá z několika Skalární vlastnosti, jako například `StreetAddress`, `City`, `StateOrProvince`, `Country`, a `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="99fd3-129">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="99fd3-130">Reprezentace CSDL komplexního typu vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="99fd3-130">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="99fd3-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="99fd3-131">See Also</span></span>  
 [<span data-ttu-id="99fd3-132">Entity Data Model klíčové koncepty</span><span class="sxs-lookup"><span data-stu-id="99fd3-132">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="99fd3-133">Datového modelu entity</span><span class="sxs-lookup"><span data-stu-id="99fd3-133">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
