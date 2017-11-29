---
title: "ICorDebugManagedCallback::ExitProcess – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ExitProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ff80462c722a84ef68ac8c6703ded3e7138a1939
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="2fb26-102">ICorDebugManagedCallback::ExitProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="2fb26-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="2fb26-103">Upozorní ladicího programu, proces byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="2fb26-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fb26-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fb26-104">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2fb26-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fb26-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="2fb26-106">[v] Ukazatel na ICorDebugProcess objekt, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="2fb26-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fb26-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fb26-107">Remarks</span></span>  
 <span data-ttu-id="2fb26-108">Nelze pokračovat od `ExitProcess` událostí.</span><span class="sxs-lookup"><span data-stu-id="2fb26-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="2fb26-109">Tato událost může aktivovat asynchronně s ostatními událostmi během procesu se zobrazí zastavení.</span><span class="sxs-lookup"><span data-stu-id="2fb26-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="2fb26-110">Tato situace může nastat, pokud se proces ukončí při zastavená, obvykle kvůli některé externí force.</span><span class="sxs-lookup"><span data-stu-id="2fb26-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="2fb26-111">Pokud modul CLR (CLR) je již odeslání spravované zpětné volání, tato událost bude opožděno až po vrátila že zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="2fb26-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="2fb26-112">`ExitProcess` Událostí je pouze ukončení a vyřadit událost, který zaručeně zavolána na vypnutí.</span><span class="sxs-lookup"><span data-stu-id="2fb26-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fb26-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2fb26-113">Requirements</span></span>  
 <span data-ttu-id="2fb26-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fb26-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fb26-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fb26-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fb26-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fb26-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fb26-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fb26-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fb26-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fb26-118">See Also</span></span>  
 [<span data-ttu-id="2fb26-119">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fb26-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
