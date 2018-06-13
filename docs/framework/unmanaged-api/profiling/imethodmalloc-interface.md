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
ms.openlocfilehash: b11cf0fadc9142ee291115cf9f0d84e6429834fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455114"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="60d2a-102">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60d2a-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="60d2a-103">Poskytuje metodu pro přidělení paměti pro nový tělo funkce (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="60d2a-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60d2a-104">`IMethodMalloc` Rozhraní je přidělení jednoduché paměti.</span><span class="sxs-lookup"><span data-stu-id="60d2a-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="60d2a-105">Umožní vám přidělit paměť, ale nechcete ho volné.</span><span class="sxs-lookup"><span data-stu-id="60d2a-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60d2a-106">Metody</span><span class="sxs-lookup"><span data-stu-id="60d2a-106">Methods</span></span>  
  
|<span data-ttu-id="60d2a-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="60d2a-107">Method</span></span>|<span data-ttu-id="60d2a-108">Popis</span><span class="sxs-lookup"><span data-stu-id="60d2a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60d2a-109">Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="60d2a-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="60d2a-110">Pokusí se přidělit zadanou velikost paměti pro nový tělo funkce MSIL.</span><span class="sxs-lookup"><span data-stu-id="60d2a-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60d2a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60d2a-111">Remarks</span></span>  
 <span data-ttu-id="60d2a-112">Každý allocator je modulů a zajistí, že tělo funkce bude v kladné posun od základní modulu.</span><span class="sxs-lookup"><span data-stu-id="60d2a-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="60d2a-113">Paměť nad základní modulu může být drahocenný, takže přidělujícího modulu se má použít k přidělení paměti pouze pro tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="60d2a-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60d2a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60d2a-114">Requirements</span></span>  
 <span data-ttu-id="60d2a-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60d2a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60d2a-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60d2a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60d2a-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60d2a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60d2a-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60d2a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60d2a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="60d2a-119">See Also</span></span>  
 [<span data-ttu-id="60d2a-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="60d2a-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
