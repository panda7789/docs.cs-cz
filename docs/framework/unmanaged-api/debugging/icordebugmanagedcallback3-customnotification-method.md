---
title: "ICorDebugManagedCallback3::CustomNotification – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c42443b0d1e355d4233909357c341763298160e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="b3aa1-102">ICorDebugManagedCallback3::CustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="b3aa1-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="b3aa1-103">Označuje, že bylo vyvoláno upozornění vlastní ladicí program.</span><span class="sxs-lookup"><span data-stu-id="b3aa1-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3aa1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3aa1-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3aa1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3aa1-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="b3aa1-106">[v] Ukazatel na vlákno, které vyvolá oznámení.</span><span class="sxs-lookup"><span data-stu-id="b3aa1-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="b3aa1-107">[v] Ukazatel na doménu aplikace, která obsahuje vlákno, které vyvolá oznámení.</span><span class="sxs-lookup"><span data-stu-id="b3aa1-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3aa1-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b3aa1-108">Return Value</span></span>  
 <span data-ttu-id="b3aa1-109">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="b3aa1-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b3aa1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3aa1-110">HRESULT</span></span>|<span data-ttu-id="b3aa1-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b3aa1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3aa1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3aa1-112">S_OK</span></span>|<span data-ttu-id="b3aa1-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="b3aa1-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b3aa1-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="b3aa1-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3aa1-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3aa1-115">Remarks</span></span>  
 <span data-ttu-id="b3aa1-116">Další volání [icordebugthread4::getcurrentcustomdebuggernotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) metoda načte objekt přístup z více vláken, který byl předán <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="b3aa1-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b3aa1-117">Typ objektu vlákno musí být dříve povolen voláním [icordebugprocess3::setenablecustomnotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="b3aa1-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="b3aa1-118">Ladicí program může číst typ specifické parametry od polí objektu vláken a můžete ukládání odpovědí do pole.</span><span class="sxs-lookup"><span data-stu-id="b3aa1-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="b3aa1-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní ukládá žádné zásady pro typy oznámení nebo jejich obsah a sémantika oznámení se týkají výhradně kontraktu mezi ladicí programy, aplikace a rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b3aa1-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3aa1-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3aa1-120">Requirements</span></span>  
 <span data-ttu-id="b3aa1-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3aa1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3aa1-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3aa1-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3aa1-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3aa1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3aa1-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3aa1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3aa1-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3aa1-125">See Also</span></span>  
 [<span data-ttu-id="b3aa1-126">ICorDebugManagedCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3aa1-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 [<span data-ttu-id="b3aa1-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b3aa1-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b3aa1-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="b3aa1-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
