---
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 59eed56204543adf405cfc7c71a49697a9e18374
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769663"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="8140a-102">association end multiplicity</span><span class="sxs-lookup"><span data-stu-id="8140a-102">association end multiplicity</span></span>
<span data-ttu-id="8140a-103">*Násobnost end přidružení* definuje počet [typ entity](../../../../docs/framework/data/adonet/entity-type.md) instancí, které mohou být na jednom konci [přidružení](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="8140a-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="8140a-104">Násobnost end přidružení může mít jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="8140a-104">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="8140a-105">jedna (1): Označuje, že tuto instanci typu přesně jedna entita existuje na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="8140a-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="8140a-106">nula nebo jedna (0..1): Udává, že existuje žádnou nebo jednou instancí typu entity na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="8140a-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="8140a-107">Mnoho (\*): Udává, že existuje žádného, jednoho nebo více instancí typu entity na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="8140a-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="8140a-108">Asociace je často vyznačují Násobnosti zakončení její přidružení.</span><span class="sxs-lookup"><span data-stu-id="8140a-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="8140a-109">Například, pokud konce asociace mají násobnosti jeden (1) a mnoho (\*), přidružení je označováno jako jeden mnoho přidružení.</span><span class="sxs-lookup"><span data-stu-id="8140a-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="8140a-110">V následujícím příkladu `PublishedBy` přidružení je přidružení jednoho k několika (vydavatel publikuje mnoho knih a knihy se publikuje vydavatele).</span><span class="sxs-lookup"><span data-stu-id="8140a-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="8140a-111">`WrittenBy` Přidružení je přidružení many-to-many (knihu můžete mít více autoři a autor můžete psát více seznamů).</span><span class="sxs-lookup"><span data-stu-id="8140a-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8140a-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="8140a-112">Example</span></span>  
 <span data-ttu-id="8140a-113">Následující diagram znázorňuje Koncepční model se dvěma přidružení: `PublishedBy` a `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="8140a-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="8140a-114">Konec asociace `PublishedBy` přidružení se `Book` a `Publisher` typy entit.</span><span class="sxs-lookup"><span data-stu-id="8140a-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="8140a-115">Násobnost `Publisher` end je jedna (1) a násobnost `Book` end je mnoho (\*).</span><span class="sxs-lookup"><span data-stu-id="8140a-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![Příklad modelu s tři typy entit](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="8140a-117">ADO.NET Entity Framework používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů.</span><span class="sxs-lookup"><span data-stu-id="8140a-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="8140a-118">Definuje následující CSDL `PublishedBy` přidružení, které jsou zobrazeny ve výše uvedeném diagramu:</span><span class="sxs-lookup"><span data-stu-id="8140a-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="8140a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8140a-119">See also</span></span>

- [<span data-ttu-id="8140a-120">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="8140a-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="8140a-121">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="8140a-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
