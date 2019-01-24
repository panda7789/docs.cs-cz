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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4576d8ea7d601e1b37d0cb6f54802f93bc128622
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593781"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="d47e1-102">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d47e1-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="d47e1-103">Poskytuje metody, které řídí počty odkazů, výčet procesů a uvolňují paměť spojené s ladicím programem, který je připojen na vzdálené cílové Macintosh Silverlight.</span><span class="sxs-lookup"><span data-stu-id="d47e1-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d47e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d47e1-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="d47e1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d47e1-105">Methods</span></span>  
  
|<span data-ttu-id="d47e1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d47e1-106">Method</span></span>|<span data-ttu-id="d47e1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d47e1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d47e1-108">ICoreClrDebugTarget::EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="d47e1-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="d47e1-109">Vytváří výčet procesů, které běží na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="d47e1-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="d47e1-110">ICoreClrDebugTarget::EnumRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="d47e1-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="d47e1-111">Vytvoří výčet common language runtime (CLRs) v zadané procesu ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="d47e1-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="d47e1-112">ICoreClrDebugTarget::FreeMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="d47e1-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="d47e1-113">Uvolnění paměti, která je přidělena výčet metod této třídy.</span><span class="sxs-lookup"><span data-stu-id="d47e1-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d47e1-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d47e1-114">Remarks</span></span>  
 <span data-ttu-id="d47e1-115">Tato funkce v současné době je podporována pouze pro ladění cíl aplikace založené na technologii Silverlight, která běží na vzdáleném počítači Macintosh.</span><span class="sxs-lookup"><span data-stu-id="d47e1-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d47e1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d47e1-116">Requirements</span></span>  
 <span data-ttu-id="d47e1-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d47e1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d47e1-118">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="d47e1-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="d47e1-119">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="d47e1-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="d47e1-120">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="d47e1-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d47e1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d47e1-121">See also</span></span>
- [<span data-ttu-id="d47e1-122">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d47e1-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="d47e1-123">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d47e1-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="d47e1-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d47e1-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
