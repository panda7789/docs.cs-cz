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
ms.openlocfilehash: e9cbf4551c2f8b183e9e6c37a74b13aff3a19ec1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860966"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="a1c69-102">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1c69-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="a1c69-103">Poskytuje metodu pro přidělení paměti pro nové tělo funkce jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="a1c69-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1c69-104">Rozhraní `IMethodMalloc` je jednoduché přidělování paměti.</span><span class="sxs-lookup"><span data-stu-id="a1c69-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="a1c69-105">Umožňuje přidělit paměť, ale neuvolňuje ji.</span><span class="sxs-lookup"><span data-stu-id="a1c69-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1c69-106">Metody</span><span class="sxs-lookup"><span data-stu-id="a1c69-106">Methods</span></span>  
  
|<span data-ttu-id="a1c69-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1c69-107">Method</span></span>|<span data-ttu-id="a1c69-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a1c69-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1c69-109">Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="a1c69-109">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="a1c69-110">Pokusí se přidělit určenou velikost paměti pro nové tělo funkce jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="a1c69-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1c69-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1c69-111">Remarks</span></span>  
 <span data-ttu-id="a1c69-112">Každé přidělování je specifické pro modul a zajišťuje, aby tělo funkce bylo kladné posun od základu modulu.</span><span class="sxs-lookup"><span data-stu-id="a1c69-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="a1c69-113">Paměť nad základem modulu může být úžasné, takže k přidělení paměti pro tělo funkce by se mělo použít přidělování.</span><span class="sxs-lookup"><span data-stu-id="a1c69-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1c69-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1c69-114">Requirements</span></span>  
 <span data-ttu-id="a1c69-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1c69-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1c69-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a1c69-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1c69-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a1c69-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1c69-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1c69-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c69-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1c69-119">See also</span></span>

- [<span data-ttu-id="a1c69-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a1c69-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
