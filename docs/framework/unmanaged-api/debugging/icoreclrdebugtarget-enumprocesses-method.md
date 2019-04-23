---
title: ICoreClrDebugTarget::EnumProcesses – metoda
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a35f5ff62ca37337b7becb023f2328cbe05aea6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216038"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="61b3c-102">ICoreClrDebugTarget::EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="61b3c-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="61b3c-103">Vytváří výčet procesů, které běží na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="61b3c-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61b3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61b3c-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61b3c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61b3c-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="61b3c-106">[out] Počet procesů, které jsou vráceny v `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="61b3c-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="61b3c-107">Tato hodnota může být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="61b3c-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="61b3c-108">[out] Pole [coreclrdebugprocinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) struktury, které představují procesy spuštěné ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="61b3c-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61b3c-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="61b3c-109">Return Value</span></span>  
 <span data-ttu-id="61b3c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="61b3c-110">S_OK</span></span>  
 <span data-ttu-id="61b3c-111">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="61b3c-111">Success.</span></span>  
  
 <span data-ttu-id="61b3c-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="61b3c-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="61b3c-113">Nepovedlo se přidělit dostatek paměti pro `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="61b3c-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="61b3c-114">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="61b3c-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="61b3c-115">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="61b3c-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61b3c-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61b3c-116">Remarks</span></span>  
 <span data-ttu-id="61b3c-117">Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte [icoreclrdebugtarget::freememory –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="61b3c-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61b3c-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61b3c-118">Requirements</span></span>  
 <span data-ttu-id="61b3c-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61b3c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61b3c-120">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="61b3c-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="61b3c-121">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="61b3c-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="61b3c-122">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="61b3c-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b3c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61b3c-123">See also</span></span>

- [<span data-ttu-id="61b3c-124">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61b3c-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
