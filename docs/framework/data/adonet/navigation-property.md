---
title: "navigační vlastnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dc980a2c61be736e2c1d8e52d8f13d0ea5ed09f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="navigation-property"></a><span data-ttu-id="55e03-102">navigační vlastnost</span><span class="sxs-lookup"><span data-stu-id="55e03-102">navigation property</span></span>
<span data-ttu-id="55e03-103">A *navigační vlastnost* je volitelná vlastnost na [typ entity](../../../../docs/framework/data/adonet/entity-type.md) umožňuje pro navigaci z jednoho [end](../../../../docs/framework/data/adonet/association-end.md) z [přidružení](../../../../docs/framework/data/adonet/association-type.md) na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="55e03-103">A *navigation property* is an optional property on an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that allows for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="55e03-104">Na rozdíl od jiných [vlastnosti](../../../../docs/framework/data/adonet/property.md), navigačních vlastností nepřenášejí data.</span><span class="sxs-lookup"><span data-stu-id="55e03-104">Unlike other [properties](../../../../docs/framework/data/adonet/property.md), navigation properties do not carry data.</span></span>  
  
 <span data-ttu-id="55e03-105">Navigační vlastnost definice zahrnuje následující položky:</span><span class="sxs-lookup"><span data-stu-id="55e03-105">A navigation property definition includes the following:</span></span>  
  
-   <span data-ttu-id="55e03-106">Název.</span><span class="sxs-lookup"><span data-stu-id="55e03-106">A name.</span></span> <span data-ttu-id="55e03-107">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="55e03-107">(Required)</span></span>  
  
-   <span data-ttu-id="55e03-108">Přidružení, který se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="55e03-108">The association that it navigates.</span></span> <span data-ttu-id="55e03-109">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="55e03-109">(Required)</span></span>  
  
-   <span data-ttu-id="55e03-110">Elementy end přidružení, který se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="55e03-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="55e03-111">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="55e03-111">(Required)</span></span>  
  
 <span data-ttu-id="55e03-112">Všimněte si, že jsou volitelné na oba typy entit na koncích přidružení navigační vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="55e03-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="55e03-113">Pokud definujete navigační vlastnost u jednoho typu entity na konci tohoto přidružení, nemáte definovat navigační vlastnost typu entity na druhém konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="55e03-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>  
  
 <span data-ttu-id="55e03-114">Datový typ vlastnosti navigace je dáno [násobnost](../../../../docs/framework/data/adonet/association-end-multiplicity.md) jeho vzdálené [end přidružení](../../../../docs/framework/data/adonet/association-end.md).</span><span class="sxs-lookup"><span data-stu-id="55e03-114">The data type of a navigation property is determined by the [multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) of its remote [association end](../../../../docs/framework/data/adonet/association-end.md).</span></span> <span data-ttu-id="55e03-115">Předpokládejme například, navigační vlastnost `OrdersNavProp`, existuje na `Customer` typu entity a přejde na více přidružení mezi `Customer` a `Order`.</span><span class="sxs-lookup"><span data-stu-id="55e03-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="55e03-116">Protože end vzdáleného přidružení pro navigační vlastnost má násobnost mnoho (*), je jeho datový typ kolekce (z `Order`).</span><span class="sxs-lookup"><span data-stu-id="55e03-116">Because the remote association end for the navigation property has multiplicity of many (*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="55e03-117">Podobně, pokud navigační vlastnost `CustomerNavProp`, existuje na `Order` typ entity, bude jeho datového typu `Customer`, protože násobnost konce vzdálené je jedna (1).</span><span class="sxs-lookup"><span data-stu-id="55e03-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55e03-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="55e03-118">Example</span></span>  
 <span data-ttu-id="55e03-119">Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`.</span><span class="sxs-lookup"><span data-stu-id="55e03-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="55e03-120">Navigační vlastnosti `Publisher` a `Authors`, jsou definovány na typ entity adresáře.</span><span class="sxs-lookup"><span data-stu-id="55e03-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="55e03-121">Navigační vlastnost `Books` je definována obě vydavatele typu entity a `Author` typ entity.</span><span class="sxs-lookup"><span data-stu-id="55e03-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>  
  
 <span data-ttu-id="55e03-122">![Modelu s navigační vlastnosti](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span><span class="sxs-lookup"><span data-stu-id="55e03-122">![Model with Navigation Properties](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span></span>  
  
 <span data-ttu-id="55e03-123">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="55e03-123">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="55e03-124">Definuje následující CSDL `Book` typ entity, které jsou uvedené v diagramu výše:</span><span class="sxs-lookup"><span data-stu-id="55e03-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="55e03-125">Všimněte si, že XML atributy se používají ke komunikaci informace potřebné k definování navigační vlastnost: atribut `Name` obsahuje název vlastnosti, `Relationship` obsahuje název tohoto přidružení se odkazuje, a `FromRole` a `ToRole` obsahovat konce přidružení.</span><span class="sxs-lookup"><span data-stu-id="55e03-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55e03-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="55e03-126">See Also</span></span>  
 [<span data-ttu-id="55e03-127">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="55e03-127">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="55e03-128">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="55e03-128">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
