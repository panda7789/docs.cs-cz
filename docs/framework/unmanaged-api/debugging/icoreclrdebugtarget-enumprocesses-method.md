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
ms.openlocfilehash: 6484832e8e737b9a0d0b3eaf3ede4078729f7a4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178442"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="31b94-102">ICoreClrDebugTarget::EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="31b94-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="31b94-103">Vyjmenovává procesy spuštěné ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="31b94-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31b94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31b94-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31b94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31b94-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="31b94-106">[out] Počet vrácených procesů `ppProcs`v .</span><span class="sxs-lookup"><span data-stu-id="31b94-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="31b94-107">Tato hodnota může být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="31b94-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="31b94-108">[out] Pole [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) struktury, které představují procesy spuštěné ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="31b94-108">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31b94-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="31b94-109">Return Value</span></span>  
 <span data-ttu-id="31b94-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="31b94-110">S_OK</span></span>  
 <span data-ttu-id="31b94-111">Úspěch</span><span class="sxs-lookup"><span data-stu-id="31b94-111">Success.</span></span>  
  
 <span data-ttu-id="31b94-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="31b94-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="31b94-113">Nelze přidělit dostatek `ppProcs`paměti pro .</span><span class="sxs-lookup"><span data-stu-id="31b94-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="31b94-114">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="31b94-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="31b94-115">Další selhání.</span><span class="sxs-lookup"><span data-stu-id="31b94-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31b94-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31b94-116">Remarks</span></span>  
 <span data-ttu-id="31b94-117">Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte metodu [ICoreClrDebugTarget::FreeMemory.](icoreclrdebugtarget-freememory-method.md)</span><span class="sxs-lookup"><span data-stu-id="31b94-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31b94-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31b94-118">Requirements</span></span>  
 <span data-ttu-id="31b94-119">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31b94-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31b94-120">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="31b94-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="31b94-121">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="31b94-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="31b94-122">**Verze rozhraní .NET Framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="31b94-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b94-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="31b94-123">See also</span></span>

- [<span data-ttu-id="31b94-124">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31b94-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
