---
title: "IMethodMalloc – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc
helpviewer_keywords: IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d246f329f80a76d2c93190fd663c7362418385f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="21a30-102">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21a30-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="21a30-103">Poskytuje metodu pro přidělení paměti pro nový tělo funkce (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="21a30-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21a30-104">`IMethodMalloc` Rozhraní je přidělení jednoduché paměti.</span><span class="sxs-lookup"><span data-stu-id="21a30-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="21a30-105">Umožní vám přidělit paměť, ale nechcete ho volné.</span><span class="sxs-lookup"><span data-stu-id="21a30-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21a30-106">Metody</span><span class="sxs-lookup"><span data-stu-id="21a30-106">Methods</span></span>  
  
|<span data-ttu-id="21a30-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="21a30-107">Method</span></span>|<span data-ttu-id="21a30-108">Popis</span><span class="sxs-lookup"><span data-stu-id="21a30-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21a30-109">ALLOC – metoda</span><span class="sxs-lookup"><span data-stu-id="21a30-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="21a30-110">Pokusí se přidělit zadanou velikost paměti pro nový tělo funkce MSIL.</span><span class="sxs-lookup"><span data-stu-id="21a30-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21a30-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21a30-111">Remarks</span></span>  
 <span data-ttu-id="21a30-112">Každý allocator je modulů a zajistí, že tělo funkce bude v kladné posun od základní modulu.</span><span class="sxs-lookup"><span data-stu-id="21a30-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="21a30-113">Paměť nad základní modulu může být drahocenný, takže přidělujícího modulu se má použít k přidělení paměti pouze pro tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="21a30-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21a30-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21a30-114">Requirements</span></span>  
 <span data-ttu-id="21a30-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21a30-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21a30-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21a30-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21a30-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21a30-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21a30-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21a30-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a30-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="21a30-119">See Also</span></span>  
 [<span data-ttu-id="21a30-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="21a30-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
