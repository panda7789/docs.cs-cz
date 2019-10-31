---
title: ICoreClrDebugTarget – rozhraní
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: 83afe121b6bf0de3c5542695e38b6605db7a8b6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121820"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="9357a-102">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9357a-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="9357a-103">Poskytuje metody, které řídí počty odkazů, vytváří výčet procesů a uvolňuje paměť přidruženou k ladicímu programu, který je připojen ke vzdálenému počítači se službou Silverlight.</span><span class="sxs-lookup"><span data-stu-id="9357a-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9357a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9357a-104">Syntax</span></span>  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9357a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9357a-105">Methods</span></span>  
  
|<span data-ttu-id="9357a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9357a-106">Method</span></span>|<span data-ttu-id="9357a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9357a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9357a-108">ICoreClrDebugTarget::EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="9357a-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="9357a-109">Vytvoří výčet procesů, které jsou spuštěny na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="9357a-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="9357a-110">ICoreClrDebugTarget::EnumRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="9357a-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="9357a-111">Vytvoří výčet modulu CLR (Common Language Runtime) (CLRs) v zadaném procesu na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="9357a-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="9357a-112">ICoreClrDebugTarget::FreeMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="9357a-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="9357a-113">Uvolní paměť, která je přidělena metodami výčtu v této třídě.</span><span class="sxs-lookup"><span data-stu-id="9357a-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9357a-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9357a-114">Remarks</span></span>  
 <span data-ttu-id="9357a-115">V současné době je tato funkce podporována pouze pro ladění cíle aplikace založeného na programu Silverlight, který je spuštěn ve vzdáleném počítači se systémem Macintosh.</span><span class="sxs-lookup"><span data-stu-id="9357a-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9357a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9357a-116">Requirements</span></span>  
 <span data-ttu-id="9357a-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9357a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9357a-118">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="9357a-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="9357a-119">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="9357a-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="9357a-120">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="9357a-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9357a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9357a-121">See also</span></span>

- [<span data-ttu-id="9357a-122">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9357a-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="9357a-123">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9357a-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="9357a-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9357a-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
