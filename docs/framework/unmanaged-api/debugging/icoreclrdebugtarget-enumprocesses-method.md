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
ms.openlocfilehash: 11b1072b3467f7d0a3f223fbc2151ec9ccf461ad
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790807"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="0283e-102">ICoreClrDebugTarget::EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="0283e-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="0283e-103">Vytvoří výčet procesů, které jsou spuštěny na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="0283e-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0283e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0283e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0283e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0283e-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="0283e-106">mimo Počet procesů vrácených v `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="0283e-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="0283e-107">Tato hodnota může být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="0283e-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="0283e-108">mimo Pole struktur [coreclrdebugprocinfo –](coreclrdebugprocinfo-structure.md) , které reprezentují procesy běžící na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="0283e-108">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0283e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0283e-109">Return Value</span></span>  
 <span data-ttu-id="0283e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0283e-110">S_OK</span></span>  
 <span data-ttu-id="0283e-111">Nástup.</span><span class="sxs-lookup"><span data-stu-id="0283e-111">Success.</span></span>  
  
 <span data-ttu-id="0283e-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0283e-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="0283e-113">Nelze přidělit dostatek paměti pro `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="0283e-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="0283e-114">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="0283e-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="0283e-115">Další chyby.</span><span class="sxs-lookup"><span data-stu-id="0283e-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0283e-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0283e-116">Remarks</span></span>  
 <span data-ttu-id="0283e-117">Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte metodu [ICoreClrDebugTarget:: FreeMemory –](icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0283e-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0283e-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0283e-118">Requirements</span></span>  
 <span data-ttu-id="0283e-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0283e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0283e-120">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="0283e-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="0283e-121">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="0283e-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="0283e-122">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="0283e-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0283e-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0283e-123">See also</span></span>

- [<span data-ttu-id="0283e-124">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0283e-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
