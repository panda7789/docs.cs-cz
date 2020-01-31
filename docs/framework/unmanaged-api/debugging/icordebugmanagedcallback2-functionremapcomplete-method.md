---
title: ICorDebugManagedCallback2::FunctionRemapComplete – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
ms.openlocfilehash: c6c1fa12248b9ff871e4a62a1a3584f688f2a921
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781492"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="cf443-102">ICorDebugManagedCallback2::FunctionRemapComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="cf443-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="cf443-103">Oznamuje ladicímu programu, že provádění kódu se přepnulo na novou verzi upravované funkce.</span><span class="sxs-lookup"><span data-stu-id="cf443-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf443-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf443-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf443-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf443-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cf443-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující upravenou funkci.</span><span class="sxs-lookup"><span data-stu-id="cf443-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="cf443-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, ve kterém byla zjištěna zarážka přemapování.</span><span class="sxs-lookup"><span data-stu-id="cf443-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="cf443-108">pro Ukazatel na objekt ICorDebugFunction, který představuje verzi funkce aktuálně spuštěné ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="cf443-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf443-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf443-109">Remarks</span></span>  
 <span data-ttu-id="cf443-110">Toto zpětné volání poskytuje ladicímu programu možnost znovu vytvořit všechny prvky krokování, které dříve existovaly.</span><span class="sxs-lookup"><span data-stu-id="cf443-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf443-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf443-111">Requirements</span></span>  
 <span data-ttu-id="cf443-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf443-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf443-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cf443-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf443-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cf443-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf443-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf443-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf443-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf443-116">See also</span></span>

- [<span data-ttu-id="cf443-117">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf443-117">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="cf443-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf443-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
