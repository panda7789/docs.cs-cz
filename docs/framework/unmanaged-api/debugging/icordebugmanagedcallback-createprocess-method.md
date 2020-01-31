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
ms.openlocfilehash: 0c3059697014cea33081f6cb81b9d93c7d028c2e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777472"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="3d884-102">ICorDebugManagedCallback::CreateProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="3d884-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="3d884-103">Upozorní ladicí program, když byl proces poprvé připojen nebo spuštěn.</span><span class="sxs-lookup"><span data-stu-id="3d884-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d884-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d884-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d884-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d884-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="3d884-106">pro Ukazatel na objekt ICorDebugProcess, který představuje proces, který byl připojen nebo zahájen.</span><span class="sxs-lookup"><span data-stu-id="3d884-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d884-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d884-107">Remarks</span></span>  
 <span data-ttu-id="3d884-108">Tato metoda není volána, dokud není inicializován modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="3d884-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="3d884-109">Většina metod [ICorDebug](icordebug-interface.md) vrátí CORDBG_E_NOTREADY před zpětným voláním `CreateProcess`.</span><span class="sxs-lookup"><span data-stu-id="3d884-109">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d884-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d884-110">Requirements</span></span>  
 <span data-ttu-id="3d884-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d884-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d884-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3d884-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d884-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3d884-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d884-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d884-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d884-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d884-115">See also</span></span>

- [<span data-ttu-id="3d884-116">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3d884-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
