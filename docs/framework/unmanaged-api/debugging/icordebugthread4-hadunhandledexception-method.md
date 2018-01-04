---
title: "ICorDebugThread4::HadUnhandledException – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.HadUnhandledException Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a79d06f0a65facfbaa821d3dd6af547fd3d0305
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="b40e9-102">ICorDebugThread4::HadUnhandledException – metoda</span><span class="sxs-lookup"><span data-stu-id="b40e9-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="b40e9-103">Určuje, zda vlákno někdy došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="b40e9-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b40e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b40e9-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b40e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b40e9-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="b40e9-106">[out] Ukazatel na adresu seřazený výčet [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="b40e9-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b40e9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b40e9-107">Return Value</span></span>  
 <span data-ttu-id="b40e9-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="b40e9-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b40e9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b40e9-109">HRESULT</span></span>|<span data-ttu-id="b40e9-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b40e9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b40e9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b40e9-111">S_OK</span></span>|<span data-ttu-id="b40e9-112">Vlákno došlo k neošetřené výjimce od svého vytvoření.</span><span class="sxs-lookup"><span data-stu-id="b40e9-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="b40e9-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b40e9-113">S_FALSE</span></span>|<span data-ttu-id="b40e9-114">Vlákno nikdy došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="b40e9-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b40e9-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b40e9-115">Remarks</span></span>  
 <span data-ttu-id="b40e9-116">Tato metoda určuje, zda vlákno někdy došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="b40e9-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="b40e9-117">V čase se aktivuje zpětného volání neošetřené výjimky nebo nativní JIT – připojené se zahájí, tato metoda záruku, že se vrátíte S_OK.</span><span class="sxs-lookup"><span data-stu-id="b40e9-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="b40e9-118">Neexistuje žádná záruka, [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) metoda vrátí neošetřené výjimce; však bude, pokud proces nebyl ještě pokračuje po získání zpětné volání neošetřené výjimky nebo po nativní JIT – připojené.</span><span class="sxs-lookup"><span data-stu-id="b40e9-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="b40e9-119">Kromě toho je možné (Ačkoli je to pravděpodobně) má více než jedno vlákno s k neošetřené výjimce v době nativní JIT – připojené se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="b40e9-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="b40e9-120">V takovém případě není žádný způsob, jak určit, která výjimka aktivaci JIT – připojené.</span><span class="sxs-lookup"><span data-stu-id="b40e9-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b40e9-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b40e9-121">Requirements</span></span>  
 <span data-ttu-id="b40e9-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b40e9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b40e9-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b40e9-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b40e9-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b40e9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b40e9-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b40e9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b40e9-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b40e9-126">See Also</span></span>  
 [<span data-ttu-id="b40e9-127">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b40e9-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="b40e9-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b40e9-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b40e9-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="b40e9-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
