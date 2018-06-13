---
title: model definované funkce
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 5c91c221735f3385370ec2fbb532d5b3c5dd2898
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763771"
---
# <a name="model-defined-function"></a><span data-ttu-id="de068-102">model definované funkce</span><span class="sxs-lookup"><span data-stu-id="de068-102">model-defined function</span></span>
<span data-ttu-id="de068-103">A *modelu definované funkce* je funkce, která je definována v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="de068-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="de068-104">Tělo funkce definované model je vyjádřen v [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), což umožňuje pro funkce, která má být vyjádřena nezávisle na pravidla nebo jazyky podporované v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="de068-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="de068-105">Definice pro funkci definované model obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="de068-105">A definition for a model-defined function contains the following information:</span></span>  
  
-   <span data-ttu-id="de068-106">Název funkce.</span><span class="sxs-lookup"><span data-stu-id="de068-106">A function name.</span></span> <span data-ttu-id="de068-107">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="de068-107">(Required)</span></span>  
  
-   <span data-ttu-id="de068-108">Typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="de068-108">The type of the return value.</span></span> <span data-ttu-id="de068-109">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="de068-109">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="de068-110">Pokud není zadaný žádný návratový typ, je vrácené hodnoty void.</span><span class="sxs-lookup"><span data-stu-id="de068-110">If no return type is specified, the return value is void.</span></span>  
  
-   <span data-ttu-id="de068-111">Informace o parametrech.</span><span class="sxs-lookup"><span data-stu-id="de068-111">Parameter information.</span></span> <span data-ttu-id="de068-112">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="de068-112">(Optional)</span></span>  
  
-   <span data-ttu-id="de068-113">[Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) výraz, který definuje tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="de068-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="de068-114">Všimněte si, že model definované funkce nepodporuje výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="de068-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="de068-115">Toto omezení je na místě, aby funkce definované modelu může být složené.</span><span class="sxs-lookup"><span data-stu-id="de068-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de068-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="de068-116">Example</span></span>  
 <span data-ttu-id="de068-117">Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`.</span><span class="sxs-lookup"><span data-stu-id="de068-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="de068-118">![Modelu s datum publikování](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span><span class="sxs-lookup"><span data-stu-id="de068-118">![Model With Published Date](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span></span>  
  
 <span data-ttu-id="de068-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="de068-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="de068-120">Následující CSDL definuje funkci v konceptuálním modelu, která vrátí počet let od instance `Book` byla publikována (v diagramu výše).</span><span class="sxs-lookup"><span data-stu-id="de068-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="de068-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="de068-121">See Also</span></span>  
 [<span data-ttu-id="de068-122">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="de068-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="de068-123">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="de068-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="de068-124">Model EDM (Entity Data Model): Primitivní datové typy</span><span class="sxs-lookup"><span data-stu-id="de068-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
