---
title: ICLRDataTarget::SetThreadContext – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: cceafc8358ce2b0eafa62a3855c4eb1e96adae11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113318"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="110a2-102">ICLRDataTarget::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="110a2-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="110a2-103">Nastaví aktuální kontext zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="110a2-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="110a2-104">Tato metoda je volána službou Common Language Runtime (CLR) pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="110a2-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="110a2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="110a2-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="110a2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="110a2-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="110a2-107">pro Identifikátor operačního systému vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="110a2-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="110a2-108">pro Velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="110a2-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="110a2-109">pro Ukazatel na vyrovnávací paměť obsahující kontext.</span><span class="sxs-lookup"><span data-stu-id="110a2-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="110a2-110">Data ve vyrovnávací paměti `context` budou ve formátu `CONTEXT` struktury Win32.</span><span class="sxs-lookup"><span data-stu-id="110a2-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="110a2-111">Kontext určuje data registru pro konkrétní procesor, takže definice struktury `CONTEXT` Win32 závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="110a2-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="110a2-112">Definici struktury `CONTEXT` Win32 najdete v souboru hlaviček WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="110a2-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="110a2-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="110a2-113">Remarks</span></span>  
 <span data-ttu-id="110a2-114">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="110a2-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="110a2-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="110a2-115">Requirements</span></span>  
 <span data-ttu-id="110a2-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="110a2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="110a2-117">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="110a2-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="110a2-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="110a2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="110a2-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="110a2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110a2-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="110a2-120">See also</span></span>

- [<span data-ttu-id="110a2-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="110a2-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
