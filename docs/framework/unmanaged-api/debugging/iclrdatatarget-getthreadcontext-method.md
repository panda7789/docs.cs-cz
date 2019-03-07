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
ms.openlocfilehash: 7c2e1dc374a5205c774e4470363b38c604fa0862
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500496"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="be438-102">ICLRDataTarget::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="be438-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="be438-103">Získá aktuální kontext spuštění pro dané vlákno v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="be438-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="be438-104">Tato metoda je volána službami common language runtime přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="be438-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be438-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be438-105">Syntax</span></span>  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be438-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="be438-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="be438-107">[in] Operační systém identifikátor vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="be438-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="be438-108">[in] Příznaky, které určují, které části kontext, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="be438-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="be438-109">Implementace vrátí aspoň tyto části kontextu.</span><span class="sxs-lookup"><span data-stu-id="be438-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="be438-110">[in] Velikost kontext.</span><span class="sxs-lookup"><span data-stu-id="be438-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="be438-111">[out] Ukazatel do vyrovnávací paměti, do které se má umístit kontextu.</span><span class="sxs-lookup"><span data-stu-id="be438-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="be438-112">Data v `context` vyrovnávací paměti musí být ve formátu Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="be438-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="be438-113">Kontext určuje data registru specifické pro procesor, takže definice Win32 `CONTEXT` struktura závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="be438-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="be438-114">Najdete v souboru WinNT.h hlavičkový soubor pro definici Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="be438-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be438-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be438-115">Remarks</span></span>  
 <span data-ttu-id="be438-116">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="be438-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be438-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be438-117">Requirements</span></span>  
 <span data-ttu-id="be438-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be438-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be438-119">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="be438-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="be438-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be438-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be438-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be438-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be438-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be438-122">See also</span></span>
- [<span data-ttu-id="be438-123">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be438-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
