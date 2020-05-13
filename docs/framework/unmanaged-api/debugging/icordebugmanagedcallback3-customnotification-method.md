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
ms.openlocfilehash: 8a4620e591cc80efb5c0fd53b0edf3a35849c421
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209757"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="30425-102">ICorDebugManagedCallback3::CustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="30425-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="30425-103">Indikuje, že se aktivovalo oznámení vlastního ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="30425-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30425-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30425-104">Syntax</span></span>  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30425-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30425-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="30425-106">pro Ukazatel na vlákno, které vyvolalo oznámení.</span><span class="sxs-lookup"><span data-stu-id="30425-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="30425-107">pro Ukazatel na doménu aplikace obsahující vlákno, které vyvolalo oznámení.</span><span class="sxs-lookup"><span data-stu-id="30425-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30425-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="30425-108">Return Value</span></span>  
 <span data-ttu-id="30425-109">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="30425-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="30425-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30425-110">HRESULT</span></span>|<span data-ttu-id="30425-111">Popis</span><span class="sxs-lookup"><span data-stu-id="30425-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30425-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="30425-112">S_OK</span></span>|<span data-ttu-id="30425-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="30425-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="30425-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="30425-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30425-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30425-115">Remarks</span></span>  
 <span data-ttu-id="30425-116">Následné volání metody [ICorDebugThread4:: GetCurrentCustomDebuggerNotification –](icordebugthread4-getcurrentcustomdebuggernotification-method.md) načte objekt vlákna, který byl předán <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metodě.</span><span class="sxs-lookup"><span data-stu-id="30425-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="30425-117">Typ objektu vlákna musí být dříve povolen voláním metody [ICorDebugProcess3 –:: SetEnableCustomNotification –](icordebugprocess3-setenablecustomnotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="30425-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="30425-118">Ladicí program může číst parametry specifické pro typ z polí objektu vlákna a může ukládat odpovědi do polí.</span><span class="sxs-lookup"><span data-stu-id="30425-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="30425-119">Rozhraní [ICorDebug](icordebug-interface.md) neukládá žádné zásady na typy oznámení nebo jejich obsah a sémantika oznámení je výhradně kontraktem mezi ladicími programy, aplikacemi a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30425-119">The [ICorDebug](icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30425-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30425-120">Requirements</span></span>  
 <span data-ttu-id="30425-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30425-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30425-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="30425-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30425-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="30425-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30425-124">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30425-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30425-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="30425-125">See also</span></span>

- [<span data-ttu-id="30425-126">ICorDebugManagedCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30425-126">ICorDebugManagedCallback3 Interface</span></span>](icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="30425-127">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30425-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="30425-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="30425-128">Debugging</span></span>](index.md)
