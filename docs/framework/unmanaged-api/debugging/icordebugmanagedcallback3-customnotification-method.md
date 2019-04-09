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
ms.openlocfilehash: b086c27d73324b4d834c9afa9e7aea20bf6d9148
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193574"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="c0234-102">ICorDebugManagedCallback3::CustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="c0234-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="c0234-103">Označuje, že vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="c0234-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0234-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0234-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0234-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0234-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="c0234-106">[in] Ukazatel na vlákno, které vyvolá oznámení.</span><span class="sxs-lookup"><span data-stu-id="c0234-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="c0234-107">[in] Ukazatel na doménu aplikace, která obsahuje podproces, který vyvolá oznámení.</span><span class="sxs-lookup"><span data-stu-id="c0234-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0234-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c0234-108">Return Value</span></span>  
 <span data-ttu-id="c0234-109">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="c0234-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c0234-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c0234-110">HRESULT</span></span>|<span data-ttu-id="c0234-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c0234-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c0234-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c0234-112">S_OK</span></span>|<span data-ttu-id="c0234-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="c0234-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="c0234-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="c0234-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0234-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0234-115">Remarks</span></span>  
 <span data-ttu-id="c0234-116">Následné volání [icordebugthread4::getcurrentcustomdebuggernotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) metoda načte objekt vlákna, která byla předána <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c0234-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c0234-117">Typ objektu vlákna musí být dříve povolen voláním [icordebugprocess3::setenablecustomnotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c0234-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="c0234-118">Ladicí program může číst parametry pro konkrétní typ z polí objekt vlákna a můžete ukládání odpovědí do polí.</span><span class="sxs-lookup"><span data-stu-id="c0234-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="c0234-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní ukládá žádné zásady na typy oznámení nebo jejich obsah a sémantika oznámení je výhradně kontrakt mezi ladicích programů, aplikací a rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0234-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0234-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0234-120">Requirements</span></span>  
 <span data-ttu-id="c0234-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0234-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0234-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0234-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0234-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0234-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c0234-124">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c0234-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c0234-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0234-125">See also</span></span>

- [<span data-ttu-id="c0234-126">ICorDebugManagedCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0234-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="c0234-127">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0234-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c0234-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="c0234-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
