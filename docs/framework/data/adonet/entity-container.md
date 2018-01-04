---
title: Kontejneru entit
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4da9b4e45389df4894defa0cc04cfc6c616db447
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="entity-container"></a><span data-ttu-id="f0831-102">Kontejneru entit</span><span class="sxs-lookup"><span data-stu-id="f0831-102">entity container</span></span>
<span data-ttu-id="f0831-103">*Kontejneru entit* je logické seskupení [sad entit](../../../../docs/framework/data/adonet/entity-set.md), [přidružení sady](../../../../docs/framework/data/adonet/association-set.md), a [funkce importy](../../../../docs/framework/data/adonet/model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="f0831-103">An *entity container* is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md), [association sets](../../../../docs/framework/data/adonet/association-set.md), and [function imports](../../../../docs/framework/data/adonet/model-declared-function.md).</span></span>  
  
 <span data-ttu-id="f0831-104">Následující musí být splněné z kontejner entitu definovanou v konceptuálním modelu:</span><span class="sxs-lookup"><span data-stu-id="f0831-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
-   <span data-ttu-id="f0831-105">Minimálně jednu entitu kontejneru musí být definován v každé konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="f0831-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
-   <span data-ttu-id="f0831-106">Kontejneru entit musí mít jedinečný název v rámci každé konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="f0831-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="f0831-107">Kontejner entity můžete definovat sady entit nebo sady přidružení, které používají typy entit a přidružení definované v jedné nebo více oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="f0831-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="f0831-108">Další informace najdete v tématu [datového modelu Entity: obory názvů](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="f0831-108">For more information, see [Entity Data Model: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0831-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0831-109">Example</span></span>  
 <span data-ttu-id="f0831-110">Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`.</span><span class="sxs-lookup"><span data-stu-id="f0831-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="f0831-111">Podívejte se na další příklad další informace.</span><span class="sxs-lookup"><span data-stu-id="f0831-111">See the next example for more information.</span></span>  
  
 <span data-ttu-id="f0831-112">![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="f0831-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="f0831-113">I když diagram špatně přenáší informace o kontejneru entit, musíte definovat konceptuálního modelu kontejner entity.</span><span class="sxs-lookup"><span data-stu-id="f0831-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="f0831-114">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá DSL, kterému se říká jazyk definice konceptuálního schématu ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="f0831-114">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="f0831-115">Následující CSDL definuje kontejner entity pro koncepční model zobrazený v diagramu výše.</span><span class="sxs-lookup"><span data-stu-id="f0831-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="f0831-116">Všimněte si, že název kontejneru entit je definována v atribut XML.</span><span class="sxs-lookup"><span data-stu-id="f0831-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="f0831-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0831-117">See Also</span></span>  
 [<span data-ttu-id="f0831-118">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="f0831-118">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="f0831-119">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="f0831-119">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
