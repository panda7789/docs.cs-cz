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
ms.openlocfilehash: 0d34577f0f785bc851646423b8cd732ab4d1dae0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113852"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="b8a89-102">ICLRDataTarget::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="b8a89-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="b8a89-103">Získá aktuální kontext spuštění pro dané vlákno v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="b8a89-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="b8a89-104">Tato metoda je volána službou Common Language Runtime Data Access Services.</span><span class="sxs-lookup"><span data-stu-id="b8a89-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8a89-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8a89-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8a89-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8a89-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="b8a89-107">pro Identifikátor operačního systému vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="b8a89-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="b8a89-108">pro Příznaky, které určují, které části kontextu se mají vrátit.</span><span class="sxs-lookup"><span data-stu-id="b8a89-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="b8a89-109">Implementace bude vracet alespoň tyto části kontextu.</span><span class="sxs-lookup"><span data-stu-id="b8a89-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="b8a89-110">pro Velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="b8a89-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="b8a89-111">mimo Ukazatel na vyrovnávací paměť, do které se má kontext umístit.</span><span class="sxs-lookup"><span data-stu-id="b8a89-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="b8a89-112">Data ve vyrovnávací paměti `context` musí být ve formátu `CONTEXT` struktury Win32.</span><span class="sxs-lookup"><span data-stu-id="b8a89-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="b8a89-113">Kontext určuje data registru pro konkrétní procesor, takže definice struktury `CONTEXT` Win32 závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="b8a89-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="b8a89-114">Definici struktury `CONTEXT` Win32 najdete v souboru hlaviček WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="b8a89-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8a89-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8a89-115">Remarks</span></span>  
 <span data-ttu-id="b8a89-116">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="b8a89-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8a89-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8a89-117">Requirements</span></span>  
 <span data-ttu-id="b8a89-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8a89-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8a89-119">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="b8a89-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b8a89-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b8a89-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8a89-121">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8a89-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a89-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8a89-122">See also</span></span>

- [<span data-ttu-id="b8a89-123">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8a89-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
