---
title: ICorDebugManagedCallback3::CustomNotification – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a2213c146374033c5a985a714352edad04f178a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762023"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="bd6b1-102">ICorDebugManagedCallback3::CustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="bd6b1-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="bd6b1-103">Označuje, že vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="bd6b1-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd6b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd6b1-104">Syntax</span></span>  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd6b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd6b1-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="bd6b1-106">[in] Ukazatel na vlákno, které vyvolá oznámení.</span><span class="sxs-lookup"><span data-stu-id="bd6b1-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="bd6b1-107">[in] Ukazatel na doménu aplikace, která obsahuje podproces, který vyvolá oznámení.</span><span class="sxs-lookup"><span data-stu-id="bd6b1-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd6b1-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bd6b1-108">Return Value</span></span>  
 <span data-ttu-id="bd6b1-109">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="bd6b1-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bd6b1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd6b1-110">HRESULT</span></span>|<span data-ttu-id="bd6b1-111">Popis</span><span class="sxs-lookup"><span data-stu-id="bd6b1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd6b1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd6b1-112">S_OK</span></span>|<span data-ttu-id="bd6b1-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="bd6b1-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="bd6b1-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="bd6b1-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd6b1-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd6b1-115">Remarks</span></span>  
 <span data-ttu-id="bd6b1-116">Následné volání [icordebugthread4::getcurrentcustomdebuggernotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) metoda načte objekt vlákna, která byla předána <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="bd6b1-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bd6b1-117">Typ objektu vlákna musí být dříve povolen voláním [icordebugprocess3::setenablecustomnotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="bd6b1-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="bd6b1-118">Ladicí program může číst parametry pro konkrétní typ z polí objekt vlákna a můžete ukládání odpovědí do polí.</span><span class="sxs-lookup"><span data-stu-id="bd6b1-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="bd6b1-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní ukládá žádné zásady na typy oznámení nebo jejich obsah a sémantika oznámení je výhradně kontrakt mezi ladicích programů, aplikací a rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bd6b1-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd6b1-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd6b1-120">Requirements</span></span>  
 <span data-ttu-id="bd6b1-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd6b1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd6b1-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd6b1-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd6b1-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd6b1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd6b1-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd6b1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd6b1-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd6b1-125">See also</span></span>

- [<span data-ttu-id="bd6b1-126">ICorDebugManagedCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd6b1-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="bd6b1-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="bd6b1-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bd6b1-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="bd6b1-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
