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
ms.openlocfilehash: 7c3251b2cf7a4d0d97df0e6ecc9b332e3ed8e500
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895330"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="09a23-102">ICorDebug::SetUnmanagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="09a23-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="09a23-103">Určuje objekt obslužné rutiny události pro nespravované události.</span><span class="sxs-lookup"><span data-stu-id="09a23-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09a23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09a23-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09a23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09a23-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="09a23-106">pro Ukazatel na objekt [ICorDebugUnmanagedCallback –](icordebugunmanagedcallback-interface.md) , který představuje obslužnou rutinu události pro nespravované události.</span><span class="sxs-lookup"><span data-stu-id="09a23-106">[in] A pointer to an [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09a23-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09a23-107">Remarks</span></span>  
 <span data-ttu-id="09a23-108">Objekt obslužné rutiny události pro nespravované události musí být nastaven po volání metody [ICorDebug:: Initialize](icordebug-initialize-method.md) a před všemi voláními [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) nebo [ICorDebug::D ebugactiveprocess](icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="09a23-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="09a23-109">Pro starší účely však není nutné nastavovat objekt obslužné rutiny události pro nespravované události, dokud nebude vyvolána první nativní událost ladění.</span><span class="sxs-lookup"><span data-stu-id="09a23-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="09a23-110">Konkrétně, pokud `ICorDebug::CreateProcess` má nastaven příznak CREATE_SUSPENDED, nativní události ladění nelze odeslat, dokud nebude obnoveno hlavní vlákno.</span><span class="sxs-lookup"><span data-stu-id="09a23-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09a23-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09a23-111">Requirements</span></span>  
 <span data-ttu-id="09a23-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09a23-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09a23-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="09a23-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09a23-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="09a23-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09a23-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09a23-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a23-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="09a23-116">See also</span></span>

- [<span data-ttu-id="09a23-117">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09a23-117">ICorDebug Interface</span></span>](icordebug-interface.md)
