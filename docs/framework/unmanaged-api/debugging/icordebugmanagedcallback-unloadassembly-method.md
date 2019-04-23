---
title: ICorDebugManagedCallback::UnloadAssembly – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e770602858761dbcf15c233dceebfd35be106aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214128"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="05970-102">ICorDebugManagedCallback::UnloadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="05970-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="05970-103">Upozorní ladicího programu, že sestavení common language runtime byl uvolněn.</span><span class="sxs-lookup"><span data-stu-id="05970-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05970-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05970-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05970-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05970-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="05970-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, který obsahoval sestavení.</span><span class="sxs-lookup"><span data-stu-id="05970-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="05970-107">[in] Ukazatel na objekt icordebugassembly –, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="05970-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05970-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05970-108">Remarks</span></span>  
 <span data-ttu-id="05970-109">Sestavení se nesmí používat po tomto zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="05970-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05970-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05970-110">Requirements</span></span>  
 <span data-ttu-id="05970-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05970-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05970-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05970-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05970-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05970-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05970-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05970-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05970-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05970-115">See also</span></span>

- [<span data-ttu-id="05970-116">LoadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="05970-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="05970-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05970-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
