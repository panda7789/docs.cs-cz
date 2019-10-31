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
ms.openlocfilehash: 805f9a5d1f2590a06bfa929c152bdfd13900531a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134285"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="abf38-102">ICorDebug::CanLaunchOrAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="abf38-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="abf38-103">Vrátí hodnotu HRESULT, která označuje, zda je možné spustit nový proces nebo připojit k zadanému existujícímu procesu v rámci kontextu aktuálního počítače a konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="abf38-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf38-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abf38-104">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abf38-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abf38-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="abf38-106">pro ID existujícího procesu.</span><span class="sxs-lookup"><span data-stu-id="abf38-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="abf38-107">pro Předejte `true`, pokud máte v plánu spustit s povoleným laděním Win32 nebo připojit s povoleným laděním Win32. v opačném případě předejte `false`.</span><span class="sxs-lookup"><span data-stu-id="abf38-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abf38-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="abf38-108">Return Value</span></span>  
 <span data-ttu-id="abf38-109">S_OK, pokud služba ladění určí, že spuštění nového procesu nebo připojení k danému procesu je možné, s ohledem na informace o aktuálním počítači a konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="abf38-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="abf38-110">Možné hodnoty HRESULT:</span><span class="sxs-lookup"><span data-stu-id="abf38-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="abf38-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="abf38-111">S_OK</span></span>  
  
- <span data-ttu-id="abf38-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="abf38-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="abf38-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="abf38-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="abf38-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="abf38-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abf38-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="abf38-115">Remarks</span></span>  
 <span data-ttu-id="abf38-116">Tato metoda je čistě informativní.</span><span class="sxs-lookup"><span data-stu-id="abf38-116">This method is purely informational.</span></span> <span data-ttu-id="abf38-117">Rozhraní vám nezastaví spouštění ani připojování k procesu bez ohledu na hodnotu vrácenou `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="abf38-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="abf38-118">Pokud máte v úmyslu spustit s povoleným laděním Win32 nebo připojit s povoleným laděním Win32, předejte `true` `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="abf38-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="abf38-119">Hodnota HRESULT vrácená funkcí `CanLaunchOrAttach` se může lišit, pokud použijete tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="abf38-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abf38-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abf38-120">Requirements</span></span>  
 <span data-ttu-id="abf38-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abf38-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abf38-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="abf38-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abf38-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="abf38-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abf38-124">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abf38-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf38-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abf38-125">See also</span></span>

- [<span data-ttu-id="abf38-126">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abf38-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
