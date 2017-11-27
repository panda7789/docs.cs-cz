---
title: "ICorDebugManagedCallback::CreateProcess – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.CreateProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bef3140717ff977fbfae813d0de89011b89ed062
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="9bbd4-102">ICorDebugManagedCallback::CreateProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="9bbd4-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="9bbd4-103">Ladicí program upozorní, když proces byl připojen nebo při prvním spuštění.</span><span class="sxs-lookup"><span data-stu-id="9bbd4-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bbd4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bbd4-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bbd4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bbd4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="9bbd4-106">[v] Ukazatel na ICorDebugProcess objekt, který představuje proces, který se má připojit nebo spustit.</span><span class="sxs-lookup"><span data-stu-id="9bbd4-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bbd4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9bbd4-107">Remarks</span></span>  
 <span data-ttu-id="9bbd4-108">Tato metoda není volána, dokud se neinicializuje modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="9bbd4-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="9bbd4-109">Většina [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody vrátí CORDBG_E_NOTREADY před `CreateProcess` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9bbd4-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bbd4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9bbd4-110">Requirements</span></span>  
 <span data-ttu-id="9bbd4-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bbd4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bbd4-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bbd4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bbd4-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bbd4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bbd4-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bbd4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bbd4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bbd4-115">See Also</span></span>  
 [<span data-ttu-id="9bbd4-116">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="9bbd4-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
