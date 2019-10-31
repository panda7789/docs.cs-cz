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
ms.openlocfilehash: 2579bed9ae432a2b9460c421c6ee5bdc40d1e149
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121837"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="a141d-102">ICoreClrDebugTarget::EnumRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="a141d-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="a141d-103">Vytvoří výčet modulu CLR (Common Language Runtime) (CLRs) v zadaném procesu, který je spuštěn ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="a141d-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a141d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a141d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a141d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a141d-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="a141d-106">pro Interní ID procesu, pro který chcete vytvořit výčet modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="a141d-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="a141d-107">Tato akce bude `m_dwInternalID`a z odpovídajících [coreclrdebugprocinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span><span class="sxs-lookup"><span data-stu-id="a141d-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="a141d-108">mimo Počet běhu vrácených v `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="a141d-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="a141d-109">Tato hodnota může být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="a141d-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="a141d-110">mimo Pole struktur [coreclrdebugruntimeinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) , které reprezentují moduly runtime načtené ve vzdáleném cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="a141d-110">[out] An array of [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a141d-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a141d-111">Return Value</span></span>  
 <span data-ttu-id="a141d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a141d-112">S_OK</span></span>  
 <span data-ttu-id="a141d-113">Nástup.</span><span class="sxs-lookup"><span data-stu-id="a141d-113">Success.</span></span>  
  
 <span data-ttu-id="a141d-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a141d-114">S_FALSE</span></span>  
 <span data-ttu-id="a141d-115">`dwInternalProcessID` neodpovídá žádnému procesu, který je spuštěn v počítači, pravděpodobně proto, že proces byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="a141d-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="a141d-116">`pcRuntimes` a `ppRuntimes` budou mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a141d-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="a141d-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a141d-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="a141d-118">Nelze přidělit dostatek paměti pro `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="a141d-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="a141d-119">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="a141d-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a141d-120">Další chyby.</span><span class="sxs-lookup"><span data-stu-id="a141d-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a141d-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a141d-121">Remarks</span></span>  
 <span data-ttu-id="a141d-122">Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte metodu [ICoreClrDebugTarget:: FreeMemory –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a141d-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a141d-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a141d-123">Requirements</span></span>  
 <span data-ttu-id="a141d-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a141d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a141d-125">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="a141d-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a141d-126">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="a141d-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a141d-127">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a141d-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a141d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a141d-128">See also</span></span>

- [<span data-ttu-id="a141d-129">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a141d-129">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
