---
title: "deklarovaný modelu – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2f5c7828dc1ea79a548b35109b428da05c2b4560
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="model-declared-function"></a><span data-ttu-id="a83a1-102">deklarovaný modelu – funkce</span><span class="sxs-lookup"><span data-stu-id="a83a1-102">model-declared function</span></span>
<span data-ttu-id="a83a1-103">A *modelu deklarované funkce* je funkce, která je deklarován v konceptuálním modelu, ale není definován v tomto konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="a83a1-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="a83a1-104">Funkce mohou být definovány v prostředí hostování nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="a83a1-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="a83a1-105">Například může funkce modelu deklarované mapovat na funkci, která je definována v databázi, proto vystavení funkce na straně serveru v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="a83a1-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="a83a1-106">Deklarace funkce deklarovaný model obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="a83a1-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="a83a1-107">Název funkce.</span><span class="sxs-lookup"><span data-stu-id="a83a1-107">The name of the function.</span></span> <span data-ttu-id="a83a1-108">(Povinné)</span><span class="sxs-lookup"><span data-stu-id="a83a1-108">(Required)</span></span>  
  
-   <span data-ttu-id="a83a1-109">Typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a83a1-109">The type of the return value.</span></span> <span data-ttu-id="a83a1-110">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="a83a1-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a83a1-111">Pokud je zadán žádnou návratovou hodnotu, je návratový typ void.</span><span class="sxs-lookup"><span data-stu-id="a83a1-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="a83a1-112">Informace o parametrech, včetně parametr názvu a typu.</span><span class="sxs-lookup"><span data-stu-id="a83a1-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="a83a1-113">(Volitelné)</span><span class="sxs-lookup"><span data-stu-id="a83a1-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="a83a1-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a83a1-114">Example</span></span>  
 <span data-ttu-id="a83a1-115">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="a83a1-115">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="a83a1-116">V CSDL, je jednou z implementací funkce modelu deklarované [import funkce](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d).</span><span class="sxs-lookup"><span data-stu-id="a83a1-116">In CSDL, one implementation of a model-declared function is a [function import](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d).</span></span> <span data-ttu-id="a83a1-117">Následující CSDL definuje kontejner entity s definicí importu funkce.</span><span class="sxs-lookup"><span data-stu-id="a83a1-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="a83a1-118">Všimněte si, že návratový typ pro funkci je neplatné, protože není zadán žádný návratový typ.</span><span class="sxs-lookup"><span data-stu-id="a83a1-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="a83a1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a83a1-119">See Also</span></span>  
 [<span data-ttu-id="a83a1-120">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="a83a1-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="a83a1-121">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="a83a1-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
