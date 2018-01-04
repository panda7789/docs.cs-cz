---
title: "násobnost end přidružení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0d66c141b83402b011fdebbb04c0b2a9adc5ec29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="f9306-102">násobnost end přidružení</span><span class="sxs-lookup"><span data-stu-id="f9306-102">association end multiplicity</span></span>
<span data-ttu-id="f9306-103">*Násobnost end přidružení* definuje počet [typ entity](../../../../docs/framework/data/adonet/entity-type.md) instancí, které můžou být v jednom konci [přidružení](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="f9306-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="f9306-104">Násobnost end přidružení může mít jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="f9306-104">An association end multiplicity can have one of the following values:</span></span>  
  
-   <span data-ttu-id="f9306-105">jedna (1): Určuje tuto instanci typu přesně jedna entita existuje na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="f9306-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
-   <span data-ttu-id="f9306-106">nula nebo jeden (0..1): udává, že existuje žádnou nebo jednu instance typu entity na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="f9306-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
-   <span data-ttu-id="f9306-107">Mnoho (*): udává, že existuje nula, jednu nebo více instancí typu entity na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="f9306-107">many (*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="f9306-108">Přidružení je často charakterizovaná jeho Násobnosti zakončení přidružení.</span><span class="sxs-lookup"><span data-stu-id="f9306-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="f9306-109">Například pokud konce přidružení mnohočetnostmi jedna (1) a mnoho (*), se nazývá přidružení na více přidružení.</span><span class="sxs-lookup"><span data-stu-id="f9306-109">For example, if the ends of an association have multiplicities one (1) and many (*), the association is called a one-to-many association.</span></span> <span data-ttu-id="f9306-110">V následujícím příkladu `PublishedBy` přidružení je to přidružení k více (vydavatel publikuje mnoho knihy a publikování knihy se jeden vydavatelem).</span><span class="sxs-lookup"><span data-stu-id="f9306-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="f9306-111">`WrittenBy` Association je m: n přidružení (knihy, může mít několik autoři a Autor může zapisovat více knih).</span><span class="sxs-lookup"><span data-stu-id="f9306-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9306-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9306-112">Example</span></span>  
 <span data-ttu-id="f9306-113">Následující diagram znázorňuje Koncepční model se dvě přidružení: `PublishedBy` a `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="f9306-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="f9306-114">Přidružení končí pro `PublishedBy` jsou přidružení `Book` a `Publisher` typy entit.</span><span class="sxs-lookup"><span data-stu-id="f9306-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="f9306-115">Násobnost `Publisher` koncový je jedna (1) a násobnost `Book` koncový je mnoho (*).</span><span class="sxs-lookup"><span data-stu-id="f9306-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (*).</span></span>  
  
 <span data-ttu-id="f9306-116">![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="f9306-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="f9306-117">ADO.NET Entity Framework používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="f9306-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="f9306-118">Definuje následující CSDL `PublishedBy` přidružení vidět v diagramu výše:</span><span class="sxs-lookup"><span data-stu-id="f9306-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="f9306-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9306-119">See Also</span></span>  
 [<span data-ttu-id="f9306-120">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="f9306-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="f9306-121">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="f9306-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
