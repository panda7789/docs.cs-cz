---
title: "ICorDebug::GetProcess – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3acdcb15f22c130601394ee1bb259207e5e3df23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="9e164-102">ICorDebug::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="9e164-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="9e164-103">Získá ukazatel na instanci "ICorDebugProcess" pro určený proces.</span><span class="sxs-lookup"><span data-stu-id="9e164-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e164-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e164-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e164-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e164-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="9e164-106">[v] ID procesu.</span><span class="sxs-lookup"><span data-stu-id="9e164-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="9e164-107">[out] Ukazatel na adresu `ICorDebugProcess` instancí zadaného procesu.</span><span class="sxs-lookup"><span data-stu-id="9e164-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e164-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e164-108">Requirements</span></span>  
 <span data-ttu-id="9e164-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e164-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e164-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e164-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e164-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e164-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e164-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e164-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e164-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e164-113">See Also</span></span>  
 [<span data-ttu-id="9e164-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e164-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
