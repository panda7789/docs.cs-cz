---
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 3f3d8ba9f7e68065024dd3efb599b847496740cd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738565"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="993d2-102">association end multiplicity</span><span class="sxs-lookup"><span data-stu-id="993d2-102">association end multiplicity</span></span>
<span data-ttu-id="993d2-103">*Násobnost zakončení přidružení* definuje počet instancí [typu entity](entity-type.md) , které mohou být na jednom konci [přidružení](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="993d2-103">*Association end multiplicity* defines the number of [entity type](entity-type.md) instances that can be at one end of an [association](association-type.md).</span></span>  
  
 <span data-ttu-id="993d2-104">Násobnost zakončení přidružení může mít jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="993d2-104">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="993d2-105">jedna (1): označuje, že na konci přidružení existuje přesně jedna instance typu entity.</span><span class="sxs-lookup"><span data-stu-id="993d2-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="993d2-106">nula nebo jedna (0.. 1): označuje, že na konci přidružení existují žádné nebo jedna instance typu entity.</span><span class="sxs-lookup"><span data-stu-id="993d2-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="993d2-107">mnoho (\*): udává, že na konci přidružení existují žádné instance typu entity nula, jedna nebo více.</span><span class="sxs-lookup"><span data-stu-id="993d2-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="993d2-108">Přidružení je často charakteristické násobnostmi koncovosti přidružení.</span><span class="sxs-lookup"><span data-stu-id="993d2-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="993d2-109">Například pokud má element end přidružení násobnosti 1 a mnoho (\*), přidružení se nazývá přidružení 1:1.</span><span class="sxs-lookup"><span data-stu-id="993d2-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="993d2-110">V následujícím příkladu je přidružení `PublishedBy` přidružení typu 1: n (vydavatel zveřejňuje mnoho knih a kniha je publikována jedním vydavatelem).</span><span class="sxs-lookup"><span data-stu-id="993d2-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="993d2-111">Přidružení `WrittenBy` je přidružení typu m:n (kniha může mít více autorů a autor může zapisovat několik knih).</span><span class="sxs-lookup"><span data-stu-id="993d2-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="993d2-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="993d2-112">Example</span></span>  
 <span data-ttu-id="993d2-113">Následující diagram znázorňuje koncepční model se dvěma přidruženími: `PublishedBy` a `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="993d2-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="993d2-114">Zakončení přidružení pro `PublishedBy` přidružení jsou typy entit `Book` a `Publisher`.</span><span class="sxs-lookup"><span data-stu-id="993d2-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="993d2-115">Násobnost `Publisher` end je jedna (1) a násobnost `Book` end má mnoho (\*).</span><span class="sxs-lookup"><span data-stu-id="993d2-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![Vzorový model se třemi typy entit](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="993d2-117">ADO.NET Entity Framework používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="993d2-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="993d2-118">Následující CSDL definuje přidružení `PublishedBy` zobrazené v diagramu výše:</span><span class="sxs-lookup"><span data-stu-id="993d2-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="993d2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="993d2-119">See also</span></span>

- [<span data-ttu-id="993d2-120">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="993d2-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="993d2-121">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="993d2-121">Entity Data Model</span></span>](entity-data-model.md)
