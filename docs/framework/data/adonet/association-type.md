---
title: "Typ přidružení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5349889017ea23701a17a92947d9750610a52f59
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="association-type"></a><span data-ttu-id="ae09f-102">Typ přidružení</span><span class="sxs-lookup"><span data-stu-id="ae09f-102">association type</span></span>
<span data-ttu-id="ae09f-103">*Typ přidružení* (také nazývané přidružení) je základní stavební blok pro popisující vztahy v Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="ae09f-103">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="ae09f-104">V konceptuálním modelu přidružení představuje vztah mezi dvěma [typy entit](../../../../docs/framework/data/adonet/entity-type.md) (například `Customer` a `Order`).</span><span class="sxs-lookup"><span data-stu-id="ae09f-104">In a conceptual model, an association represents a relationship between two [entity types](../../../../docs/framework/data/adonet/entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="ae09f-105">V aplikaci, představuje instanci přidružení konkrétní přidružení (jako je například přidružení mezi instanci `Customer` a instance `Order`).</span><span class="sxs-lookup"><span data-stu-id="ae09f-105">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="ae09f-106">Přidružení instance jsou logicky seskupeny do [sadu přidružení](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="ae09f-106">Association instances are logically grouped in an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="ae09f-107">Přidružení definice obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="ae09f-107">An association definition contains the following information:</span></span>  
  
-   <span data-ttu-id="ae09f-108">Jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="ae09f-108">A unique name.</span></span> <span data-ttu-id="ae09f-109">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="ae09f-109">(Required)</span></span>  
  
-   <span data-ttu-id="ae09f-110">Dva [zakončení přidružení](../../../../docs/framework/data/adonet/association-end.md), jednu pro každý typ entity v relaci.</span><span class="sxs-lookup"><span data-stu-id="ae09f-110">Two [association ends](../../../../docs/framework/data/adonet/association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="ae09f-111">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="ae09f-111">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ae09f-112">Přidružení nemůže představují vztah mezi více než dva typy entit.</span><span class="sxs-lookup"><span data-stu-id="ae09f-112">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="ae09f-113">Přidružení můžete, ale taky definovat vztah samoobslužné tak, že zadáte stejný typ entity pro každou z konců přidružení.</span><span class="sxs-lookup"><span data-stu-id="ae09f-113">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
-   <span data-ttu-id="ae09f-114">A [omezení referenční integrity](../../../../docs/framework/data/adonet/referential-integrity-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="ae09f-114">A [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md).</span></span> <span data-ttu-id="ae09f-115">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="ae09f-115">(Optional)</span></span>  
  
 <span data-ttu-id="ae09f-116">Musíte zadat každou end přidružení [násobnost end přidružení](../../../../docs/framework/data/adonet/association-end-multiplicity.md) určující počet instancí typ entity, které mohou být na jednom konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="ae09f-116">Each association end must specify an [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="ae09f-117">Násobnost end přidružení může mít hodnotu jedna (1), žádnou nebo jednu (0..1), nebo mnoho (\*).</span><span class="sxs-lookup"><span data-stu-id="ae09f-117">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="ae09f-118">Instance typu entity na jednom konci přidružení je možné přistupovat prostřednictvím [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) nebo cizího klíče, pokud jsou zveřejněné na typ entity.</span><span class="sxs-lookup"><span data-stu-id="ae09f-118">Entity type instances at one end of an association can be accessed through [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="ae09f-119">Další informace najdete v tématu [datového modelu Entity: cizí klíče](../../../../docs/framework/data/adonet/foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="ae09f-119">For more information, see [Entity Data Model: Foreign Keys](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae09f-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae09f-120">Example</span></span>  
 <span data-ttu-id="ae09f-121">Následující diagram znázorňuje Koncepční model se dvě přidružení: `PublishedBy` a `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="ae09f-121">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="ae09f-122">Přidružení končí pro `PublishedBy` jsou přidružení `Book` a `Publisher` typy entit.</span><span class="sxs-lookup"><span data-stu-id="ae09f-122">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="ae09f-123">Násobnost `Publisher` koncový je jedna (1) a násobnosti atributu `Book` koncový je mnoho (\*), označující, že vydavatel publikuje mnoho knihy a publikování knihy se jeden vydavatelem.</span><span class="sxs-lookup"><span data-stu-id="ae09f-123">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 <span data-ttu-id="ae09f-124">![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="ae09f-124">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="ae09f-125">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="ae09f-125">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ae09f-126">Definuje následující CSDL `PublishedBy` přidružení vidět v diagramu výše:</span><span class="sxs-lookup"><span data-stu-id="ae09f-126">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="ae09f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae09f-127">See Also</span></span>  
 [<span data-ttu-id="ae09f-128">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="ae09f-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="ae09f-129">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="ae09f-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
