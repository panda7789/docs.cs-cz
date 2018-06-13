---
title: ICorDebugThread4::HadUnhandledException – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8215ddfd0f59f835d0b0dcd278b8cae9c12027d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422107"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="52855-102">ICorDebugThread4::HadUnhandledException – metoda</span><span class="sxs-lookup"><span data-stu-id="52855-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="52855-103">Určuje, zda vlákno někdy došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="52855-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52855-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52855-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52855-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52855-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="52855-106">[out] Ukazatel na adresu seřazený výčet [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="52855-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52855-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="52855-107">Return Value</span></span>  
 <span data-ttu-id="52855-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="52855-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="52855-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52855-109">HRESULT</span></span>|<span data-ttu-id="52855-110">Popis</span><span class="sxs-lookup"><span data-stu-id="52855-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52855-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="52855-111">S_OK</span></span>|<span data-ttu-id="52855-112">Vlákno došlo k neošetřené výjimce od svého vytvoření.</span><span class="sxs-lookup"><span data-stu-id="52855-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="52855-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="52855-113">S_FALSE</span></span>|<span data-ttu-id="52855-114">Vlákno nikdy došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="52855-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52855-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52855-115">Remarks</span></span>  
 <span data-ttu-id="52855-116">Tato metoda určuje, zda vlákno někdy došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="52855-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="52855-117">V čase se aktivuje zpětného volání neošetřené výjimky nebo nativní JIT – připojené se zahájí, tato metoda záruku, že se vrátíte S_OK.</span><span class="sxs-lookup"><span data-stu-id="52855-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="52855-118">Neexistuje žádná záruka, [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) metoda vrátí neošetřené výjimce; však bude, pokud proces nebyl ještě pokračuje po získání zpětné volání neošetřené výjimky nebo po nativní JIT – připojené.</span><span class="sxs-lookup"><span data-stu-id="52855-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="52855-119">Kromě toho je možné (Ačkoli je to pravděpodobně) má více než jedno vlákno s k neošetřené výjimce v době nativní JIT – připojené se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="52855-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="52855-120">V takovém případě není žádný způsob, jak určit, která výjimka aktivaci JIT – připojené.</span><span class="sxs-lookup"><span data-stu-id="52855-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52855-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52855-121">Requirements</span></span>  
 <span data-ttu-id="52855-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52855-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52855-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52855-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52855-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52855-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52855-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52855-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52855-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="52855-126">See Also</span></span>  
 [<span data-ttu-id="52855-127">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52855-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="52855-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="52855-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="52855-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="52855-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
