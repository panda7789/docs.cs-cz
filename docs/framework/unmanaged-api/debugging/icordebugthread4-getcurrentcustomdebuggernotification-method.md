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
ms.openlocfilehash: 0529dee17469018e872951740a5899ef8664300a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420999"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="f5e2f-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="f5e2f-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>
<span data-ttu-id="f5e2f-103">Získá aktuální [icordebugmanagedcallback3::customnotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) objekt na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="f5e2f-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5e2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5e2f-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCustomDebuggerNotification(  
    [out] ICorDebugValue **ppNotificationObject  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5e2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5e2f-105">Parameters</span></span>  
 `ppNOtificationObject`  
 <span data-ttu-id="f5e2f-106">[out] Ukazatel na aktuální `ICorDebugManagedCallback3::CustomNotification` objekt na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="f5e2f-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5e2f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5e2f-107">Remarks</span></span>  
 <span data-ttu-id="f5e2f-108">Hodnota `ppNotificationObject` má hodnotu null, pokud metoda není volána v rámci `ICorDebugManagedCallback3::CustomNotification` zpětné volání, nebo pokud neexistuje žádný aktuální objekt oznámení.</span><span class="sxs-lookup"><span data-stu-id="f5e2f-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5e2f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5e2f-109">Requirements</span></span>  
 <span data-ttu-id="f5e2f-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5e2f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5e2f-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5e2f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5e2f-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5e2f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5e2f-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5e2f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e2f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5e2f-114">See Also</span></span>  
 [<span data-ttu-id="f5e2f-115">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5e2f-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="f5e2f-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f5e2f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f5e2f-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="f5e2f-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
