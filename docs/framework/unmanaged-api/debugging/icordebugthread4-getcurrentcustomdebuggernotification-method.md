---
title: ICorDebugThread4::GetCurrentCustomDebuggerNotification – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f626ff6e562bd9bc94440f31e9470a45cc32cfbd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216324"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="5e6c7-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="5e6c7-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="5e6c7-103">Získá aktuální [icordebugmanagedcallback3::customnotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) objektu v aktuálním vláknu.</span><span class="sxs-lookup"><span data-stu-id="5e6c7-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="5e6c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e6c7-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="5e6c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e6c7-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="5e6c7-106">[out] Ukazatel na aktuální `ICorDebugManagedCallback3::CustomNotification` objektu v aktuálním vláknu.</span><span class="sxs-lookup"><span data-stu-id="5e6c7-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="5e6c7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e6c7-107">Remarks</span></span>

<span data-ttu-id="5e6c7-108">Hodnota `ppNotificationObject` má hodnotu null, pokud metoda není volána zevnitř `ICorDebugManagedCallback3::CustomNotification` zpětné volání, nebo pokud neexistuje žádné aktuální objekt oznámení.</span><span class="sxs-lookup"><span data-stu-id="5e6c7-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="5e6c7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e6c7-109">Requirements</span></span>

<span data-ttu-id="5e6c7-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e6c7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5e6c7-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e6c7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="5e6c7-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e6c7-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5e6c7-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e6c7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5e6c7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e6c7-114">See also</span></span>

- [<span data-ttu-id="5e6c7-115">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e6c7-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="5e6c7-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5e6c7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5e6c7-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="5e6c7-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
