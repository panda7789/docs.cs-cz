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
ms.openlocfilehash: 0cc79c0a93fa4f05b8c793a8b7fb0b9b3f031b1a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791955"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="9ca5f-102">ICorDebugRemote – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ca5f-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="9ca5f-103">Umožňuje spustit nebo připojit spravovaný ladicí program ke vzdálenému cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="9ca5f-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ca5f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="9ca5f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9ca5f-105">Methods</span></span>  
  
|<span data-ttu-id="9ca5f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9ca5f-106">Method</span></span>|<span data-ttu-id="9ca5f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9ca5f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ca5f-108">ICorDebugRemote::CreateProcessEx – metoda</span><span class="sxs-lookup"><span data-stu-id="9ca5f-108">ICorDebugRemote::CreateProcessEx Method</span></span>](icordebugremote-createprocessex-method.md)|<span data-ttu-id="9ca5f-109">Vytvoří proces na vzdáleném počítači pro spravované ladění.</span><span class="sxs-lookup"><span data-stu-id="9ca5f-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="9ca5f-110">ICorDebugRemote::DebugActiveProcessEx – metoda</span><span class="sxs-lookup"><span data-stu-id="9ca5f-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="9ca5f-111">Spustí proces na vzdáleném počítači v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="9ca5f-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ca5f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ca5f-112">Remarks</span></span>  
 <span data-ttu-id="9ca5f-113">V současné době je tato funkce podporována pouze pro ladění cíle aplikace založeného na programu Silverlight, který je spuštěn na vzdáleném počítači se systémem Macintosh.</span><span class="sxs-lookup"><span data-stu-id="9ca5f-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ca5f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ca5f-114">Requirements</span></span>  
 <span data-ttu-id="9ca5f-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ca5f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca5f-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9ca5f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ca5f-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9ca5f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ca5f-118">**Verze .NET Framework:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="9ca5f-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca5f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ca5f-119">See also</span></span>

- [<span data-ttu-id="9ca5f-120">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ca5f-120">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="9ca5f-121">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ca5f-121">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="9ca5f-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9ca5f-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
