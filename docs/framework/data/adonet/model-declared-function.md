---
title: model-declared function
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: 73e716f1c42dfbbb91dc6456212de2a331d7c4ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943915"
---
# <a name="model-declared-function"></a><span data-ttu-id="7400f-102">model-declared function</span><span class="sxs-lookup"><span data-stu-id="7400f-102">model-declared function</span></span>
<span data-ttu-id="7400f-103">*Modelem deklarovaná funkce* je funkce, která je deklarována v koncepčním modelu, ale není definována v tomto koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="7400f-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="7400f-104">Funkce může být definována v prostředí hostování nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="7400f-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="7400f-105">Například funkce deklarovaná modelem může být mapována na funkci, která je definována v databázi, čímž vystavuje funkce na straně serveru v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="7400f-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="7400f-106">Deklarace funkce deklarované modelem obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="7400f-106">The declaration of a model-declared function contains the following information:</span></span>  
  
- <span data-ttu-id="7400f-107">Název funkce</span><span class="sxs-lookup"><span data-stu-id="7400f-107">The name of the function.</span></span> <span data-ttu-id="7400f-108">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="7400f-108">(Required)</span></span>  
  
- <span data-ttu-id="7400f-109">Typ návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7400f-109">The type of the return value.</span></span> <span data-ttu-id="7400f-110">Volitelné</span><span class="sxs-lookup"><span data-stu-id="7400f-110">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7400f-111">Pokud není zadána žádná návratová hodnota, návratový typ je void.</span><span class="sxs-lookup"><span data-stu-id="7400f-111">If no return value is specified, the return type is void.</span></span>  
  
- <span data-ttu-id="7400f-112">Informace o parametrech, včetně názvu a typu parametru.</span><span class="sxs-lookup"><span data-stu-id="7400f-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="7400f-113">Volitelné</span><span class="sxs-lookup"><span data-stu-id="7400f-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="7400f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7400f-114">Example</span></span>  
 <span data-ttu-id="7400f-115">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="7400f-115">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="7400f-116">V CSDL jedna implementace modelem deklarované funkce je importovaná funkce (pomocí [elementu FunctionImport](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span><span class="sxs-lookup"><span data-stu-id="7400f-116">In CSDL, one implementation of a model-declared function is a function import (using the [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span></span> <span data-ttu-id="7400f-117">Následující CSDL definuje kontejner entit s definicí importu funkce.</span><span class="sxs-lookup"><span data-stu-id="7400f-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="7400f-118">Všimněte si, že návratový typ pro funkci je void, protože není zadaný žádný návratový typ.</span><span class="sxs-lookup"><span data-stu-id="7400f-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="7400f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7400f-119">See also</span></span>

- [<span data-ttu-id="7400f-120">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="7400f-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="7400f-121">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="7400f-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
