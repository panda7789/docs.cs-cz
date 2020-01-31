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
ms.openlocfilehash: cafa1c99a8988c199d866796911d1983aabb7208
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785069"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="7b64e-102">ICorDebug::SetUnmanagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="7b64e-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="7b64e-103">Určuje objekt obslužné rutiny události pro nespravované události.</span><span class="sxs-lookup"><span data-stu-id="7b64e-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b64e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b64e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b64e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b64e-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="7b64e-106">pro Ukazatel na objekt [ICorDebugUnmanagedCallback –](icordebugunmanagedcallback-interface.md) , který představuje obslužnou rutinu události pro nespravované události.</span><span class="sxs-lookup"><span data-stu-id="7b64e-106">[in] A pointer to an [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b64e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b64e-107">Remarks</span></span>  
 <span data-ttu-id="7b64e-108">Objekt obslužné rutiny události pro nespravované události musí být nastaven po volání metody [ICorDebug:: Initialize](icordebug-initialize-method.md) a před všemi voláními [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) nebo [ICorDebug::D ebugactiveprocess](icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="7b64e-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="7b64e-109">Pro starší účely však není nutné nastavovat objekt obslužné rutiny události pro nespravované události, dokud nebude vyvolána první nativní událost ladění.</span><span class="sxs-lookup"><span data-stu-id="7b64e-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="7b64e-110">Konkrétně Pokud `ICorDebug::CreateProcess` nastavil příznak CREATE_SUSPENDED, nativní události ladění nelze odeslat, dokud nebude obnoveno hlavní vlákno.</span><span class="sxs-lookup"><span data-stu-id="7b64e-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b64e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b64e-111">Requirements</span></span>  
 <span data-ttu-id="7b64e-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b64e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b64e-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7b64e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b64e-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7b64e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b64e-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b64e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b64e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b64e-116">See also</span></span>

- [<span data-ttu-id="7b64e-117">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b64e-117">ICorDebug Interface</span></span>](icordebug-interface.md)
