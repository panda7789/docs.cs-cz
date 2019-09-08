---
title: model-defined function
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 1418eccecea647204620455969696c6390bd4a18
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783618"
---
# <a name="model-defined-function"></a><span data-ttu-id="aef14-102">model-defined function</span><span class="sxs-lookup"><span data-stu-id="aef14-102">model-defined function</span></span>
<span data-ttu-id="aef14-103">*Funkce definovaná modelem* je funkce, která je definována v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="aef14-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="aef14-104">Tělo funkce definované modelem je vyjádřeno v [Entity SQL](./ef/language-reference/entity-sql-language.md), což umožňuje, aby byla funkce vyjádřena nezávisle na pravidlech nebo jazycích podporovaných ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="aef14-104">The body of a model-defined function is expressed in [Entity SQL](./ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="aef14-105">Definice funkce definované modelem obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="aef14-105">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="aef14-106">Název funkce.</span><span class="sxs-lookup"><span data-stu-id="aef14-106">A function name.</span></span> <span data-ttu-id="aef14-107">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="aef14-107">(Required)</span></span>  
  
- <span data-ttu-id="aef14-108">Typ návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="aef14-108">The type of the return value.</span></span> <span data-ttu-id="aef14-109">Volitelné</span><span class="sxs-lookup"><span data-stu-id="aef14-109">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="aef14-110">Pokud není zadán žádný návratový typ, návratová hodnota je void.</span><span class="sxs-lookup"><span data-stu-id="aef14-110">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="aef14-111">Informace o parametrech.</span><span class="sxs-lookup"><span data-stu-id="aef14-111">Parameter information.</span></span> <span data-ttu-id="aef14-112">Volitelné</span><span class="sxs-lookup"><span data-stu-id="aef14-112">(Optional)</span></span>  
  
- <span data-ttu-id="aef14-113">Výraz [Entity SQL](./ef/language-reference/entity-sql-language.md) definující tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="aef14-113">An [Entity SQL](./ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="aef14-114">Všimněte si, že funkce definované modelem nepodporují výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="aef14-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="aef14-115">Toto omezení je nastaveno tak, aby bylo možné sestavit funkce definované modelem.</span><span class="sxs-lookup"><span data-stu-id="aef14-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aef14-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="aef14-116">Example</span></span>  
 <span data-ttu-id="aef14-117">Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher` `Author`a.</span><span class="sxs-lookup"><span data-stu-id="aef14-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje model s datem publikování](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="aef14-119">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="aef14-119">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="aef14-120">Následující CSDL definuje funkci v koncepčním modelu, která vrací počet roků od okamžiku, kdy byla publikována instance `Book` (v diagramu výše).</span><span class="sxs-lookup"><span data-stu-id="aef14-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="aef14-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aef14-121">See also</span></span>

- [<span data-ttu-id="aef14-122">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="aef14-122">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="aef14-123">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="aef14-123">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="aef14-124">Model EDM (Entity Data Model): Primitivní datové typy</span><span class="sxs-lookup"><span data-stu-id="aef14-124">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)
