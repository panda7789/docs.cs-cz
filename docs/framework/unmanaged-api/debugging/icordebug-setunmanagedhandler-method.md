---
title: ICorDebug::SetUnmanagedHandler – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1be18d374bad07b590096acac985812c2e2ed9b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407580"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="78457-102">ICorDebug::SetUnmanagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="78457-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="78457-103">Určuje objekt obslužné rutiny události pro události se nespravované.</span><span class="sxs-lookup"><span data-stu-id="78457-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78457-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78457-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78457-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78457-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="78457-106">[v] Ukazatel na [icordebugunmanagedcallback –](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) objekt, který reprezentuje obslužnou rutinu události pro nespravované události.</span><span class="sxs-lookup"><span data-stu-id="78457-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78457-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78457-107">Remarks</span></span>  
 <span data-ttu-id="78457-108">Obslužné rutiny události objektu pro nespravované události musí být nastavena po volání [icordebug::Initialize –](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) a před volání [icordebug::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) nebo [icordebug::DebugActiveProcess – ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="78457-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="78457-109">Pro starší verze účely, ale není nutné nastavit objekt obslužné rutiny události pro nespravované události, dokud první nativní ladění událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="78457-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="78457-110">Konkrétně Pokud `ICorDebug::CreateProcess` nastavil příznak CREATE_SUSPENDED nativní ladění události nelze odeslat, dokud je obnoveno hlavního vlákna.</span><span class="sxs-lookup"><span data-stu-id="78457-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78457-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78457-111">Requirements</span></span>  
 <span data-ttu-id="78457-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78457-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78457-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78457-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78457-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78457-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78457-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78457-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78457-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="78457-116">See Also</span></span>  
 [<span data-ttu-id="78457-117">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78457-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
