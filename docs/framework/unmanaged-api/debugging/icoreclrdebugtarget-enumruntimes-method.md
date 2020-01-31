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
ms.openlocfilehash: 4b55ac1d895bfecbe74be447bd06f4aa22b9d04f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790784"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="ad4d4-102">ICoreClrDebugTarget::EnumRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="ad4d4-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="ad4d4-103">Vytvoří výčet modulu CLR (Common Language Runtime) (CLRs) v zadaném procesu, který je spuštěn ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad4d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad4d4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad4d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad4d4-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="ad4d4-106">pro Interní ID procesu, pro který chcete vytvořit výčet modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="ad4d4-107">Tato akce bude `m_dwInternalID`a z odpovídajících [coreclrdebugprocinfo –](coreclrdebugprocinfo-structure.md).</span><span class="sxs-lookup"><span data-stu-id="ad4d4-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="ad4d4-108">mimo Počet běhu vrácených v `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="ad4d4-109">Tato hodnota může být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="ad4d4-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="ad4d4-110">mimo Pole struktur [coreclrdebugruntimeinfo –](coreclrdebugruntimeinfo-structure.md) , které reprezentují moduly runtime načtené ve vzdáleném cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-110">[out] An array of [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad4d4-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ad4d4-111">Return Value</span></span>  
 <span data-ttu-id="ad4d4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad4d4-112">S_OK</span></span>  
 <span data-ttu-id="ad4d4-113">Nástup.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-113">Success.</span></span>  
  
 <span data-ttu-id="ad4d4-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ad4d4-114">S_FALSE</span></span>  
 <span data-ttu-id="ad4d4-115">`dwInternalProcessID` neodpovídá žádnému procesu, který je spuštěn v počítači, pravděpodobně proto, že proces byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="ad4d4-116">`pcRuntimes` a `ppRuntimes` budou mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="ad4d4-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ad4d4-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="ad4d4-118">Nelze přidělit dostatek paměti pro `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="ad4d4-119">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="ad4d4-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ad4d4-120">Další chyby.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad4d4-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad4d4-121">Remarks</span></span>  
 <span data-ttu-id="ad4d4-122">Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte metodu [ICoreClrDebugTarget:: FreeMemory –](icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ad4d4-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad4d4-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad4d4-123">Requirements</span></span>  
 <span data-ttu-id="ad4d4-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad4d4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad4d4-125">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="ad4d4-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="ad4d4-126">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="ad4d4-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="ad4d4-127">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="ad4d4-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad4d4-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad4d4-128">See also</span></span>

- [<span data-ttu-id="ad4d4-129">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad4d4-129">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
