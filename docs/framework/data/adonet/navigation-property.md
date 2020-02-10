---
title: Navigační vlastnost
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: eaf22ad4dd24b4bf046f14ccabd435a9ecd1776f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094381"
---
# <a name="navigation-property"></a><span data-ttu-id="cdde0-102">Navigační vlastnost</span><span class="sxs-lookup"><span data-stu-id="cdde0-102">Navigation property</span></span>

<span data-ttu-id="cdde0-103">*Navigační vlastnost* je volitelnou vlastností u [typu entity](entity-type.md) , která umožňuje navigaci od jednoho [konce](association-end.md) [přidružení](association-type.md) k druhému konci.</span><span class="sxs-lookup"><span data-stu-id="cdde0-103">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="cdde0-104">Na rozdíl od jiných [vlastností](property.md)navigační vlastnosti neobsahují data.</span><span class="sxs-lookup"><span data-stu-id="cdde0-104">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="cdde0-105">Definice navigační vlastnosti zahrnuje následující:</span><span class="sxs-lookup"><span data-stu-id="cdde0-105">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="cdde0-106">Název.</span><span class="sxs-lookup"><span data-stu-id="cdde0-106">A name.</span></span> <span data-ttu-id="cdde0-107">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="cdde0-107">(Required)</span></span>

- <span data-ttu-id="cdde0-108">Přidružení, které naviguje.</span><span class="sxs-lookup"><span data-stu-id="cdde0-108">The association that it navigates.</span></span> <span data-ttu-id="cdde0-109">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="cdde0-109">(Required)</span></span>

- <span data-ttu-id="cdde0-110">Konec přidružení, které naviguje.</span><span class="sxs-lookup"><span data-stu-id="cdde0-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="cdde0-111">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="cdde0-111">(Required)</span></span>

<span data-ttu-id="cdde0-112">Navigační vlastnosti jsou v obou typech entit na koncích přidružení volitelné.</span><span class="sxs-lookup"><span data-stu-id="cdde0-112">Navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="cdde0-113">Definujete-li vlastnost navigace na jednom typu entity na konci přidružení, nemusíte definovat vlastnost navigace na typu entity na druhém konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="cdde0-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="cdde0-114">Datový typ vlastnosti navigace je určen [násobností](association-end-multiplicity.md) jeho vzdáleného [zakončení přidružení](association-end.md).</span><span class="sxs-lookup"><span data-stu-id="cdde0-114">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="cdde0-115">Předpokládejme například, že navigační vlastnost, `OrdersNavProp`, existuje v `Customer` typu entity a přechází mezi `Customer` a `Order`přidružení 1:1.</span><span class="sxs-lookup"><span data-stu-id="cdde0-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="cdde0-116">Vzhledem k tomu, že vzdálené zakončení přidružení pro navigační vlastnost má násobnost mnoho (\*), je jeho datovým typem kolekce (z `Order`).</span><span class="sxs-lookup"><span data-stu-id="cdde0-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="cdde0-117">Podobně platí, že pokud v `Order` typu entity `CustomerNavProp`existuje vlastnost navigace, její datový typ by byl `Customer`, protože násobnost vzdáleného elementu end je jedna (1).</span><span class="sxs-lookup"><span data-stu-id="cdde0-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="cdde0-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdde0-118">Example</span></span>

<span data-ttu-id="cdde0-119">Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher`a `Author`.</span><span class="sxs-lookup"><span data-stu-id="cdde0-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="cdde0-120">Navigační vlastnosti `Publisher` a `Authors` jsou definovány pro typ entity Book.</span><span class="sxs-lookup"><span data-stu-id="cdde0-120">The navigation properties `Publisher` and `Authors` are defined on the Book entity type.</span></span> <span data-ttu-id="cdde0-121">Navigační vlastnost `Books` je definována jak pro typ entity Vydavatel, tak pro typ entity `Author`.</span><span class="sxs-lookup"><span data-stu-id="cdde0-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

![Diagram znázorňující koncepční model se třemi typy entit.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

<span data-ttu-id="cdde0-123">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="cdde0-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="cdde0-124">Následující CSDL definuje typ entity `Book` zobrazený v diagramu výše:</span><span class="sxs-lookup"><span data-stu-id="cdde0-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="cdde0-125">Atributy XML slouží ke sdělování informací nezbytných pro definování navigační vlastnosti: atribut `Name` obsahuje název vlastnosti, `Relationship` obsahuje název přidaného přidružení a `FromRole` a `ToRole` obsahuje konce přidružení.</span><span class="sxs-lookup"><span data-stu-id="cdde0-125">XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdde0-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="cdde0-126">See also</span></span>

- [<span data-ttu-id="cdde0-127">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="cdde0-127">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="cdde0-128">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="cdde0-128">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="cdde0-129">Relace, navigační vlastnosti a cizí klíče</span><span class="sxs-lookup"><span data-stu-id="cdde0-129">Relationships, navigation properties, and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
