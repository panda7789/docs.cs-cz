---
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cdcf69e7118620b2f8febd02d7695d429bf8cc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786941"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="8a1cf-102">association end multiplicity</span><span class="sxs-lookup"><span data-stu-id="8a1cf-102">association end multiplicity</span></span>
<span data-ttu-id="8a1cf-103">*Násobnost zakončení přidružení* definuje počet instancí [typu entity](entity-type.md) , které mohou být na jednom konci [přidružení](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="8a1cf-103">*Association end multiplicity* defines the number of [entity type](entity-type.md) instances that can be at one end of an [association](association-type.md).</span></span>  
  
 <span data-ttu-id="8a1cf-104">Násobnost zakončení přidružení může mít jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="8a1cf-104">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="8a1cf-105">jedna (1): Označuje, že na konci přidružení existuje přesně jedna instance typu entity.</span><span class="sxs-lookup"><span data-stu-id="8a1cf-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="8a1cf-106">nula nebo jedna (0.. 1): Označuje, že na konci přidružení existují žádné nebo jedna instance typu entity.</span><span class="sxs-lookup"><span data-stu-id="8a1cf-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="8a1cf-107">mnoho (\*): Označuje, že na konci přidružení existují žádné instance typu entity nula, jedna nebo více.</span><span class="sxs-lookup"><span data-stu-id="8a1cf-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="8a1cf-108">Přidružení je často charakteristické násobnostmi koncovosti přidružení.</span><span class="sxs-lookup"><span data-stu-id="8a1cf-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="8a1cf-109">Například pokud končí přidružení násobnosti jedna (1) a many (\*), přidružení se nazývá přidružení 1:1.</span><span class="sxs-lookup"><span data-stu-id="8a1cf-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="8a1cf-110">V následujícím `PublishedBy` příkladu je přidružení přidružení typu 1: n (vydavatel zveřejňuje mnoho knih a kniha je publikována jedním vydavatelem).</span><span class="sxs-lookup"><span data-stu-id="8a1cf-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="8a1cf-111">`WrittenBy` Přidružení je asociace typu m:n (kniha může mít více autorů a autor může zapisovat několik knih).</span><span class="sxs-lookup"><span data-stu-id="8a1cf-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a1cf-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a1cf-112">Example</span></span>  
 <span data-ttu-id="8a1cf-113">Následující diagram znázorňuje koncepční model se dvěma přidruženími: `PublishedBy` a. `WrittenBy`</span><span class="sxs-lookup"><span data-stu-id="8a1cf-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="8a1cf-114">Přidružení `PublishedBy` jsouzakončenápro`Publisher` přidružení jsou typy entit a.`Book`</span><span class="sxs-lookup"><span data-stu-id="8a1cf-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="8a1cf-115">Násobnost elementu `Publisher` end je jedna (1) a násobnost elementu `Book` end je mnoho (\*).</span><span class="sxs-lookup"><span data-stu-id="8a1cf-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![Vzorový model se třemi typy entit](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="8a1cf-117">ADO.NET Entity Framework používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="8a1cf-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="8a1cf-118">Následující CSDL definuje `PublishedBy` přidružení zobrazené v diagramu výše:</span><span class="sxs-lookup"><span data-stu-id="8a1cf-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="8a1cf-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a1cf-119">See also</span></span>

- [<span data-ttu-id="8a1cf-120">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="8a1cf-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="8a1cf-121">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="8a1cf-121">Entity Data Model</span></span>](entity-data-model.md)
