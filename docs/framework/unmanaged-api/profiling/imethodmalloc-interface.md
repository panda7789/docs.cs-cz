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
ms.openlocfilehash: c67ce15175f8667139f99cec1ed17531eab473e1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935649"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="e122e-102">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e122e-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="e122e-103">Poskytuje metodu pro přidělení paměti pro nové tělo funkce jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="e122e-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e122e-104">`IMethodMalloc` Rozhraní je jednoduchý Alokátor paměti.</span><span class="sxs-lookup"><span data-stu-id="e122e-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="e122e-105">Umožňuje přidělit paměť, ale neuvolňuje ji.</span><span class="sxs-lookup"><span data-stu-id="e122e-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e122e-106">Metody</span><span class="sxs-lookup"><span data-stu-id="e122e-106">Methods</span></span>  
  
|<span data-ttu-id="e122e-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="e122e-107">Method</span></span>|<span data-ttu-id="e122e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e122e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e122e-109">Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="e122e-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="e122e-110">Pokusí se přidělit určenou velikost paměti pro nové tělo funkce jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="e122e-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e122e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e122e-111">Remarks</span></span>  
 <span data-ttu-id="e122e-112">Každé přidělování je specifické pro modul a zajišťuje, aby tělo funkce bylo kladné posun od základu modulu.</span><span class="sxs-lookup"><span data-stu-id="e122e-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="e122e-113">Paměť nad základem modulu může být úžasné, takže k přidělení paměti pro tělo funkce by se mělo použít přidělování.</span><span class="sxs-lookup"><span data-stu-id="e122e-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e122e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e122e-114">Requirements</span></span>  
 <span data-ttu-id="e122e-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e122e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e122e-116">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e122e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e122e-117">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e122e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e122e-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e122e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e122e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e122e-119">See also</span></span>

- [<span data-ttu-id="e122e-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e122e-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
