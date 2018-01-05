---
title: "ICoreClrDebugTarget::EnumProcesses – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget.EnumProcesses
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8296b4b137032400ee172b6d3670bc1a53dbe60d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="fb58f-102">ICoreClrDebugTarget::EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="fb58f-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="fb58f-103">Vytvoří výčet procesů, které běží na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="fb58f-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb58f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb58f-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb58f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb58f-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="fb58f-106">[out] Počet procesů, vrátí se v `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="fb58f-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="fb58f-107">Tato hodnota může být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="fb58f-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="fb58f-108">[out] Pole [coreclrdebugprocinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) struktury, které představují procesů spuštěných na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="fb58f-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb58f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fb58f-109">Return Value</span></span>  
 <span data-ttu-id="fb58f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb58f-110">S_OK</span></span>  
 <span data-ttu-id="fb58f-111">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="fb58f-111">Success.</span></span>  
  
 <span data-ttu-id="fb58f-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fb58f-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="fb58f-113">Nelze přidělit dostatek paměti pro `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="fb58f-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="fb58f-114">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="fb58f-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="fb58f-115">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="fb58f-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb58f-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb58f-116">Remarks</span></span>  
 <span data-ttu-id="fb58f-117">Chcete-li volné paměti, která byla přidělena touto metodou, volejte [icoreclrdebugtarget::freememory –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="fb58f-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb58f-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb58f-118">Requirements</span></span>  
 <span data-ttu-id="fb58f-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb58f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb58f-120">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="fb58f-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="fb58f-121">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="fb58f-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="fb58f-122">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="fb58f-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb58f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb58f-123">See Also</span></span>  
 [<span data-ttu-id="fb58f-124">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb58f-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
