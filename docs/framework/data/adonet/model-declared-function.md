---
title: deklarovaný modelu – funkce
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: fd573df4eb93b44622bb3b2f611ed726f4700b1d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="model-declared-function"></a><span data-ttu-id="3c762-102">deklarovaný modelu – funkce</span><span class="sxs-lookup"><span data-stu-id="3c762-102">model-declared function</span></span>
<span data-ttu-id="3c762-103">A *modelu deklarované funkce* je funkce, která je deklarován v konceptuálním modelu, ale není definován v tomto konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="3c762-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="3c762-104">Funkce mohou být definovány v prostředí hostování nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="3c762-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="3c762-105">Například může funkce modelu deklarované mapovat na funkci, která je definována v databázi, proto vystavení funkce na straně serveru v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="3c762-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="3c762-106">Deklarace funkce deklarovaný model obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="3c762-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="3c762-107">Název funkce.</span><span class="sxs-lookup"><span data-stu-id="3c762-107">The name of the function.</span></span> <span data-ttu-id="3c762-108">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="3c762-108">(Required)</span></span>  
  
-   <span data-ttu-id="3c762-109">Typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3c762-109">The type of the return value.</span></span> <span data-ttu-id="3c762-110">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="3c762-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c762-111">Pokud je zadán žádnou návratovou hodnotu, je návratový typ void.</span><span class="sxs-lookup"><span data-stu-id="3c762-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="3c762-112">Informace o parametrech, včetně parametr názvu a typu.</span><span class="sxs-lookup"><span data-stu-id="3c762-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="3c762-113">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="3c762-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c762-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c762-114">Example</span></span>  
 <span data-ttu-id="3c762-115">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="3c762-115">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="3c762-116">V CSDL, je jednou z implementací funkce modelu deklarované [import funkce](http://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span><span class="sxs-lookup"><span data-stu-id="3c762-116">In CSDL, one implementation of a model-declared function is a [function import](http://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span></span> <span data-ttu-id="3c762-117">Následující CSDL definuje kontejner entity s definicí importu funkce.</span><span class="sxs-lookup"><span data-stu-id="3c762-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="3c762-118">Všimněte si, že návratový typ pro funkci je neplatné, protože není zadán žádný návratový typ.</span><span class="sxs-lookup"><span data-stu-id="3c762-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="3c762-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c762-119">See Also</span></span>  
 [<span data-ttu-id="3c762-120">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="3c762-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="3c762-121">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="3c762-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
