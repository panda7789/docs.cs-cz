---
title: model-defined function
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 77152e8f37b009cbc3e72f053ead867914768d3d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226635"
---
# <a name="model-defined-function"></a><span data-ttu-id="ccc4e-102">model-defined function</span><span class="sxs-lookup"><span data-stu-id="ccc4e-102">model-defined function</span></span>
<span data-ttu-id="ccc4e-103">A *modelově definovaných funkcí* je funkce, která je definována v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="ccc4e-104">Tělo funkce definované model je vyjádřen v [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), který umožňuje pro funkce, který má být vyjádřena nezávisle na pravidla nebo ve zdroji dat podporuje jazyky.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="ccc4e-105">Definice pro definovaný model funkci obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="ccc4e-105">A definition for a model-defined function contains the following information:</span></span>  
  
-   <span data-ttu-id="ccc4e-106">Název funkce.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-106">A function name.</span></span> <span data-ttu-id="ccc4e-107">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="ccc4e-107">(Required)</span></span>  
  
-   <span data-ttu-id="ccc4e-108">Typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-108">The type of the return value.</span></span> <span data-ttu-id="ccc4e-109">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="ccc4e-109">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ccc4e-110">Pokud není zadán žádný návratový typ, vrácená hodnota je typu void.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-110">If no return type is specified, the return value is void.</span></span>  
  
-   <span data-ttu-id="ccc4e-111">Informace o parametrech.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-111">Parameter information.</span></span> <span data-ttu-id="ccc4e-112">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="ccc4e-112">(Optional)</span></span>  
  
-   <span data-ttu-id="ccc4e-113">[Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) výraz, který definuje těla funkce.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="ccc4e-114">Všimněte si, že modelově definovaných funkcí nepodporuje výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="ccc4e-115">Toto omezení je na místě, tak, aby se může skládat modelově definovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccc4e-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccc4e-116">Example</span></span>  
 <span data-ttu-id="ccc4e-117">Následující diagram znázorňuje Koncepční model s tři typy entit: `Book`, `Publisher`, a `Author`.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Snímek obrazovky zobrazující model se datum publikování.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="ccc4e-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ccc4e-120">Následující CSDL definuje funkci v konceptuálním modelu, který vrací počet let od instance `Book` (ve výše uvedeném diagramu) publikoval.</span><span class="sxs-lookup"><span data-stu-id="ccc4e-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="ccc4e-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccc4e-121">See also</span></span>

- [<span data-ttu-id="ccc4e-122">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="ccc4e-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="ccc4e-123">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="ccc4e-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="ccc4e-124">Model Entity Data Model: Primitivní datové typy</span><span class="sxs-lookup"><span data-stu-id="ccc4e-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
