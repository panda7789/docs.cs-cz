---
title: entity set
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 4473b74a4142bb49076068b50dc8b6f9c2c0d54a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959237"
---
# <a name="entity-set"></a><span data-ttu-id="24fdf-102">entity set</span><span class="sxs-lookup"><span data-stu-id="24fdf-102">entity set</span></span>
<span data-ttu-id="24fdf-103">*Sada entit* je logický kontejner pro instance [typu entity](../../../../docs/framework/data/adonet/entity-type.md) a instance libovolného typu odvozeného z tohoto typu entity.</span><span class="sxs-lookup"><span data-stu-id="24fdf-103">An *entity set* is a logical container for instances of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="24fdf-104">(Informace o odvozených typech naleznete v [tématu model EDM (Entity Data Model): Dědičnost](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) Vztah mezi typem entity a sadou entit je podobný relaci mezi řádkem a tabulkou v relační databázi: Podobně jako u řádku typ entity popisuje datovou strukturu a, podobně jako tabulka, sada entit obsahuje instance dané struktury.</span><span class="sxs-lookup"><span data-stu-id="24fdf-104">(For information about derived types, see [Entity Data Model: Inheritance](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="24fdf-105">Sada entit není konstrukcí modelování dat; nepopisuje strukturu dat.</span><span class="sxs-lookup"><span data-stu-id="24fdf-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="24fdf-106">Místo toho sada entit poskytuje konstrukci pro prostředí hostování nebo úložiště (například modul CLR (Common Language Runtime) nebo databáze SQL Server) k seskupení instancí typů entit tak, aby bylo možné je namapovat na úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="24fdf-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="24fdf-107">Sada entit je definována v rámci [kontejneru entit](../../../../docs/framework/data/adonet/entity-container.md), což je logické seskupení sad entit a [sad přidružení](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="24fdf-107">An entity set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of entity sets and [association sets](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="24fdf-108">Aby v sadě entit existovala instance typu entity, musí být splněny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="24fdf-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
- <span data-ttu-id="24fdf-109">Typ instance je buď stejný jako typ entity, na které je založena sada entit, nebo typ instance je podtypem typu entity.</span><span class="sxs-lookup"><span data-stu-id="24fdf-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
- <span data-ttu-id="24fdf-110">[Klíč entity](../../../../docs/framework/data/adonet/entity-key.md) pro instanci je v sadě entit jedinečný.</span><span class="sxs-lookup"><span data-stu-id="24fdf-110">The [entity key](../../../../docs/framework/data/adonet/entity-key.md) for the instance is unique within the entity set.</span></span>  
  
- <span data-ttu-id="24fdf-111">Instance neexistuje v žádné jiné sadě entit.</span><span class="sxs-lookup"><span data-stu-id="24fdf-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="24fdf-112">Pomocí stejného typu entity lze definovat více sad entit, ale instance daného typu entity může existovat pouze v jedné sadě entit.</span><span class="sxs-lookup"><span data-stu-id="24fdf-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="24fdf-113">Pro každý typ entity v koncepčním modelu nemusíte definovat sadu entit.</span><span class="sxs-lookup"><span data-stu-id="24fdf-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24fdf-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="24fdf-114">Example</span></span>  
 <span data-ttu-id="24fdf-115">Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher` `Author`a.</span><span class="sxs-lookup"><span data-stu-id="24fdf-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Vzorový model se třemi typy entit](./media/entity-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="24fdf-117">Následující diagram znázorňuje dvě sady entit (`Books` a `Publishers`) a sadu přidružení (`PublishedBy`) založenou na koncepčním modelu uvedeném výše.</span><span class="sxs-lookup"><span data-stu-id="24fdf-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="24fdf-118">BI v `Books` sadě entit představuje instanci `Book` typu entity v době běhu.</span><span class="sxs-lookup"><span data-stu-id="24fdf-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="24fdf-119">Podobně PJ představuje `Publisher` instanci `Publishers` v sadě entit.</span><span class="sxs-lookup"><span data-stu-id="24fdf-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="24fdf-120">BiPj představuje instanci `PublishedBy` přidružení `PublishedBy` v sadě přidružení.</span><span class="sxs-lookup"><span data-stu-id="24fdf-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje příklad sady.](./media/entity-set/sets-example-association.gif)  
  
 <span data-ttu-id="24fdf-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="24fdf-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="24fdf-123">Následující CSDL definuje kontejner entit s jednou sadou entit pro každý typ entity v koncepčním modelu uvedeném výše.</span><span class="sxs-lookup"><span data-stu-id="24fdf-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="24fdf-124">Všimněte si, že název a typ entity pro každou sadu entit jsou definovány pomocí atributů XML.</span><span class="sxs-lookup"><span data-stu-id="24fdf-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="24fdf-125">Je možné definovat několik sad entit na typ (MEST).</span><span class="sxs-lookup"><span data-stu-id="24fdf-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="24fdf-126">Následující CSDL definuje kontejner entit se dvěma sadami entit pro `Book` typ entity:</span><span class="sxs-lookup"><span data-stu-id="24fdf-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="24fdf-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24fdf-127">See also</span></span>

- [<span data-ttu-id="24fdf-128">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="24fdf-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="24fdf-129">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="24fdf-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
