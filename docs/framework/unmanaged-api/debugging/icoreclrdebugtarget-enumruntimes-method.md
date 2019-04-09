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
ms.openlocfilehash: afb31646d21ec7e15f79601f5fe83ea6ce44fa90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134672"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="37238-102">ICoreClrDebugTarget::EnumRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="37238-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="37238-103">Vytvoří výčet common language runtime (CLRs) v zadané proces, který běží na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="37238-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37238-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37238-104">Syntax</span></span>  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="37238-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37238-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="37238-106">[in] Interní proces ID procesu, pro kterou chcete vytvořit výčet modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="37238-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="37238-107">Bude jím `m_dwInternalID` od odpovídajících [coreclrdebugprocinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span><span class="sxs-lookup"><span data-stu-id="37238-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="37238-108">[out] Počet modulů runtime, které jsou vráceny v `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="37238-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="37238-109">Tato hodnota může být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="37238-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="37238-110">[out] Pole [coreclrdebugruntimeinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) struktury, které představují modulů runtime načten v vzdálenému cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="37238-110">[out] An array of [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37238-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37238-111">Return Value</span></span>  
 <span data-ttu-id="37238-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="37238-112">S_OK</span></span>  
 <span data-ttu-id="37238-113">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="37238-113">Success.</span></span>  
  
 <span data-ttu-id="37238-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="37238-114">S_FALSE</span></span>  
 `dwInternalProcessID` <span data-ttu-id="37238-115">se neshoduje s jakýkoli proces, který běží na počítači, pravděpodobně protože proces byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="37238-115">does not match any process that is running on the computer, probably because the process was terminated.</span></span> `pcRuntimes` <span data-ttu-id="37238-116">a `ppRuntimes` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="37238-116">and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="37238-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="37238-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="37238-118">Nepovedlo se přidělit dostatek paměti pro `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="37238-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="37238-119">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="37238-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="37238-120">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="37238-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37238-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37238-121">Remarks</span></span>  
 <span data-ttu-id="37238-122">Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte [icoreclrdebugtarget::freememory –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="37238-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37238-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37238-123">Requirements</span></span>  
 <span data-ttu-id="37238-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37238-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37238-125">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="37238-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="37238-126">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="37238-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="37238-127">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="37238-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37238-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37238-128">See also</span></span>

- [<span data-ttu-id="37238-129">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37238-129">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
