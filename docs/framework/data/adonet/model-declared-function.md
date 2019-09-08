---
title: model-declared function
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: cb2fca52604bd57f25469f5621c292a27638c76f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794795"
---
# <a name="model-declared-function"></a><span data-ttu-id="3a553-102">model-declared function</span><span class="sxs-lookup"><span data-stu-id="3a553-102">model-declared function</span></span>
<span data-ttu-id="3a553-103">*Modelem deklarovaná funkce* je funkce, která je deklarována v koncepčním modelu, ale není definována v tomto koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="3a553-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="3a553-104">Funkce může být definována v prostředí hostování nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="3a553-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="3a553-105">Například funkce deklarovaná modelem může být mapována na funkci, která je definována v databázi, čímž vystavuje funkce na straně serveru v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="3a553-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="3a553-106">Deklarace funkce deklarované modelem obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="3a553-106">The declaration of a model-declared function contains the following information:</span></span>  
  
- <span data-ttu-id="3a553-107">Název funkce</span><span class="sxs-lookup"><span data-stu-id="3a553-107">The name of the function.</span></span> <span data-ttu-id="3a553-108">Požadovanou</span><span class="sxs-lookup"><span data-stu-id="3a553-108">(Required)</span></span>  
  
- <span data-ttu-id="3a553-109">Typ návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3a553-109">The type of the return value.</span></span> <span data-ttu-id="3a553-110">Volitelné</span><span class="sxs-lookup"><span data-stu-id="3a553-110">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3a553-111">Pokud není zadána žádná návratová hodnota, návratový typ je void.</span><span class="sxs-lookup"><span data-stu-id="3a553-111">If no return value is specified, the return type is void.</span></span>  
  
- <span data-ttu-id="3a553-112">Informace o parametrech, včetně názvu a typu parametru.</span><span class="sxs-lookup"><span data-stu-id="3a553-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="3a553-113">Volitelné</span><span class="sxs-lookup"><span data-stu-id="3a553-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a553-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a553-114">Example</span></span>  
 <span data-ttu-id="3a553-115">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="3a553-115">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="3a553-116">V CSDL jedna implementace modelem deklarované funkce je importovaná funkce (pomocí [elementu FunctionImport](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span><span class="sxs-lookup"><span data-stu-id="3a553-116">In CSDL, one implementation of a model-declared function is a function import (using the [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span></span> <span data-ttu-id="3a553-117">Následující CSDL definuje kontejner entit s definicí importu funkce.</span><span class="sxs-lookup"><span data-stu-id="3a553-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="3a553-118">Všimněte si, že návratový typ pro funkci je void, protože není zadaný žádný návratový typ.</span><span class="sxs-lookup"><span data-stu-id="3a553-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="3a553-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a553-119">See also</span></span>

- [<span data-ttu-id="3a553-120">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="3a553-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="3a553-121">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="3a553-121">Entity Data Model</span></span>](entity-data-model.md)
