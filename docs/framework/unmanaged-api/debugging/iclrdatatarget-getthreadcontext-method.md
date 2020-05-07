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
ms.openlocfilehash: 5c0fb023dd355f3a9c1ed846913f86b354592ed5
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860607"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="aecaf-102">ICLRDataTarget::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="aecaf-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="aecaf-103">Získá aktuální kontext spuštění pro dané vlákno v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="aecaf-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="aecaf-104">Tato metoda je volána službou Common Language Runtime Data Access Services.</span><span class="sxs-lookup"><span data-stu-id="aecaf-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aecaf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aecaf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aecaf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aecaf-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="aecaf-107">pro Identifikátor operačního systému vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="aecaf-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="aecaf-108">pro Příznaky, které určují, které části kontextu se mají vrátit.</span><span class="sxs-lookup"><span data-stu-id="aecaf-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="aecaf-109">Implementace bude vracet alespoň tyto části kontextu.</span><span class="sxs-lookup"><span data-stu-id="aecaf-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="aecaf-110">pro Velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="aecaf-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="aecaf-111">mimo Ukazatel na vyrovnávací paměť, do které se má kontext umístit.</span><span class="sxs-lookup"><span data-stu-id="aecaf-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="aecaf-112">Data ve `context` vyrovnávací paměti musí být v podobě struktury Win32 `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="aecaf-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="aecaf-113">Kontext určuje data registru specifická pro procesor, takže definice struktury Win32 `CONTEXT` závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="aecaf-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="aecaf-114">Definici struktury Win32 `CONTEXT` najdete v souboru hlaviček Winnt. h.</span><span class="sxs-lookup"><span data-stu-id="aecaf-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aecaf-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aecaf-115">Remarks</span></span>  
 <span data-ttu-id="aecaf-116">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="aecaf-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aecaf-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aecaf-117">Requirements</span></span>  
 <span data-ttu-id="aecaf-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aecaf-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aecaf-119">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="aecaf-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="aecaf-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aecaf-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aecaf-121">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aecaf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aecaf-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="aecaf-122">See also</span></span>

- [<span data-ttu-id="aecaf-123">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aecaf-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
