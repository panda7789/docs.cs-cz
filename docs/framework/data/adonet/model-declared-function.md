---
title: funkce deklarované modelu
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: f92bdfedaefca7182b5de72abae9852965d83ff7
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332043"
---
# <a name="model-declared-function"></a><span data-ttu-id="bbc8d-102">funkce deklarované modelu</span><span class="sxs-lookup"><span data-stu-id="bbc8d-102">model-declared function</span></span>
<span data-ttu-id="bbc8d-103">A *modelu deklarované funkce* je funkce, která je deklarována v konceptuálním modelu, ale není definovaný v tomto koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="bbc8d-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="bbc8d-104">Funkce mohou být definovány v prostředí hostování nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="bbc8d-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="bbc8d-105">Funkce deklarované modelu může například namapovat na funkce, která je definována v databázi tak vystavení funkce na straně serveru v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="bbc8d-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="bbc8d-106">Deklarace funkce deklarované model obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="bbc8d-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="bbc8d-107">Název funkce.</span><span class="sxs-lookup"><span data-stu-id="bbc8d-107">The name of the function.</span></span> <span data-ttu-id="bbc8d-108">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="bbc8d-108">(Required)</span></span>  
  
-   <span data-ttu-id="bbc8d-109">Typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bbc8d-109">The type of the return value.</span></span> <span data-ttu-id="bbc8d-110">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="bbc8d-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bbc8d-111">Pokud není zadána žádná návratová hodnota, je návratový typ void.</span><span class="sxs-lookup"><span data-stu-id="bbc8d-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="bbc8d-112">Informace o parametrech, včetně názvu parametru a typu.</span><span class="sxs-lookup"><span data-stu-id="bbc8d-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="bbc8d-113">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="bbc8d-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbc8d-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="bbc8d-114">Example</span></span>  
 <span data-ttu-id="bbc8d-115">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů.</span><span class="sxs-lookup"><span data-stu-id="bbc8d-115">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="bbc8d-116">V CSDL, je jedna implementace modelu deklarovaná funkce [funkce import](https://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span><span class="sxs-lookup"><span data-stu-id="bbc8d-116">In CSDL, one implementation of a model-declared function is a [function import](https://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span></span> <span data-ttu-id="bbc8d-117">Následující CSDL definuje kontejneru entity s definicí funkce importu.</span><span class="sxs-lookup"><span data-stu-id="bbc8d-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="bbc8d-118">Všimněte si, že návratový typ pro funkci je neplatný, protože není zadán žádný návratový typ.</span><span class="sxs-lookup"><span data-stu-id="bbc8d-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="bbc8d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbc8d-119">See Also</span></span>  
 [<span data-ttu-id="bbc8d-120">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="bbc8d-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="bbc8d-121">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="bbc8d-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
