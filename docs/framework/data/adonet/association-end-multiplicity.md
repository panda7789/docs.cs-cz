---
title: násobnost end přidružení
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 2f70fa4b163b957ea1e43506033863c3540b0418
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="cb072-102">násobnost end přidružení</span><span class="sxs-lookup"><span data-stu-id="cb072-102">association end multiplicity</span></span>
<span data-ttu-id="cb072-103">*Násobnost end přidružení* definuje počet [typ entity](../../../../docs/framework/data/adonet/entity-type.md) instancí, které můžou být v jednom konci [přidružení](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="cb072-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="cb072-104">Násobnost end přidružení může mít jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="cb072-104">An association end multiplicity can have one of the following values:</span></span>  
  
-   <span data-ttu-id="cb072-105">jedna (1): Určuje tuto instanci typu přesně jedna entita existuje na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="cb072-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
-   <span data-ttu-id="cb072-106">nula nebo jeden (0..1): udává, že existuje žádnou nebo jednu instance typu entity na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="cb072-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
-   <span data-ttu-id="cb072-107">Mnoho (\*): udává, že existuje nula, jednu nebo více instancí typu entity na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="cb072-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="cb072-108">Přidružení je často charakterizovaná jeho Násobnosti zakončení přidružení.</span><span class="sxs-lookup"><span data-stu-id="cb072-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="cb072-109">Například pokud konce přidružení mnohočetnostmi jedna (1) a mnoho (\*), se nazývá přidružení na více přidružení.</span><span class="sxs-lookup"><span data-stu-id="cb072-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="cb072-110">V následujícím příkladu `PublishedBy` přidružení je to přidružení k více (vydavatel publikuje mnoho knihy a publikování knihy se jeden vydavatelem).</span><span class="sxs-lookup"><span data-stu-id="cb072-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="cb072-111">`WrittenBy` Association je m: n přidružení (knihy, může mít několik autoři a Autor může zapisovat více knih).</span><span class="sxs-lookup"><span data-stu-id="cb072-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb072-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb072-112">Example</span></span>  
 <span data-ttu-id="cb072-113">Následující diagram znázorňuje Koncepční model se dvě přidružení: `PublishedBy` a `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="cb072-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="cb072-114">Přidružení končí pro `PublishedBy` jsou přidružení `Book` a `Publisher` typy entit.</span><span class="sxs-lookup"><span data-stu-id="cb072-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="cb072-115">Násobnost `Publisher` koncový je jedna (1) a násobnost `Book` koncový je mnoho (\*).</span><span class="sxs-lookup"><span data-stu-id="cb072-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 <span data-ttu-id="cb072-116">![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="cb072-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="cb072-117">ADO.NET Entity Framework používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="cb072-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="cb072-118">Definuje následující CSDL `PublishedBy` přidružení vidět v diagramu výše:</span><span class="sxs-lookup"><span data-stu-id="cb072-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="cb072-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb072-119">See Also</span></span>  
 [<span data-ttu-id="cb072-120">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="cb072-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="cb072-121">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="cb072-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
