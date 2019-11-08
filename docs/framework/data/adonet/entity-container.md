---
title: entity container
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 0c194d86e6276c948a545f830e569cbc68f86a14
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737871"
---
# <a name="entity-container"></a><span data-ttu-id="1d955-102">entity container</span><span class="sxs-lookup"><span data-stu-id="1d955-102">entity container</span></span>
<span data-ttu-id="1d955-103">*Kontejner entit* je logické seskupení [sad entit](entity-set.md), [sad přidružení](association-set.md)a [importů funkcí](model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="1d955-103">An *entity container* is a logical grouping of [entity sets](entity-set.md), [association sets](association-set.md), and [function imports](model-declared-function.md).</span></span>  
  
 <span data-ttu-id="1d955-104">Následující hodnota musí být true kontejneru entity definovaného v koncepčním modelu:</span><span class="sxs-lookup"><span data-stu-id="1d955-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
- <span data-ttu-id="1d955-105">V každém koncepčním modelu musí být definován alespoň jeden kontejner entit.</span><span class="sxs-lookup"><span data-stu-id="1d955-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
- <span data-ttu-id="1d955-106">Kontejner entity musí mít jedinečný název v rámci každého koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="1d955-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="1d955-107">Kontejner entit může definovat sady entit nebo sady přidružení, které používají typy entit nebo přidružení definované v jednom nebo více oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="1d955-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="1d955-108">Další informace najdete v tématu [model EDM (Entity Data Model): obory názvů](entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="1d955-108">For more information, see [Entity Data Model: Namespaces](entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d955-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d955-109">Example</span></span>  
 <span data-ttu-id="1d955-110">Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher`a `Author`.</span><span class="sxs-lookup"><span data-stu-id="1d955-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="1d955-111">Další informace najdete v dalším příkladu.</span><span class="sxs-lookup"><span data-stu-id="1d955-111">See the next example for more information.</span></span>  
  
 ![Vzorový model se třemi typy entit](./media/entity-container/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="1d955-113">I když diagram nevyjadřuje informace o kontejneru entit, koncepční model musí definovat kontejner entit.</span><span class="sxs-lookup"><span data-stu-id="1d955-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="1d955-114">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů DSL označované jako konceptuální schéma Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)).</span><span class="sxs-lookup"><span data-stu-id="1d955-114">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="1d955-115">Následující CSDL definuje kontejner entit pro koncepční model zobrazený v diagramu výše.</span><span class="sxs-lookup"><span data-stu-id="1d955-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="1d955-116">Všimněte si, že název kontejneru entity je definován v atributu XML.</span><span class="sxs-lookup"><span data-stu-id="1d955-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="1d955-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d955-117">See also</span></span>

- [<span data-ttu-id="1d955-118">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="1d955-118">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="1d955-119">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="1d955-119">Entity Data Model</span></span>](entity-data-model.md)
