---
title: "Model Entity Data Model: dědičnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 421a2bdbf2652880097fb1df3c9b63f38ac2bd10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="entity-data-model-inheritance"></a><span data-ttu-id="7ad8b-102">Model Entity Data Model: dědičnosti</span><span class="sxs-lookup"><span data-stu-id="7ad8b-102">Entity Data Model: Inheritance</span></span>
<span data-ttu-id="7ad8b-103">Entity Data Model (EDM) podporuje dědičnosti pro [typy entit](../../../../docs/framework/data/adonet/entity-type.md).</span><span class="sxs-lookup"><span data-stu-id="7ad8b-103">The Entity Data Model (EDM) supports inheritance for [entity types](../../../../docs/framework/data/adonet/entity-type.md).</span></span> <span data-ttu-id="7ad8b-104">Dědičnost v modelu EDM je podobná dědičnosti pro třídy v objektově orientované programovací jazyky.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-104">Inheritance in the EDM is similar to inheritance for classes in object-oriented programming languages.</span></span> <span data-ttu-id="7ad8b-105">Jako pomocí třídy v objektově orientovaný jazyků v konceptuálním modelu můžete definovat typ entity ( *odvozeného typu*), dědí z jiného typu entity ( *základní typ*).</span><span class="sxs-lookup"><span data-stu-id="7ad8b-105">Like with classes in object-oriented languages, in a conceptual model you can define an entity type (a *derived type*) that inherits from another entity type (the *base type*).</span></span> <span data-ttu-id="7ad8b-106">Ale na rozdíl od třídy v objektově orientované programování v konceptuálním modelu odvozený typ vždy dědí všechny [vlastnosti](../../../../docs/framework/data/adonet/property.md) a [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) základního typu.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-106">However, unlike classes in object-oriented programming, in a conceptual model the derived type always inherits all the [properties](../../../../docs/framework/data/adonet/property.md) and [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) of the base type.</span></span> <span data-ttu-id="7ad8b-107">Nejde přepsat zděděné vlastnosti v odvozeném typu.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-107">You cannot override inherited properties in a derived type.</span></span>  
  
 <span data-ttu-id="7ad8b-108">Hierarchie dědičnosti, ve kterých odvozený typ dědí z jiné odvozený typ můžete vytvořit v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-108">In a conceptual model you can build inheritance hierarchies in which a derived type inherits from another derived type.</span></span> <span data-ttu-id="7ad8b-109">Typ na nejvyšší úrovni hierarchie (jeden typ v hierarchii, která není typu odvozené) se nazývá *kořenový typ*.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-109">The type at the top of the hierarchy (the one type in the hierarchy that is not a derived type) is called the *root type*.</span></span> <span data-ttu-id="7ad8b-110">V hierarchii dědičnosti [klíč entity](../../../../docs/framework/data/adonet/entity-key.md) v kořenové typ musí být definován.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-110">In an inheritance hierarchy, the [entity key](../../../../docs/framework/data/adonet/entity-key.md) must be defined on the root type.</span></span>  
  
 <span data-ttu-id="7ad8b-111">Hierarchie dědičnosti, ve kterých odvozený typ dědí z více než jeden typ nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-111">You cannot build inheritance hierarchies in which a derived type inherits from more than one type.</span></span> <span data-ttu-id="7ad8b-112">Například v konceptuálním modelu s `Book` typ entity, můžete definovat odvozené typy `FictionBook` a `NonFictionBook` každý dědit z `Book`.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-112">For example, in a conceptual model with a `Book` entity type, you could define derived types `FictionBook` and `NonFictionBook` that each inherit from `Book`.</span></span> <span data-ttu-id="7ad8b-113">Však nelze definovat pak typ, který dědí z obou `FictionBook` a `NonFictionBook` typy.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-113">However, you could not then define a type that inherits from both the `FictionBook` and `NonFictionBook` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ad8b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ad8b-114">Example</span></span>  
 <span data-ttu-id="7ad8b-115">Následující diagram znázorňuje Koncepční model s čtyři typy entit: `Book`, `FictionBook`, `Publisher`, a `Author`.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-115">The diagram below shows a conceptual model with four entity types: `Book`, `FictionBook`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="7ad8b-116">`FictionBook` Typ entity je odvozený typ, která dědí z `Book` typ entity.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-116">The `FictionBook` entity type is a derived type, inheriting from the `Book` entity type.</span></span> <span data-ttu-id="7ad8b-117">`FictionBook` Typ dědí `ISBN (Key)`, `Title`, a `Revision` vlastnosti a definuje další vlastnost s názvem `Genre`.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-117">The `FictionBook` type inherits the `ISBN (Key)`, `Title`, and `Revision` properties, and defines an additional property called `Genre`.</span></span>  
  
 <span data-ttu-id="7ad8b-118">![Dědičnost](../../../../docs/framework/data/adonet/media/inheritanceexample.gif "InheritanceExample")</span><span class="sxs-lookup"><span data-stu-id="7ad8b-118">![Inheritance](../../../../docs/framework/data/adonet/media/inheritanceexample.gif "InheritanceExample")</span></span>  
  
 <span data-ttu-id="7ad8b-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="7ad8b-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="7ad8b-120">Následující CSDL definuje typ entity `FictionBook`, který dědí z `Book` typu (jako v diagramu výše):</span><span class="sxs-lookup"><span data-stu-id="7ad8b-120">The following CSDL defines an entity type, `FictionBook`, that inherits from the `Book` type (as in the diagram above):</span></span>  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a><span data-ttu-id="7ad8b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ad8b-121">See Also</span></span>  
 [<span data-ttu-id="7ad8b-122">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="7ad8b-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="7ad8b-123">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="7ad8b-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
