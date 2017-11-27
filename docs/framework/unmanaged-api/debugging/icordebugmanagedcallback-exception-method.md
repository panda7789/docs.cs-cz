---
title: "ICorDebugManagedCallback::Exception – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 550b4961cb082ca6ee745b1d998a6fa95a22ace3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="70c9e-102">ICorDebugManagedCallback::Exception – metoda</span><span class="sxs-lookup"><span data-stu-id="70c9e-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="70c9e-103">Upozorní ladicí program, že byla vyvolána výjimka ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="70c9e-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70c9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70c9e-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70c9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70c9e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="70c9e-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, ve kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="70c9e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="70c9e-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, ve kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="70c9e-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="70c9e-108">[v] Pokud je tato hodnota `false`, výjimka nebyl dosud byla zpracovaná aplikace; jinak, výjimka neošetřených a proces ukončí.</span><span class="sxs-lookup"><span data-stu-id="70c9e-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70c9e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70c9e-109">Remarks</span></span>  
 <span data-ttu-id="70c9e-110">Konkrétní výjimky mohou být načteny z objektu přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="70c9e-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70c9e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70c9e-111">Requirements</span></span>  
 <span data-ttu-id="70c9e-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70c9e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70c9e-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70c9e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70c9e-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70c9e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70c9e-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70c9e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c9e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="70c9e-116">See Also</span></span>  
 [<span data-ttu-id="70c9e-117">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="70c9e-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
