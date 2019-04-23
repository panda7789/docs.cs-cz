---
title: ICorDebugManagedCallback::ExitProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51162bfb6f9763d2ab4ac1f86e0ccdc15b601271
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159871"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="dadad-102">ICorDebugManagedCallback::ExitProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="dadad-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="dadad-103">Upozorní ladicího programu, že proces byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="dadad-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dadad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dadad-104">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dadad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dadad-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="dadad-106">[in] Ukazatel na objekt ICorDebugProcess, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="dadad-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dadad-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dadad-107">Remarks</span></span>  
 <span data-ttu-id="dadad-108">Nejde pokračovat od `ExitProcess` událostí.</span><span class="sxs-lookup"><span data-stu-id="dadad-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="dadad-109">Tato událost může aktivovat asynchronně s ostatními událostmi během procesu se zdá být zastaven.</span><span class="sxs-lookup"><span data-stu-id="dadad-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="dadad-110">Tato situace může nastat, pokud se proces ukončí při zastavení, obvykle kvůli některé externí platnost.</span><span class="sxs-lookup"><span data-stu-id="dadad-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="dadad-111">Pokud common language runtime (CLR) je již odesílání spravované zpětné volání, tato událost bude odložena až do po vrátila tohoto zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="dadad-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="dadad-112">`ExitProcess` Událostí je jediná událost výstupu/uvolnění, která je zaručeně získat volat pro vypnutí.</span><span class="sxs-lookup"><span data-stu-id="dadad-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dadad-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dadad-113">Requirements</span></span>  
 <span data-ttu-id="dadad-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dadad-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dadad-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dadad-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dadad-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dadad-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dadad-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dadad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dadad-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dadad-118">See also</span></span>

- [<span data-ttu-id="dadad-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dadad-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
