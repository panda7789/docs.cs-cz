---
title: Metoda ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c51ce8ff76e0fc1588cdd136de83b77dcab0f10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413492"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="27c35-102">Metoda ICorDebugDataTarget3::GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="27c35-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="27c35-103">Získá seznam modulů, které byly načteny dosavadní práce.</span><span class="sxs-lookup"><span data-stu-id="27c35-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27c35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27c35-104">Syntax</span></span>  
  
```  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27c35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27c35-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="27c35-106">[v] Počet modulů, pro které je požadované informace.</span><span class="sxs-lookup"><span data-stu-id="27c35-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="27c35-107">[out] Ukazatel na počet modulů, které se vrátí informace.</span><span class="sxs-lookup"><span data-stu-id="27c35-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="27c35-108">[out] Ukazatel na pole [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objekty, které obsahují informace o načíst moduly.</span><span class="sxs-lookup"><span data-stu-id="27c35-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27c35-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27c35-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27c35-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="27c35-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27c35-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27c35-111">Requirements</span></span>  
 <span data-ttu-id="27c35-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27c35-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27c35-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27c35-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27c35-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27c35-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27c35-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27c35-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27c35-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="27c35-116">See Also</span></span>  
 [<span data-ttu-id="27c35-117">ICorDebugDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27c35-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 [<span data-ttu-id="27c35-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="27c35-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
