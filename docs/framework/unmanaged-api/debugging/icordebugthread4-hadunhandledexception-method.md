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
ms.openlocfilehash: d9f0eff35dbe0058398d2d1c851ef85effa9cd28
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122413"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="ea70d-102">ICorDebugThread4::HadUnhandledException – metoda</span><span class="sxs-lookup"><span data-stu-id="ea70d-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="ea70d-103">Označuje, zda má vlákno někdy neošetřenou výjimku.</span><span class="sxs-lookup"><span data-stu-id="ea70d-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea70d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea70d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea70d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea70d-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="ea70d-106">mimo Ukazatel na adresu seřazeného výčtu struktur [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="ea70d-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea70d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ea70d-107">Return Value</span></span>  
 <span data-ttu-id="ea70d-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="ea70d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ea70d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea70d-109">HRESULT</span></span>|<span data-ttu-id="ea70d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ea70d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea70d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea70d-111">S_OK</span></span>|<span data-ttu-id="ea70d-112">Vlákno mělo neošetřenou výjimku od jejího vytvoření.</span><span class="sxs-lookup"><span data-stu-id="ea70d-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="ea70d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ea70d-113">S_FALSE</span></span>|<span data-ttu-id="ea70d-114">Vlákno nikdy nemá neošetřenou výjimku.</span><span class="sxs-lookup"><span data-stu-id="ea70d-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea70d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea70d-115">Remarks</span></span>  
 <span data-ttu-id="ea70d-116">Tato metoda označuje, zda vlákno má někdy neošetřenou výjimku.</span><span class="sxs-lookup"><span data-stu-id="ea70d-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="ea70d-117">V době spuštění neošetřeného zpětného volání výjimky nebo při zahájení nativního připojení JIT je zaručeno, že tato metoda vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="ea70d-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="ea70d-118">Není zaručeno, že metoda [ICorDebugThread. GetCurrentException –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) vrátí neošetřenou výjimku; Nicméně pokud proces ještě nepokračoval po získání neošetřeného zpětného volání výjimky nebo po nativním připojení JIT.</span><span class="sxs-lookup"><span data-stu-id="ea70d-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="ea70d-119">Kromě toho je možné (i když nepravděpodobné), aby měl více než jedno vlákno s neošetřenou výjimkou v době, kdy se spustí nativní JIT – připojit.</span><span class="sxs-lookup"><span data-stu-id="ea70d-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="ea70d-120">V takovém případě neexistuje způsob, jak určit, která výjimka aktivovala připojení JIT.</span><span class="sxs-lookup"><span data-stu-id="ea70d-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea70d-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea70d-121">Requirements</span></span>  
 <span data-ttu-id="ea70d-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea70d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea70d-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea70d-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea70d-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ea70d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea70d-125">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea70d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea70d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea70d-126">See also</span></span>

- [<span data-ttu-id="ea70d-127">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea70d-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="ea70d-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ea70d-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ea70d-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="ea70d-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
