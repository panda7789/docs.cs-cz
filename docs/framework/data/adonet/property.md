---
title: property
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: d1e20a6570c458041ec5d8ececbfa291ca9e4612
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735391"
---
# <a name="property"></a><span data-ttu-id="038dc-102">property</span><span class="sxs-lookup"><span data-stu-id="038dc-102">property</span></span>
<span data-ttu-id="038dc-103">*Vlastnosti* jsou základní stavební bloky [typů entit](entity-type.md) a [komplexních typů](complex-type.md).</span><span class="sxs-lookup"><span data-stu-id="038dc-103">*Properties* are the fundamental building blocks of [entity types](entity-type.md) and [complex types](complex-type.md).</span></span> <span data-ttu-id="038dc-104">Vlastnosti definují tvar a vlastnosti dat, které bude obsahovat instance typu entity nebo instance komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="038dc-104">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="038dc-105">Vlastnosti v koncepčním modelu jsou analogické k vlastnostem definovaným pro třídu.</span><span class="sxs-lookup"><span data-stu-id="038dc-105">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="038dc-106">Stejně jako vlastnosti třídy definují tvar třídy a přenášejí informace o objektech, vlastnosti v koncepčním modelu definují tvar typu entity a přenášejí informace o instancích typu entity.</span><span class="sxs-lookup"><span data-stu-id="038dc-106">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="038dc-107">Vlastnosti, jak je popsáno v tomto tématu, se liší od vlastností navigace.</span><span class="sxs-lookup"><span data-stu-id="038dc-107">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="038dc-108">Další informace najdete v tématu [vlastnosti navigace](navigation-property.md).</span><span class="sxs-lookup"><span data-stu-id="038dc-108">For more information, see [navigation properties](navigation-property.md).</span></span>  
  
 <span data-ttu-id="038dc-109">Definice vlastnosti obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="038dc-109">A property definition contains the following information:</span></span>  
  
- <span data-ttu-id="038dc-110">Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="038dc-110">A property name.</span></span> <span data-ttu-id="038dc-111">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="038dc-111">(Required)</span></span>  
  
- <span data-ttu-id="038dc-112">Typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="038dc-112">A property type.</span></span> <span data-ttu-id="038dc-113">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="038dc-113">(Required)</span></span>  
  
- <span data-ttu-id="038dc-114">Sada [omezujících vlastností](facet.md).</span><span class="sxs-lookup"><span data-stu-id="038dc-114">A set of [facets](facet.md).</span></span> <span data-ttu-id="038dc-115">Volitelné</span><span class="sxs-lookup"><span data-stu-id="038dc-115">(Optional)</span></span>  
  
 <span data-ttu-id="038dc-116">Vlastnost může obsahovat primitivní data (například řetězec, celé číslo nebo logickou hodnotu) nebo strukturovaná data (například komplexní typ).</span><span class="sxs-lookup"><span data-stu-id="038dc-116">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="038dc-117">Vlastnosti primitivního typu jsou označovány také jako skalární vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="038dc-117">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="038dc-118">Další informace naleznete v tématu [model EDM (Entity Data Model): primitivní datové typy](entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="038dc-118">For more information, see [Entity Data Model: Primitive Data Types](entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="038dc-119">Komplexní typ může sám sebe mít vlastnosti, které jsou komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="038dc-119">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="038dc-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="038dc-120">Example</span></span>  
 <span data-ttu-id="038dc-121">Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher`a `Author`.</span><span class="sxs-lookup"><span data-stu-id="038dc-121">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="038dc-122">Každý typ entity má několik vlastností, i když informace o typech jednotlivých vlastností nejsou v diagramu předány.</span><span class="sxs-lookup"><span data-stu-id="038dc-122">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="038dc-123">Vlastnosti, které jsou [klíče entit](entity-key.md) , se označuje jako (klíč).</span><span class="sxs-lookup"><span data-stu-id="038dc-123">Properties that are [entity keys](entity-key.md) are denoted with (Key).</span></span>  
  
 ![Vzorový model se třemi typy entit](./media/property/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="038dc-125">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="038dc-125">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="038dc-126">Následující soubor CSDL definuje typ entity `Book` (jak je znázorněno v diagramu výše) a označuje typ a název každé vlastnosti pomocí atributů XML.</span><span class="sxs-lookup"><span data-stu-id="038dc-126">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="038dc-127">Volitelná omezující vlastnost, `Nullable`, je definována také pomocí atributu XML.</span><span class="sxs-lookup"><span data-stu-id="038dc-127">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="038dc-128">Je možné, že jedna z vlastností zobrazených v diagramu je vlastnost komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="038dc-128">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="038dc-129">Například vlastnost `Address` v typu entity `Publisher` by mohla být vlastnost komplexního typu složená z několika skalárních vlastností, jako jsou například `StreetAddress`, `City`, `StateOrProvince`, `Country`a `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="038dc-129">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="038dc-130">Reprezentace typu CSDL takového komplexního typu by vypadala takto:</span><span class="sxs-lookup"><span data-stu-id="038dc-130">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="038dc-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="038dc-131">See also</span></span>

- [<span data-ttu-id="038dc-132">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="038dc-132">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="038dc-133">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="038dc-133">Entity Data Model</span></span>](entity-data-model.md)
