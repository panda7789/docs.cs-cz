---
title: ICorDebugManagedCallback::CreateProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eda214200ca4c3837ad89ed14887ef6b09af7d30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160365"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="a41a5-102">ICorDebugManagedCallback::CreateProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="a41a5-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="a41a5-103">Ladicí program upozorní, když proces byl připojen nebo první spuštění.</span><span class="sxs-lookup"><span data-stu-id="a41a5-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a41a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a41a5-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a41a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a41a5-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="a41a5-106">[in] Ukazatel na objekt ICorDebugProcess, který představuje proces, který se má připojit nebo spustit.</span><span class="sxs-lookup"><span data-stu-id="a41a5-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a41a5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a41a5-107">Remarks</span></span>  
 <span data-ttu-id="a41a5-108">Tato metoda není volána, dokud se inicializovat modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="a41a5-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="a41a5-109">Většina [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody vrátí CORDBG_E_NOTREADY před `CreateProcess` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="a41a5-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a41a5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a41a5-110">Requirements</span></span>  
 <span data-ttu-id="a41a5-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a41a5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a41a5-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a41a5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a41a5-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a41a5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a41a5-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a41a5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a41a5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a41a5-115">See also</span></span>

- [<span data-ttu-id="a41a5-116">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a41a5-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
