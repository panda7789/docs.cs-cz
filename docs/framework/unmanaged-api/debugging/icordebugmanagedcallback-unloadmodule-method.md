---
title: ICorDebugManagedCallback::UnloadModule – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: 88ef9fd5a0aac19954a247d0215fe698ebe30d40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788338"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="e5708-102">ICorDebugManagedCallback::UnloadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="e5708-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="e5708-103">Oznamuje ladicímu programu, že byl uvolněn modul common language runtime (DLL).</span><span class="sxs-lookup"><span data-stu-id="e5708-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5708-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5708-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5708-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5708-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e5708-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje aplikační doménu, která obsahuje modul.</span><span class="sxs-lookup"><span data-stu-id="e5708-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="e5708-107">pro Ukazatel na objekt ICorDebugModule, který představuje modul.</span><span class="sxs-lookup"><span data-stu-id="e5708-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5708-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5708-108">Remarks</span></span>  
 <span data-ttu-id="e5708-109">Modul by neměl být použit po tomto volání.</span><span class="sxs-lookup"><span data-stu-id="e5708-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5708-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5708-110">Requirements</span></span>  
 <span data-ttu-id="e5708-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5708-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5708-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5708-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5708-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e5708-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5708-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5708-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5708-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5708-115">See also</span></span>

- [<span data-ttu-id="e5708-116">LoadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="e5708-116">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="e5708-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5708-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
