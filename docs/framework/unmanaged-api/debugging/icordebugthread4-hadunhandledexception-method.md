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
ms.openlocfilehash: 12433786f353212c1ffbd57e9bf526c3ecc60e9a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163622"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="56e2c-102">ICorDebugThread4::HadUnhandledException – metoda</span><span class="sxs-lookup"><span data-stu-id="56e2c-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="56e2c-103">Určuje, zda vlákna někdy došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="56e2c-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56e2c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56e2c-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="56e2c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56e2c-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="56e2c-106">[out] Ukazatel na adresu seřazený výčet [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="56e2c-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56e2c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="56e2c-107">Return Value</span></span>  
 <span data-ttu-id="56e2c-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="56e2c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="56e2c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56e2c-109">HRESULT</span></span>|<span data-ttu-id="56e2c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="56e2c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56e2c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="56e2c-111">S_OK</span></span>|<span data-ttu-id="56e2c-112">Vlákna došlo k neošetřené výjimce od jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="56e2c-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="56e2c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="56e2c-113">S_FALSE</span></span>|<span data-ttu-id="56e2c-114">Vlákna nikdy došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="56e2c-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56e2c-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56e2c-115">Remarks</span></span>  
 <span data-ttu-id="56e2c-116">Tato metoda určuje, zda vlákna někdy došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="56e2c-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="56e2c-117">Časem se aktivuje zpětného volání neošetřené výjimky nebo nativní připojit JIT je zahájeno, tato metoda je zaručeno, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="56e2c-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="56e2c-118">Neexistuje žádná záruka, který [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) metoda vrátí neošetřená výjimka; však bude, pokud proces nebyl dosud pokračuje po získání zpětné volání neošetřené výjimky nebo po nativní JIT připojení.</span><span class="sxs-lookup"><span data-stu-id="56e2c-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="56e2c-119">Kromě toho je možné (ale nepravděpodobné) mít více než jedno vlákno s neošetřenou výjimkou v době nativní připojit JIT se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="56e2c-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="56e2c-120">V takovém případě neexistuje žádný způsob, jak určit výjimky aktivuje připojit JIT.</span><span class="sxs-lookup"><span data-stu-id="56e2c-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56e2c-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56e2c-121">Requirements</span></span>  
 <span data-ttu-id="56e2c-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56e2c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56e2c-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56e2c-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56e2c-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56e2c-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="56e2c-125">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="56e2c-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56e2c-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56e2c-126">See also</span></span>

- [<span data-ttu-id="56e2c-127">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56e2c-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="56e2c-128">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56e2c-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="56e2c-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="56e2c-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
