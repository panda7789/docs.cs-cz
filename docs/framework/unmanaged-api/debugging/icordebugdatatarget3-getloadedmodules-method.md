---
title: Metoda ICorDebugDataTarget3::GetLoadedModules
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3db6449abee4eed4a8e5d6c691834c52dc0717e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="20b39-102">Metoda ICorDebugDataTarget3::GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="20b39-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="20b39-103">Získá seznam modulů, které byly načteny dosavadní práce.</span><span class="sxs-lookup"><span data-stu-id="20b39-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20b39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20b39-104">Syntax</span></span>  
  
```  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20b39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20b39-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="20b39-106">[v] Počet modulů, pro které je požadované informace.</span><span class="sxs-lookup"><span data-stu-id="20b39-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="20b39-107">[out] Ukazatel na počet modulů, které se vrátí informace.</span><span class="sxs-lookup"><span data-stu-id="20b39-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="20b39-108">[out] Ukazatel na pole [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objekty, které obsahují informace o načíst moduly.</span><span class="sxs-lookup"><span data-stu-id="20b39-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20b39-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20b39-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20b39-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="20b39-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20b39-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20b39-111">Requirements</span></span>  
 <span data-ttu-id="20b39-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20b39-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20b39-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20b39-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20b39-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20b39-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20b39-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20b39-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20b39-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="20b39-116">See Also</span></span>  
 [<span data-ttu-id="20b39-117">ICorDebugDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20b39-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 [<span data-ttu-id="20b39-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="20b39-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
