---
title: "ICLRDataTarget::SetThreadContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 02b77bbb721a44ff24734499011402f2b9165ef4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="c311b-102">ICLRDataTarget::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="c311b-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="c311b-103">Nastaví aktuální kontext zadaný vlákno v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="c311b-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="c311b-104">Tato metoda je volána běžné data přístupu služby modulu runtime (CLR) jazyk.</span><span class="sxs-lookup"><span data-stu-id="c311b-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c311b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c311b-105">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c311b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c311b-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c311b-107">[v] Identifikátor operačního systému vlákna v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="c311b-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="c311b-108">[v] Velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="c311b-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="c311b-109">[v] Ukazatel na vyrovnávací paměť obsahující kontext.</span><span class="sxs-lookup"><span data-stu-id="c311b-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="c311b-110">Data v `context` vyrovnávací paměti bude ve formátu Win32 `CONTEXT` struktura.</span><span class="sxs-lookup"><span data-stu-id="c311b-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="c311b-111">Kontext určuje data registrace specifické pro procesor, takže definice Win32 `CONTEXT` struktura závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="c311b-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="c311b-112">Naleznete v souboru WinNT.h hlavičky souboru pro danou definici Win32 `CONTEXT` struktura.</span><span class="sxs-lookup"><span data-stu-id="c311b-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c311b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c311b-113">Remarks</span></span>  
 <span data-ttu-id="c311b-114">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c311b-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c311b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c311b-115">Requirements</span></span>  
 <span data-ttu-id="c311b-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c311b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c311b-117">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c311b-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c311b-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c311b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c311b-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c311b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c311b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c311b-120">See Also</span></span>  
 [<span data-ttu-id="c311b-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c311b-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
