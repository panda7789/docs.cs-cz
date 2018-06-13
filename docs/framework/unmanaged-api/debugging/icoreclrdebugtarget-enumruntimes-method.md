---
title: ICoreClrDebugTarget::EnumRuntimes – metoda
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14b5f2227991e38ba66889d7e966ab24e714294c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422579"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="c6568-102">ICoreClrDebugTarget::EnumRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="c6568-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="c6568-103">Vytvoří výčet běžné moduly runtime jazyka (CLRs) v zadané procesu, který je spuštěn ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="c6568-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6568-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6568-104">Syntax</span></span>  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6568-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6568-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="c6568-106">[v] Interní proces ID procesu, pro který chcete vytvořit výčet moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="c6568-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="c6568-107">Bude jím `m_dwInternalID` z odpovídající [coreclrdebugprocinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span><span class="sxs-lookup"><span data-stu-id="c6568-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="c6568-108">[out] Číslo, vrátí se v modulech runtime `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="c6568-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="c6568-109">Tato hodnota může být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="c6568-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="c6568-110">[out] Pole [coreclrdebugruntimeinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) struktury, které představují modulech runtime načten do vzdáleného Cílový proces.</span><span class="sxs-lookup"><span data-stu-id="c6568-110">[out] An array of [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6568-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c6568-111">Return Value</span></span>  
 <span data-ttu-id="c6568-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6568-112">S_OK</span></span>  
 <span data-ttu-id="c6568-113">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="c6568-113">Success.</span></span>  
  
 <span data-ttu-id="c6568-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c6568-114">S_FALSE</span></span>  
 <span data-ttu-id="c6568-115">`dwInternalProcessID` neodpovídá jakýkoli proces, který běží na počítači, pravděpodobně, protože proces byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="c6568-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="c6568-116">`pcRuntimes` a `ppRuntimes` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c6568-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="c6568-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c6568-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="c6568-118">Nelze přidělit dostatek paměti pro `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="c6568-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="c6568-119">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="c6568-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c6568-120">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="c6568-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6568-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6568-121">Remarks</span></span>  
 <span data-ttu-id="c6568-122">Chcete-li volné paměti, která byla přidělena touto metodou, volejte [icoreclrdebugtarget::freememory –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="c6568-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6568-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6568-123">Requirements</span></span>  
 <span data-ttu-id="c6568-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6568-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6568-125">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="c6568-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="c6568-126">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="c6568-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="c6568-127">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="c6568-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6568-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6568-128">See Also</span></span>  
 [<span data-ttu-id="c6568-129">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6568-129">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
