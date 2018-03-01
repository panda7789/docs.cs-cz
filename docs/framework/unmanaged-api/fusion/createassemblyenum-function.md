---
title: "CreateAssemblyEnum – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3719da442b2c2c589772a0bc19cec3efb4e6dace
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="5f7b5-102">CreateAssemblyEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="5f7b5-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="5f7b5-103">Získá odkazy [iassemblyenum –](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instanci, která můžete vytvořit výčet objektů v sestavení se zadaným [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5f7b5-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f7b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f7b5-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f7b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f7b5-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="5f7b5-106">[out] Ukazatel na umístění paměti, která obsahuje požadovanou `IAssemblyEnum` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="5f7b5-107">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="5f7b5-108">`pUnkReserved`musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="5f7b5-109">[v] `IAssemblyName` Požadovaný sestavení.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="5f7b5-110">Tento název se používá k filtrování výčtu.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="5f7b5-111">Může být null výčet všechna sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="5f7b5-112">[v] Příznaky úpravy chování enumerátor.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="5f7b5-113">Tento parametr obsahuje přesně jeden bit z [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="5f7b5-114">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="5f7b5-115">`pvReserved`musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f7b5-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f7b5-116">Remarks</span></span>  
 <span data-ttu-id="5f7b5-117">`dwFlags` Parametr obsahuje přesně jeden bit z `ASM_CACHE_FLAGS` výčtu.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f7b5-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f7b5-118">Requirements</span></span>  
 <span data-ttu-id="5f7b5-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f7b5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f7b5-120">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5f7b5-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5f7b5-121">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f7b5-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5f7b5-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f7b5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f7b5-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f7b5-123">See Also</span></span>  
 [<span data-ttu-id="5f7b5-124">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f7b5-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [<span data-ttu-id="5f7b5-125">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f7b5-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="5f7b5-126">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="5f7b5-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
