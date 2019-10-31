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
ms.openlocfilehash: 36d314211d95dff6648753f5d550a2cfd402a918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134049"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="674ee-102">ICorDebug::SetUnmanagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="674ee-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="674ee-103">Určuje objekt obslužné rutiny události pro nespravované události.</span><span class="sxs-lookup"><span data-stu-id="674ee-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="674ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="674ee-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="674ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="674ee-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="674ee-106">pro Ukazatel na objekt [ICorDebugUnmanagedCallback –](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) , který představuje obslužnou rutinu události pro nespravované události.</span><span class="sxs-lookup"><span data-stu-id="674ee-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="674ee-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="674ee-107">Remarks</span></span>  
 <span data-ttu-id="674ee-108">Objekt obslužné rutiny události pro nespravované události musí být nastaven po volání metody [ICorDebug:: Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) a před všemi voláními [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) nebo [ICorDebug::D ebugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="674ee-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="674ee-109">Pro starší účely však není nutné nastavovat objekt obslužné rutiny události pro nespravované události, dokud nebude vyvolána první nativní událost ladění.</span><span class="sxs-lookup"><span data-stu-id="674ee-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="674ee-110">Konkrétně, pokud `ICorDebug::CreateProcess` nastavil příznak CREATE_SUSPENDED, nativní události ladění nelze odeslat, dokud nebude obnoveno hlavní vlákno.</span><span class="sxs-lookup"><span data-stu-id="674ee-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="674ee-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="674ee-111">Requirements</span></span>  
 <span data-ttu-id="674ee-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="674ee-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="674ee-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="674ee-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="674ee-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="674ee-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="674ee-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="674ee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="674ee-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="674ee-116">See also</span></span>

- [<span data-ttu-id="674ee-117">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="674ee-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
