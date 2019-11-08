---
title: association end
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 489802ca18708e076c0cd5dd380ad1361916ad5f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732356"
---
# <a name="association-end"></a><span data-ttu-id="f4dc2-102">association end</span><span class="sxs-lookup"><span data-stu-id="f4dc2-102">association end</span></span>
<span data-ttu-id="f4dc2-103">*Zakončení přidružení* identifikuje [typ entity](entity-type.md) na jednom konci [přidružení](association-type.md) a počet instancí typu entity, které mohou existovat na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-103">An *association end* identifies the [entity type](entity-type.md) on one end of an [association](association-type.md) and the number of entity type instances that can exist at that end of an association.</span></span> <span data-ttu-id="f4dc2-104">Zakončení přidružení jsou definována jako součást přidružení; přidružení musí mít přesně dvě zakončení přidružení.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-104">Association ends are defined as part of an association; an association must have exactly two association ends.</span></span> <span data-ttu-id="f4dc2-105">[Navigační vlastnosti](navigation-property.md) umožňují navigaci z jednoho zakončení přidružení k druhému.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-105">[Navigation properties](navigation-property.md) allow for navigation from one association end to the other.</span></span>  
  
 <span data-ttu-id="f4dc2-106">Definice elementu end přidružení obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="f4dc2-106">An association end definition contains the following information:</span></span>  
  
- <span data-ttu-id="f4dc2-107">Jeden z typů entit zapojených do přidružení.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-107">One of the entity types involved in the association.</span></span> <span data-ttu-id="f4dc2-108">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="f4dc2-108">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f4dc2-109">Pro dané přidružení může být typ entity zadaný pro každý konec přidružení stejný.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-109">For a given association, the entity type specified for each association end can be the same.</span></span> <span data-ttu-id="f4dc2-110">Tím se vytvoří samo přidružení.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-110">This creates a self-association.</span></span>  
  
- <span data-ttu-id="f4dc2-111">[Násobnost zakončení přidružení](association-end-multiplicity.md) , která označuje počet instancí typu entity, které mohou být na jednom konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-111">An [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="f4dc2-112">Násobnost zakončení přidružení může mít hodnotu jedna (1), 0 nebo 1 (0.. 1) nebo mnoho (\*).</span><span class="sxs-lookup"><span data-stu-id="f4dc2-112">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span>  
  
- <span data-ttu-id="f4dc2-113">Název zakončení přidružení.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-113">A name for the association end.</span></span> <span data-ttu-id="f4dc2-114">Volitelné</span><span class="sxs-lookup"><span data-stu-id="f4dc2-114">(Optional)</span></span>  
  
- <span data-ttu-id="f4dc2-115">Informace o operacích, které jsou prováděny na konci přidružení, jako je například kaskáda při odstranění.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-115">Information about operations that are performed on the association end, such as cascade on delete.</span></span> <span data-ttu-id="f4dc2-116">Volitelné</span><span class="sxs-lookup"><span data-stu-id="f4dc2-116">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4dc2-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4dc2-117">Example</span></span>  
 <span data-ttu-id="f4dc2-118">Následující diagram znázorňuje koncepční model se dvěma přidruženími: `PublishedBy` a `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-118">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="f4dc2-119">Zakončení přidružení pro `PublishedBy` přidružení jsou typy entit `Book` a `Publisher`.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-119">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="f4dc2-120">Násobnost `Publisher` end je jedna (1) a násobnost `Book` end je mnoho (\*), což znamená, že vydavatel zveřejňuje mnoho knih a kniha je publikována jedním vydavatelem.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-120">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![Vzorový model se třemi typy entit](./media/association-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="f4dc2-122">ADO.NET Entity Framework používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="f4dc2-122">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="f4dc2-123">Následující CSDL definuje přidružení `PublishedBy` zobrazené v diagramu výše.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-123">The CSDL below defines the `PublishedBy` association shown in the diagram above.</span></span> <span data-ttu-id="f4dc2-124">Všimněte si, že typ, název a násobnost každého elementu end přidružení jsou určeny atributy XML (`Type`, `Role`a `Multiplicity` atributů v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="f4dc2-124">Note that the type, name, and multiplicity of each association end are specified by XML attributes (the `Type`, `Role`, and `Multiplicity` attributes, respectively).</span></span> <span data-ttu-id="f4dc2-125">Volitelné informace o operacích provedených na konci jsou zadány v elementu XML (`OnDelete` element).</span><span class="sxs-lookup"><span data-stu-id="f4dc2-125">Optional information about operations performed on an end is specified in an XML element (the `OnDelete` element).</span></span> <span data-ttu-id="f4dc2-126">V tomto případě platí, že pokud je Vydavatel odstraněn, jsou všechny přidružené knihy.</span><span class="sxs-lookup"><span data-stu-id="f4dc2-126">In this case, if a publisher is deleted, so are all associated books.</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a><span data-ttu-id="f4dc2-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4dc2-127">See also</span></span>

- [<span data-ttu-id="f4dc2-128">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="f4dc2-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="f4dc2-129">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="f4dc2-129">Entity Data Model</span></span>](entity-data-model.md)
