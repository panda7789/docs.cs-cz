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
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179130"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="8ef20-102">ICLRDataTarget::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="8ef20-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="8ef20-103">Nastaví aktuální kontext zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="8ef20-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="8ef20-104">Tato metoda je volána služby přístupu k datům CLR (COMMON Language runtime).</span><span class="sxs-lookup"><span data-stu-id="8ef20-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef20-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ef20-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ef20-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ef20-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="8ef20-107">[v] Identifikátor operačního systému podprocesu v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="8ef20-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="8ef20-108">[v] Velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="8ef20-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="8ef20-109">[v] Ukazatel na vyrovnávací paměť obsahující kontext.</span><span class="sxs-lookup"><span data-stu-id="8ef20-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="8ef20-110">Data ve `context` vyrovnávací paměti budou ve formátu win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="8ef20-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="8ef20-111">Kontext určuje data registru specifické pro procesor, takže definice `CONTEXT` win32 struktury závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="8ef20-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="8ef20-112">Definice struktury Win32 `CONTEXT` naleznete v souboru záhlaví winnt.h.</span><span class="sxs-lookup"><span data-stu-id="8ef20-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ef20-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ef20-113">Remarks</span></span>  
 <span data-ttu-id="8ef20-114">Tato metoda je implementována zapisovače ladicí aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ef20-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef20-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ef20-115">Requirements</span></span>  
 <span data-ttu-id="8ef20-116">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef20-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef20-117">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="8ef20-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8ef20-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ef20-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ef20-119">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef20-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef20-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ef20-120">See also</span></span>

- [<span data-ttu-id="8ef20-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ef20-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
