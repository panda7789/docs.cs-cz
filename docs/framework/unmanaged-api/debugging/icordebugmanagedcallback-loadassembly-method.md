---
title: ICorDebugManagedCallback::LoadAssembly – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8fde6772a43cc763df82ec109c11f8548ba240e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476175"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="420b4-102">ICorDebugManagedCallback::LoadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="420b4-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="420b4-103">Upozorní ladicího programu, že sestavení common language runtime (CLR) byl úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="420b4-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="420b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="420b4-104">Syntax</span></span>  
  
```  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="420b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="420b4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="420b4-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do které sestavení bylo načteno.</span><span class="sxs-lookup"><span data-stu-id="420b4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="420b4-107">[in] Ukazatel na objekt icordebugassembly –, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="420b4-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="420b4-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="420b4-108">Requirements</span></span>  
 <span data-ttu-id="420b4-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="420b4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="420b4-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="420b4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="420b4-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="420b4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="420b4-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="420b4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="420b4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="420b4-113">See also</span></span>
- [<span data-ttu-id="420b4-114">UnloadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="420b4-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="420b4-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="420b4-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
