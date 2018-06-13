---
title: Metoda ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1089668aa19747f5f694360ebb87098e2df9ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405548"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="8d483-102">Metoda ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="8d483-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="8d483-103">Získá objekt spravovaného z COM ukazatel obálka volatelná aplikacemi (doleva).</span><span class="sxs-lookup"><span data-stu-id="8d483-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d483-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d483-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d483-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d483-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="8d483-106">[v] Obálka volatelná aplikacemi (doleva) ukazatel COM.</span><span class="sxs-lookup"><span data-stu-id="8d483-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="8d483-107">[out] Ukazatel na adresu "ICorDebugValue" objekt, který představuje spravovaný objekt, který odpovídá dané ukazatele doleva.</span><span class="sxs-lookup"><span data-stu-id="8d483-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d483-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d483-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d483-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d483-109">Requirements</span></span>  
 <span data-ttu-id="8d483-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d483-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d483-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d483-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d483-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d483-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d483-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d483-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d483-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d483-114">See Also</span></span>  
 [<span data-ttu-id="8d483-115">ICorDebugAppDomain4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d483-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 [<span data-ttu-id="8d483-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8d483-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
