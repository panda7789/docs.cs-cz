---
title: ICorDebugRemote – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
ms.openlocfilehash: a7eb2796de060b3a5dc8e8c08d07e6aeeb3daecb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131269"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="69dcd-102">ICorDebugRemote – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69dcd-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="69dcd-103">Umožňuje spustit nebo připojit spravovaný ladicí program ke vzdálenému cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="69dcd-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69dcd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69dcd-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="69dcd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="69dcd-105">Methods</span></span>  
  
|<span data-ttu-id="69dcd-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="69dcd-106">Method</span></span>|<span data-ttu-id="69dcd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="69dcd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69dcd-108">ICorDebugRemote::CreateProcessEx – metoda</span><span class="sxs-lookup"><span data-stu-id="69dcd-108">ICorDebugRemote::CreateProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|<span data-ttu-id="69dcd-109">Vytvoří proces na vzdáleném počítači pro spravované ladění.</span><span class="sxs-lookup"><span data-stu-id="69dcd-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="69dcd-110">ICorDebugRemote::DebugActiveProcessEx – metoda</span><span class="sxs-lookup"><span data-stu-id="69dcd-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="69dcd-111">Spustí proces na vzdáleném počítači v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="69dcd-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69dcd-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69dcd-112">Remarks</span></span>  
 <span data-ttu-id="69dcd-113">V současné době je tato funkce podporována pouze pro ladění cíle aplikace založeného na programu Silverlight, který je spuštěn na vzdáleném počítači se systémem Macintosh.</span><span class="sxs-lookup"><span data-stu-id="69dcd-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69dcd-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69dcd-114">Requirements</span></span>  
 <span data-ttu-id="69dcd-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69dcd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69dcd-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="69dcd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69dcd-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="69dcd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69dcd-118">**Verze .NET Framework:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="69dcd-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69dcd-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69dcd-119">See also</span></span>

- [<span data-ttu-id="69dcd-120">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69dcd-120">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="69dcd-121">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69dcd-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="69dcd-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="69dcd-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
