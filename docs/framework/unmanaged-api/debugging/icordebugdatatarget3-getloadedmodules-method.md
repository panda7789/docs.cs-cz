---
title: Metoda ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 464fd9ac44d6ba5717dbc4ecfbe03b6e6ad52276
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789716"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="b4827-102">Metoda ICorDebugDataTarget3::GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="b4827-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="b4827-103">Získá seznam modulů, které zatím byly načteny.</span><span class="sxs-lookup"><span data-stu-id="b4827-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4827-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4827-104">Syntax</span></span>  
  
```  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4827-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4827-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="b4827-106">[in] Počet modulů, pro které je požadované informace.</span><span class="sxs-lookup"><span data-stu-id="b4827-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="b4827-107">[out] Ukazatel na počet modulů, které se vrátí informace.</span><span class="sxs-lookup"><span data-stu-id="b4827-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="b4827-108">[out] Ukazatel na pole [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objekty, které poskytují informace o načtené moduly.</span><span class="sxs-lookup"><span data-stu-id="b4827-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4827-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4827-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4827-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b4827-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4827-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4827-111">Requirements</span></span>  
 <span data-ttu-id="b4827-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4827-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4827-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4827-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4827-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4827-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4827-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4827-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4827-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4827-116">See also</span></span>

- [<span data-ttu-id="b4827-117">ICorDebugDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4827-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [<span data-ttu-id="b4827-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b4827-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
