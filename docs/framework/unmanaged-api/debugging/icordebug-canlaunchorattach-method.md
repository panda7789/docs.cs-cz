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
ms.openlocfilehash: 354df02b27e87550ba602fe102352455c227441b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859687"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="bc2a0-102">ICorDebug::CanLaunchOrAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="bc2a0-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="bc2a0-103">Vrátí hodnotu HRESULT, která označuje, zda je možné spustit nový proces nebo připojit k zadanému existujícímu procesu v rámci kontextu aktuálního počítače a konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bc2a0-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc2a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc2a0-104">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc2a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc2a0-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="bc2a0-106">pro ID existujícího procesu.</span><span class="sxs-lookup"><span data-stu-id="bc2a0-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="bc2a0-107">pro Předat v `true` případě, že máte v plánu spustit s povoleným laděním Win32 nebo připojit s povoleným laděním Win32; v opačném `false`případě předejte.</span><span class="sxs-lookup"><span data-stu-id="bc2a0-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc2a0-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bc2a0-108">Return Value</span></span>  
 <span data-ttu-id="bc2a0-109">S_OK, pokud služby ladění určí, že spuštění nového procesu nebo připojení k danému procesu je možné, s ohledem na informace o aktuálním počítači a konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bc2a0-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="bc2a0-110">Možné hodnoty HRESULT:</span><span class="sxs-lookup"><span data-stu-id="bc2a0-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="bc2a0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc2a0-111">S_OK</span></span>  
  
- <span data-ttu-id="bc2a0-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="bc2a0-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="bc2a0-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="bc2a0-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="bc2a0-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="bc2a0-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc2a0-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc2a0-115">Remarks</span></span>  
 <span data-ttu-id="bc2a0-116">Tato metoda je čistě informativní.</span><span class="sxs-lookup"><span data-stu-id="bc2a0-116">This method is purely informational.</span></span> <span data-ttu-id="bc2a0-117">Rozhraní vám nezastaví spouštění ani připojování k procesu bez ohledu na hodnotu vrácenou `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="bc2a0-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="bc2a0-118">Pokud máte v úmyslu spustit s povoleným laděním Win32 nebo připojit s povoleným `true` laděním Win32, předejte `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="bc2a0-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="bc2a0-119">Pokud použijete tuto `CanLaunchOrAttach` možnost, může se stát, že se hodnota HRESULT vrátila.</span><span class="sxs-lookup"><span data-stu-id="bc2a0-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc2a0-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc2a0-120">Requirements</span></span>  
 <span data-ttu-id="bc2a0-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc2a0-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc2a0-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc2a0-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc2a0-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bc2a0-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc2a0-124">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc2a0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc2a0-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc2a0-125">See also</span></span>

- [<span data-ttu-id="bc2a0-126">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc2a0-126">ICorDebug Interface</span></span>](icordebug-interface.md)
