---
title: Metoda ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9eeb0b80ba691d813e3193f7ae746129c6725e1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506534"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="41300-102">Metoda ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="41300-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="41300-103">Získá z ukazatele (CCW) obálka volatelná aplikacemi COM spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="41300-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41300-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41300-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41300-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41300-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="41300-106">[in] Ukazatel (CCW) obálka volatelná aplikacemi COM.</span><span class="sxs-lookup"><span data-stu-id="41300-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="41300-107">[out] Ukazatel na adresu objektu "ICorDebugValue", který představuje spravovaný objekt, který odpovídá na daný objekt CCW ukazatel.</span><span class="sxs-lookup"><span data-stu-id="41300-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41300-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41300-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41300-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41300-109">Requirements</span></span>  
 <span data-ttu-id="41300-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41300-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41300-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41300-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41300-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41300-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41300-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41300-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41300-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41300-114">See also</span></span>
- [<span data-ttu-id="41300-115">ICorDebugAppDomain4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41300-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="41300-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="41300-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
