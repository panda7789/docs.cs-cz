---
title: association set
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: e279322f9e950cd4359db8c6dce39bfc46d188f6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732378"
---
# <a name="association-set"></a><span data-ttu-id="729ae-102">association set</span><span class="sxs-lookup"><span data-stu-id="729ae-102">association set</span></span>
<span data-ttu-id="729ae-103">*Sada přidružení* je logický kontejner pro instance [přidružení](association-type.md) stejného typu.</span><span class="sxs-lookup"><span data-stu-id="729ae-103">An *association set* is a logical container for [association](association-type.md) instances of the same type.</span></span> <span data-ttu-id="729ae-104">Sada přidružení není konstrukcí modelování dat; To znamená, že nepopisuje strukturu dat nebo relací.</span><span class="sxs-lookup"><span data-stu-id="729ae-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="729ae-105">Místo toho poskytuje sada přidružení konstrukci pro prostředí hostování nebo úložiště (například modul CLR (Common Language Runtime) nebo databáze SQL Server) k seskupení instancí přidružení, aby bylo možné je namapovat na úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="729ae-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="729ae-106">Sada přidružení je definována v rámci [kontejneru entit](entity-container.md), což je logické seskupení [sad entit](entity-set.md) a sad přidružení.</span><span class="sxs-lookup"><span data-stu-id="729ae-106">An association set is defined within an [entity container](entity-container.md), which is a logical grouping of [entity sets](entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="729ae-107">Definice sady přidružení obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="729ae-107">A definition for an association set contains the following information:</span></span>  
  
- <span data-ttu-id="729ae-108">Název sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="729ae-108">The association set name.</span></span> <span data-ttu-id="729ae-109">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="729ae-109">(Required)</span></span>  
  
- <span data-ttu-id="729ae-110">Přidružení, které bude obsahovat instance.</span><span class="sxs-lookup"><span data-stu-id="729ae-110">The association of which it will contain instances.</span></span> <span data-ttu-id="729ae-111">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="729ae-111">(Required)</span></span>  
  
- <span data-ttu-id="729ae-112">[Končí dvě sady přidružení](association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="729ae-112">Two [association set ends](association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="729ae-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="729ae-113">Example</span></span>  
 <span data-ttu-id="729ae-114">Následující diagram znázorňuje koncepční model se dvěma přidruženími: `PublishedBy`a `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="729ae-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="729ae-115">I když informace o sadách přidružení nejsou předány v diagramu, další diagram zobrazuje příklad sad přidružení a sad entit založených na tomto modelu.</span><span class="sxs-lookup"><span data-stu-id="729ae-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 ![Vzorový model se třemi typy entit](./media/association-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="729ae-117">Následující příklad ukazuje sadu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) na základě koncepčního modelu uvedeného výše.</span><span class="sxs-lookup"><span data-stu-id="729ae-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="729ae-118">BI v `Books` sadě entit představuje instanci `Book` typu entity v době běhu.</span><span class="sxs-lookup"><span data-stu-id="729ae-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="729ae-119">Podobně PJ představuje instanci `Publisher` v sadě entit `Publishers`.</span><span class="sxs-lookup"><span data-stu-id="729ae-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="729ae-120">BiPj představuje instanci přidružení `PublishedBy` v sadě přidružení `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="729ae-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje příklad sady.](./media/association-set/sets-example-association.gif)  
  
 <span data-ttu-id="729ae-122">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="729ae-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="729ae-123">Následující CSDL definuje kontejner entit s jednou sadou přidružení pro každé přidružení v diagramu výše.</span><span class="sxs-lookup"><span data-stu-id="729ae-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="729ae-124">Všimněte si, že název a přidružení pro každou sadu přidružení jsou definovány pomocí atributů XML.</span><span class="sxs-lookup"><span data-stu-id="729ae-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="729ae-125">Pro každé přidružení je možné definovat několik sad přidružení, pokud žádné dvě sady přidružení nesdílejí [zakončení sady přidružení](association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="729ae-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](association-set-end.md).</span></span> <span data-ttu-id="729ae-126">Následující CSDL definuje kontejner entit se dvěma sadami přidružení pro `WrittenBy` přidružení.</span><span class="sxs-lookup"><span data-stu-id="729ae-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="729ae-127">Všimněte si, že pro `Book` a `Author` typů entit byly definovány více sad entit a že žádná sada přidružení nesdílí sadu přidružení end.</span><span class="sxs-lookup"><span data-stu-id="729ae-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="729ae-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="729ae-128">See also</span></span>

- [<span data-ttu-id="729ae-129">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="729ae-129">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="729ae-130">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="729ae-130">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="729ae-131">foreign key property</span><span class="sxs-lookup"><span data-stu-id="729ae-131">foreign key property</span></span>](foreign-key-property.md)
