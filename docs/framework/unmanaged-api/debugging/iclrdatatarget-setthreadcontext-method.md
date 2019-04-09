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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3f98ab65512a380ebd4dc0ecd50e36f94a6d6b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104153"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="79405-102">ICLRDataTarget::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="79405-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="79405-103">Nastaví aktuální kontext ze zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="79405-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="79405-104">Tato metoda je volána službami common language runtime (CLR) přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="79405-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79405-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79405-105">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79405-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="79405-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="79405-107">[in] Operační systém identifikátor vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="79405-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="79405-108">[in] Velikost kontext.</span><span class="sxs-lookup"><span data-stu-id="79405-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="79405-109">[in] Ukazatel do vyrovnávací paměti, který obsahuje kontext.</span><span class="sxs-lookup"><span data-stu-id="79405-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="79405-110">Data v `context` vyrovnávací paměť bude ve formátu Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="79405-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="79405-111">Kontext určuje data registru specifické pro procesor, takže definice Win32 `CONTEXT` struktura závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="79405-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="79405-112">Najdete v souboru WinNT.h hlavičkový soubor pro definici Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="79405-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79405-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79405-113">Remarks</span></span>  
 <span data-ttu-id="79405-114">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="79405-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79405-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79405-115">Requirements</span></span>  
 <span data-ttu-id="79405-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79405-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79405-117">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="79405-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="79405-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79405-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="79405-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="79405-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="79405-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79405-120">See also</span></span>

- [<span data-ttu-id="79405-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79405-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
