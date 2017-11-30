---
title: "ICorDebugManagedCallback::UnloadAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.UnloadAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29400e5bda2a17c731cb33e67c0123cffc89c48b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="ef444-102">ICorDebugManagedCallback::UnloadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="ef444-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="ef444-103">Upozorní ladicího programu běžné sestavení modulu runtime jazyka byl odpojen.</span><span class="sxs-lookup"><span data-stu-id="ef444-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef444-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef444-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef444-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef444-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ef444-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, která obsahovala sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef444-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="ef444-107">[v] Ukazatel na ICorDebugAssembly objekt, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef444-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef444-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef444-108">Remarks</span></span>  
 <span data-ttu-id="ef444-109">Sestavení není vhodné používat po této zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ef444-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef444-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef444-110">Requirements</span></span>  
 <span data-ttu-id="ef444-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef444-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef444-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef444-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef444-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef444-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef444-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef444-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef444-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef444-115">See Also</span></span>  
 [<span data-ttu-id="ef444-116">Loadassembly – metoda</span><span class="sxs-lookup"><span data-stu-id="ef444-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="ef444-117">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef444-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
