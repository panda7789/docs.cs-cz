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
ms.openlocfilehash: c234b3953130f53d7e6b583cd92670149a70689b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168859"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="598b6-102">ICorDebug::SetUnmanagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="598b6-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="598b6-103">Určuje objekt obslužné rutiny události pro nespravované události.</span><span class="sxs-lookup"><span data-stu-id="598b6-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="598b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="598b6-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="598b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="598b6-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="598b6-106">[in] Ukazatel [icordebugunmanagedcallback –](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) objekt, který reprezentuje obslužnou rutinu události pro nespravované události.</span><span class="sxs-lookup"><span data-stu-id="598b6-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="598b6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="598b6-107">Remarks</span></span>  
 <span data-ttu-id="598b6-108">Obslužná rutina události objektu pro nespravované události musí být nastavena po volání [icordebug::Initialize –](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) a před všechna volání do [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) nebo [icordebug::DebugActiveProcess – ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="598b6-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="598b6-109">V zájmu starší verze však není nutné nastavit objekt obslužné rutiny události pro nespravované události, dokud se vyvolá první událost nativní ladění.</span><span class="sxs-lookup"><span data-stu-id="598b6-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="598b6-110">Konkrétně Pokud `ICorDebug::CreateProcess` nastavil příznak CREATE_SUSPENDED nativní ladění události nelze zpracovat, dokud nebude obnoven hlavního vlákna.</span><span class="sxs-lookup"><span data-stu-id="598b6-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="598b6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="598b6-111">Requirements</span></span>  
 <span data-ttu-id="598b6-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="598b6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="598b6-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="598b6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="598b6-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="598b6-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="598b6-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="598b6-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="598b6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="598b6-116">See also</span></span>

- [<span data-ttu-id="598b6-117">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="598b6-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
