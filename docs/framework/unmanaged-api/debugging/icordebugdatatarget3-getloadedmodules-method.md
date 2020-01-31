---
title: Metoda ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: d4c22146422085daa4dc9d90ae5b3735a12500c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793558"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="11c19-102">Metoda ICorDebugDataTarget3::GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="11c19-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="11c19-103">Načte seznam modulů, které byly doposud načteny.</span><span class="sxs-lookup"><span data-stu-id="11c19-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11c19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11c19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11c19-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="11c19-106">pro Počet modulů, pro které jsou požadovány informace.</span><span class="sxs-lookup"><span data-stu-id="11c19-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="11c19-107">mimo Ukazatel na počet modulů, které informace byly vráceny.</span><span class="sxs-lookup"><span data-stu-id="11c19-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="11c19-108">mimo Ukazatel na pole objektů [Metoda ICorDebugLoadedModule](icordebugloadedmodule-interface.md) , které poskytují informace o načtených modulech.</span><span class="sxs-lookup"><span data-stu-id="11c19-108">[out] A pointer to an array of [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11c19-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11c19-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11c19-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="11c19-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11c19-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11c19-111">Requirements</span></span>  
 <span data-ttu-id="11c19-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11c19-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c19-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="11c19-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11c19-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="11c19-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11c19-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11c19-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c19-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11c19-116">See also</span></span>

- [<span data-ttu-id="11c19-117">ICorDebugDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11c19-117">ICorDebugDataTarget3 Interface</span></span>](icordebugdatatarget3-interface.md)
- [<span data-ttu-id="11c19-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="11c19-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
