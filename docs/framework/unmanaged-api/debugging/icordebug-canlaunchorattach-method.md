---
title: ICorDebug::CanLaunchOrAttach – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cf0065f1ed12ad3a37819b0a15d734a2b51ff5b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125603"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="6a9d2-102">ICorDebug::CanLaunchOrAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="6a9d2-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="6a9d2-103">Vrátí hodnotu HRESULT, která určuje, zda je možné v rámci kontextu aktuální konfiguraci počítače a modul runtime spustí nový proces nebo připojení k zadané existující procesu.</span><span class="sxs-lookup"><span data-stu-id="6a9d2-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a9d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a9d2-104">Syntax</span></span>  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a9d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a9d2-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="6a9d2-106">[in] ID existující proces.</span><span class="sxs-lookup"><span data-stu-id="6a9d2-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="6a9d2-107">[in] Předejte `true` Pokud plánujete spustit s povoleným laděním Win32, nebo se připojit s Win32 ladění povoleno; jinak předejte `false`.</span><span class="sxs-lookup"><span data-stu-id="6a9d2-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a9d2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a9d2-108">Return Value</span></span>  
 <span data-ttu-id="6a9d2-109">S_OK Pokud ladění služby určit, který spouští se nový proces nebo připojení k dané procesu je možné, uvedené informace o aktuální konfiguraci počítače a modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6a9d2-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="6a9d2-110">Jsou možné hodnoty HRESULT:</span><span class="sxs-lookup"><span data-stu-id="6a9d2-110">Possible HRESULT values are:</span></span>  
  
-   <span data-ttu-id="6a9d2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a9d2-111">S_OK</span></span>  
  
-   <span data-ttu-id="6a9d2-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="6a9d2-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
-   <span data-ttu-id="6a9d2-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="6a9d2-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
-   <span data-ttu-id="6a9d2-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="6a9d2-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a9d2-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a9d2-115">Remarks</span></span>  
 <span data-ttu-id="6a9d2-116">Tato metoda je pouze informační.</span><span class="sxs-lookup"><span data-stu-id="6a9d2-116">This method is purely informational.</span></span> <span data-ttu-id="6a9d2-117">Rozhraní nezastaví spouštění nebo připojení k procesu, bez ohledu na hodnotu vrácenou `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="6a9d2-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="6a9d2-118">Pokud budete chtít spustit s povoleným laděním Win32 nebo připojení s povoleným laděním Win32, předejte `true` pro `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="6a9d2-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="6a9d2-119">Vrácená hodnota HRESULT `CanLaunchOrAttach` mohou lišit, pokud použijete tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="6a9d2-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a9d2-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a9d2-120">Requirements</span></span>  
 <span data-ttu-id="6a9d2-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a9d2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a9d2-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a9d2-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a9d2-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a9d2-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6a9d2-124">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6a9d2-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6a9d2-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a9d2-125">See also</span></span>

- [<span data-ttu-id="6a9d2-126">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a9d2-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
