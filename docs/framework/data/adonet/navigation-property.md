---
title: Navigační vlastnost – ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 6729b22dbc012d5ccfabd64cd83b710833fe1b9d
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857941"
---
# <a name="navigation-property"></a><span data-ttu-id="5ee5f-102">Navigační vlastnost</span><span class="sxs-lookup"><span data-stu-id="5ee5f-102">Navigation property</span></span>

<span data-ttu-id="5ee5f-103">A *navigační vlastnost* vlastnost je volitelná na [typ entity](entity-type.md) , který umožňuje navigace z jednoho [end](association-end.md) z [přidružení](association-type.md) do druhém konci.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-103">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="5ee5f-104">Na rozdíl od jiných [vlastnosti](property.md), navigačních vlastností není vázané na data.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-104">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="5ee5f-105">Definice vlastnosti navigace zahrnuje následující položky:</span><span class="sxs-lookup"><span data-stu-id="5ee5f-105">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="5ee5f-106">Název.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-106">A name.</span></span> <span data-ttu-id="5ee5f-107">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="5ee5f-107">(Required)</span></span>

- <span data-ttu-id="5ee5f-108">Přidružení, na kterou se přejde.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-108">The association that it navigates.</span></span> <span data-ttu-id="5ee5f-109">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="5ee5f-109">(Required)</span></span>

- <span data-ttu-id="5ee5f-110">Elementy end přidružení, na kterou se přejde.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="5ee5f-111">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="5ee5f-111">(Required)</span></span>

<span data-ttu-id="5ee5f-112">Všimněte si, že jsou volitelné na oba typy entit na konci asociace navigační vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="5ee5f-113">Pokud definujete navigační vlastnost jednoho typu entity na konci asociace, není nutné definovat vlastnost navigace typu entity na druhém konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="5ee5f-114">Datový typ vlastnosti navigace závisí [násobnost](association-end-multiplicity.md) jeho vzdáleného [end přidružení](association-end.md).</span><span class="sxs-lookup"><span data-stu-id="5ee5f-114">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="5ee5f-115">Předpokládejme například, vlastnost navigace, `OrdersNavProp`, existuje na `Customer` typu entity a přejde na více přidružení mezi `Customer` a `Order`.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="5ee5f-116">Protože ukončení vzdálené přidružení pro navigační vlastnost má násobnost mnoha (\*), jeho datový typ je kolekce (z `Order`).</span><span class="sxs-lookup"><span data-stu-id="5ee5f-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="5ee5f-117">Podobně, pokud vlastnost navigace, `CustomerNavProp`, existuje na `Order` typ entity, jeho datový typ by `Customer`, protože vzdáleným koncem násobnost je jedna (1).</span><span class="sxs-lookup"><span data-stu-id="5ee5f-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="5ee5f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ee5f-118">Example</span></span>

<span data-ttu-id="5ee5f-119">Následující diagram znázorňuje Koncepční model s tři typy entit: `Book`, `Publisher`, a `Author`.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="5ee5f-120">Vlastnosti navigace `Publisher` a `Authors`, jsou definovány na typ entity adresáře.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="5ee5f-121">Navigační vlastnost `Books` je definována obě vydavatele typu entity a `Author` typ entity.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

<span data-ttu-id="5ee5f-122">![Model s navigační vlastnosti](/media/modelwithnavprops.gif "ModelWithNavProps")</span><span class="sxs-lookup"><span data-stu-id="5ee5f-122">![Model with Navigation Properties](/media/modelwithnavprops.gif "ModelWithNavProps")</span></span>

<span data-ttu-id="5ee5f-123">[ADO.NET Entity Framework](./ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](./ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="5ee5f-124">Definuje následující CSDL `Book` typ entity, které jsou zobrazeny ve výše uvedeném diagramu:</span><span class="sxs-lookup"><span data-stu-id="5ee5f-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="5ee5f-125">Všimněte si, že atributy ve formátu XML se používají ke komunikaci informace potřebné k definování navigační vlastnost: Atribut `Name` obsahuje název vlastnosti, `Relationship` obsahuje název přidružení se odkazuje, a `FromRole` a `ToRole` obsahovat elementy end přidružení.</span><span class="sxs-lookup"><span data-stu-id="5ee5f-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ee5f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ee5f-126">See also</span></span>

- [<span data-ttu-id="5ee5f-127">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="5ee5f-127">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="5ee5f-128">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="5ee5f-128">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="5ee5f-129">Relace, navigačních vlastností a cizí klíče</span><span class="sxs-lookup"><span data-stu-id="5ee5f-129">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
