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
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179182"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="89e8c-102">ICLRDataTarget::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="89e8c-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="89e8c-103">Získá aktuální kontext spuštění pro dané vlákno v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="89e8c-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="89e8c-104">Tato metoda je volána služby přístupu k datům za běhu běžného jazyka.</span><span class="sxs-lookup"><span data-stu-id="89e8c-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e8c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89e8c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89e8c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="89e8c-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="89e8c-107">[v] Identifikátor operačního systému podprocesu v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="89e8c-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="89e8c-108">[v] Příznaky, které určují, které části kontextu vrátit.</span><span class="sxs-lookup"><span data-stu-id="89e8c-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="89e8c-109">Implementace vrátí alespoň tyto části kontextu.</span><span class="sxs-lookup"><span data-stu-id="89e8c-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="89e8c-110">[v] Velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="89e8c-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="89e8c-111">[out] Ukazatel na vyrovnávací paměť, do které chcete umístit kontext.</span><span class="sxs-lookup"><span data-stu-id="89e8c-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="89e8c-112">Data ve `context` vyrovnávací paměti musí být ve formátu `CONTEXT` Win32 struktury.</span><span class="sxs-lookup"><span data-stu-id="89e8c-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="89e8c-113">Kontext určuje data registru specifické pro procesor, takže definice `CONTEXT` win32 struktury závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="89e8c-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="89e8c-114">Definice struktury Win32 `CONTEXT` naleznete v souboru záhlaví winnt.h.</span><span class="sxs-lookup"><span data-stu-id="89e8c-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89e8c-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89e8c-115">Remarks</span></span>  
 <span data-ttu-id="89e8c-116">Tato metoda je implementována zapisovače ladicí aplikace.</span><span class="sxs-lookup"><span data-stu-id="89e8c-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89e8c-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89e8c-117">Requirements</span></span>  
 <span data-ttu-id="89e8c-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89e8c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89e8c-119">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="89e8c-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="89e8c-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89e8c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89e8c-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89e8c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e8c-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="89e8c-122">See also</span></span>

- [<span data-ttu-id="89e8c-123">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89e8c-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
