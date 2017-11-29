---
title: "Sada přidružení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db293cbc636d0ae4e532f24b2852444395f603c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="association-set"></a><span data-ttu-id="b967c-102">Sada přidružení</span><span class="sxs-lookup"><span data-stu-id="b967c-102">association set</span></span>
<span data-ttu-id="b967c-103">*Sadu přidružení* je logický kontejner pro [přidružení](../../../../docs/framework/data/adonet/association-type.md) instance stejného typu.</span><span class="sxs-lookup"><span data-stu-id="b967c-103">An *association set* is a logical container for [association](../../../../docs/framework/data/adonet/association-type.md) instances of the same type.</span></span> <span data-ttu-id="b967c-104">Sadu přidružení není dat modelování konstrukce; nepopisuje tedy strukturu dat nebo vztahy.</span><span class="sxs-lookup"><span data-stu-id="b967c-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="b967c-105">Místo toho sadu přidružení poskytuje konstrukt pro hostování nebo úložiště prostředí (například databáze SQL serveru nebo modul common language runtime) k instancím přidružení skupiny, které může být namapovaný na úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="b967c-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="b967c-106">Sadu přidružení je definována v rámci [kontejneru entit](../../../../docs/framework/data/adonet/entity-container.md), což je logické seskupení [sad entit](../../../../docs/framework/data/adonet/entity-set.md) a nastaví přidružení.</span><span class="sxs-lookup"><span data-stu-id="b967c-106">An association set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="b967c-107">Definice pro sadu přidružení obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="b967c-107">A definition for an association set contains the following information:</span></span>  
  
-   <span data-ttu-id="b967c-108">Název sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="b967c-108">The association set name.</span></span> <span data-ttu-id="b967c-109">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="b967c-109">(Required)</span></span>  
  
-   <span data-ttu-id="b967c-110">Přidružení, které bude obsahovat instancí.</span><span class="sxs-lookup"><span data-stu-id="b967c-110">The association of which it will contain instances.</span></span> <span data-ttu-id="b967c-111">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="b967c-111">(Required)</span></span>  
  
-   <span data-ttu-id="b967c-112">Dva [končí nastavená přidružení](../../../../docs/framework/data/adonet/association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="b967c-112">Two [association set ends](../../../../docs/framework/data/adonet/association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b967c-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b967c-113">Example</span></span>  
 <span data-ttu-id="b967c-114">Následující diagram znázorňuje Koncepční model se dvě přidružení: `PublishedBy`, a `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="b967c-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="b967c-115">I když v diagramu není bude předávat informace o přidružení sady, další diagram ukazuje příklad sady přidružení a sad entit na základě tohoto modelu.</span><span class="sxs-lookup"><span data-stu-id="b967c-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 <span data-ttu-id="b967c-116">![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="b967c-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="b967c-117">Následující příklad ukazuje sadu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) na základě konceptuálního modelu uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="b967c-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="b967c-118">BI v `Books` sady entit představuje instanci `Book` typ entity v době běhu.</span><span class="sxs-lookup"><span data-stu-id="b967c-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="b967c-119">Podobně, představuje Pj `Publisher` instance v `Publishers` sady entit.</span><span class="sxs-lookup"><span data-stu-id="b967c-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="b967c-120">BiPj představuje instanci `PublishedBy` přidružení v `PublishedBy` sadu přidružení.</span><span class="sxs-lookup"><span data-stu-id="b967c-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="b967c-121">![Nastaví příklad](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="b967c-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="b967c-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="b967c-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="b967c-123">Následující CSDL definuje jednu sadu pro každé přidružení v diagramu výše přidružení kontejner entity.</span><span class="sxs-lookup"><span data-stu-id="b967c-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="b967c-124">Všimněte si, že název a přidružení pro každé přidružení nastavit jsou definovány pomocí atributy XML.</span><span class="sxs-lookup"><span data-stu-id="b967c-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="b967c-125">Je možné definovat několik sad přidružení na přidružení, stejně dlouho jako žádná sdílená složka sady dvě přidružení [nastavená přidružení end](../../../../docs/framework/data/adonet/association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="b967c-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](../../../../docs/framework/data/adonet/association-set-end.md).</span></span> <span data-ttu-id="b967c-126">Následující CSDL definuje kontejner entity dvě sady přidružení pro `WrittenBy` přidružení.</span><span class="sxs-lookup"><span data-stu-id="b967c-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="b967c-127">Všimněte si, že se definovaly několik sad entit `Book` a `Author` typy entit a nastavit žádné přidružení sdílené složky přidružení nastavit end.</span><span class="sxs-lookup"><span data-stu-id="b967c-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="b967c-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="b967c-128">See Also</span></span>  
 [<span data-ttu-id="b967c-129">Entity Data Model klíčové koncepty</span><span class="sxs-lookup"><span data-stu-id="b967c-129">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="b967c-130">Datového modelu entity</span><span class="sxs-lookup"><span data-stu-id="b967c-130">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="b967c-131">vlastností cizího klíče</span><span class="sxs-lookup"><span data-stu-id="b967c-131">foreign key property</span></span>](../../../../docs/framework/data/adonet/foreign-key-property.md)
