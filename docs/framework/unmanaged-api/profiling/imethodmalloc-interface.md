---
title: IMethodMalloc – rozhraní
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee825da1f3f0fd72a3b47b48783f0f344af99b65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969803"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="54209-102">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54209-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="54209-103">Poskytuje metodu, jak přidělit paměť pro nové tělo funkce Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="54209-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54209-104">`IMethodMalloc` Rozhraní je jednoduché paměti alokátoru.</span><span class="sxs-lookup"><span data-stu-id="54209-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="54209-105">Je možné přidělit paměť, ale nechcete ho zdarma.</span><span class="sxs-lookup"><span data-stu-id="54209-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54209-106">Metody</span><span class="sxs-lookup"><span data-stu-id="54209-106">Methods</span></span>  
  
|<span data-ttu-id="54209-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="54209-107">Method</span></span>|<span data-ttu-id="54209-108">Popis</span><span class="sxs-lookup"><span data-stu-id="54209-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54209-109">Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="54209-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="54209-110">Pokusí se přidělit zadanou velikost paměti pro nové tělo funkce jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="54209-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54209-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54209-111">Remarks</span></span>  
 <span data-ttu-id="54209-112">Každý allocator je modulů a zajistí, že tělo funkce bude kladné posunem od báze modulu.</span><span class="sxs-lookup"><span data-stu-id="54209-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="54209-113">Paměť nad základní modul může být účely, proto alokátoru by měla sloužit pouze pro tělo funkce přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="54209-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54209-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54209-114">Requirements</span></span>  
 <span data-ttu-id="54209-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54209-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54209-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54209-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54209-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54209-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54209-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54209-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54209-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54209-119">See also</span></span>

- [<span data-ttu-id="54209-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="54209-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
