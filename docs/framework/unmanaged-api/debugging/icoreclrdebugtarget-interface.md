---
title: "ICoreClrDebugTarget – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e13355078727a55c950bed795d3b01b6c7d52564
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="b15bf-102">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b15bf-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="b15bf-103">Poskytuje metody, které řídí počty odkazů, výčet procesy a uvolnit paměť, přidružené ladicí program, který je připojen k vzdálený cíl Macintosh Silverlight.</span><span class="sxs-lookup"><span data-stu-id="b15bf-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b15bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b15bf-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b15bf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b15bf-105">Methods</span></span>  
  
|<span data-ttu-id="b15bf-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b15bf-106">Method</span></span>|<span data-ttu-id="b15bf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b15bf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b15bf-108">Icoreclrdebugtarget::enumprocesses – metoda</span><span class="sxs-lookup"><span data-stu-id="b15bf-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="b15bf-109">Vytvoří výčet procesů, které běží na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="b15bf-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="b15bf-110">Icoreclrdebugtarget::enumruntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="b15bf-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="b15bf-111">Vytvoří výčet běžné moduly runtime jazyka (CLRs) v zadané procesu ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="b15bf-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="b15bf-112">Icoreclrdebugtarget::freememory – metoda</span><span class="sxs-lookup"><span data-stu-id="b15bf-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="b15bf-113">Uvolní paměť, která je přidělena výčtu metody v této třídě.</span><span class="sxs-lookup"><span data-stu-id="b15bf-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b15bf-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b15bf-114">Remarks</span></span>  
 <span data-ttu-id="b15bf-115">Tato funkce je v současné době podporována pouze pro ladění aplikace založená na technologii Silverlight cíl, který běží na vzdáleném počítači Macintosh.</span><span class="sxs-lookup"><span data-stu-id="b15bf-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b15bf-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b15bf-116">Requirements</span></span>  
 <span data-ttu-id="b15bf-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b15bf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b15bf-118">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="b15bf-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="b15bf-119">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="b15bf-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="b15bf-120">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b15bf-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b15bf-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b15bf-121">See Also</span></span>  
 [<span data-ttu-id="b15bf-122">ICorDebugRemoteTarget – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="b15bf-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="b15bf-123">ICorDebug – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="b15bf-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="b15bf-124">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="b15bf-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
