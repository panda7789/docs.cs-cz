---
title: ICLRDataTarget::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1492c6d72d68a95a79925d7789a710b5b5ed14b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738702"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="84b19-102">ICLRDataTarget::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="84b19-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="84b19-103">Získá aktuální kontext spuštění pro dané vlákno v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="84b19-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="84b19-104">Tato metoda je volána službami common language runtime přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="84b19-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84b19-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84b19-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84b19-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="84b19-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="84b19-107">[in] Operační systém identifikátor vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="84b19-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="84b19-108">[in] Příznaky, které určují, které části kontext, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="84b19-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="84b19-109">Implementace vrátí aspoň tyto části kontextu.</span><span class="sxs-lookup"><span data-stu-id="84b19-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="84b19-110">[in] Velikost kontext.</span><span class="sxs-lookup"><span data-stu-id="84b19-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="84b19-111">[out] Ukazatel do vyrovnávací paměti, do které se má umístit kontextu.</span><span class="sxs-lookup"><span data-stu-id="84b19-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="84b19-112">Data v `context` vyrovnávací paměti musí být ve formátu Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="84b19-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="84b19-113">Kontext určuje data registru specifické pro procesor, takže definice Win32 `CONTEXT` struktura závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="84b19-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="84b19-114">Najdete v souboru WinNT.h hlavičkový soubor pro definici Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="84b19-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84b19-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84b19-115">Remarks</span></span>  
 <span data-ttu-id="84b19-116">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="84b19-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84b19-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84b19-117">Requirements</span></span>  
 <span data-ttu-id="84b19-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84b19-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84b19-119">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="84b19-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="84b19-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84b19-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84b19-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84b19-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b19-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84b19-122">See also</span></span>

- [<span data-ttu-id="84b19-123">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84b19-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
