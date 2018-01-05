---
title: "ICLRDataTarget::GetThreadContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b03af2f1b1fb851ebc08c23827f59eed9153f19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="62b1f-102">ICLRDataTarget::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="62b1f-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="62b1f-103">Získá aktuální kontext spuštění pro dané vlákno v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="62b1f-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="62b1f-104">Tato metoda je volána běžné data přístupu služby modulu runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="62b1f-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62b1f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62b1f-105">Syntax</span></span>  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62b1f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="62b1f-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="62b1f-107">[v] Identifikátor operačního systému vlákna v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="62b1f-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="62b1f-108">[v] Příznaky, které určují, které části kontext, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="62b1f-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="62b1f-109">Implementace vrátí alespoň tyto části kontextu.</span><span class="sxs-lookup"><span data-stu-id="62b1f-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="62b1f-110">[v] Velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="62b1f-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="62b1f-111">[out] Ukazatel na vyrovnávací paměť, do níž umístíte kontextu.</span><span class="sxs-lookup"><span data-stu-id="62b1f-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="62b1f-112">Data v `context` vyrovnávací paměti musí být ve formátu Win32 `CONTEXT` struktura.</span><span class="sxs-lookup"><span data-stu-id="62b1f-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="62b1f-113">Kontext určuje data registrace specifické pro procesor, takže definice Win32 `CONTEXT` struktura závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="62b1f-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="62b1f-114">Naleznete v souboru WinNT.h hlavičky souboru pro danou definici Win32 `CONTEXT` struktura.</span><span class="sxs-lookup"><span data-stu-id="62b1f-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62b1f-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62b1f-115">Remarks</span></span>  
 <span data-ttu-id="62b1f-116">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="62b1f-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62b1f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62b1f-117">Requirements</span></span>  
 <span data-ttu-id="62b1f-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62b1f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62b1f-119">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="62b1f-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="62b1f-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62b1f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62b1f-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62b1f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62b1f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="62b1f-122">See Also</span></span>  
 [<span data-ttu-id="62b1f-123">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62b1f-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
