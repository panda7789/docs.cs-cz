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
ms.openlocfilehash: cdf5776e1ac9907e63aba0e0d400e48aff683d51
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785303"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="6edd5-102">ICLRDataTarget::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="6edd5-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="6edd5-103">Nastaví aktuální kontext zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="6edd5-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="6edd5-104">Tato metoda je volána službou Common Language Runtime (CLR) pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="6edd5-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6edd5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6edd5-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6edd5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6edd5-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="6edd5-107">pro Identifikátor operačního systému vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="6edd5-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6edd5-108">pro Velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="6edd5-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="6edd5-109">pro Ukazatel na vyrovnávací paměť obsahující kontext.</span><span class="sxs-lookup"><span data-stu-id="6edd5-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="6edd5-110">Data ve vyrovnávací paměti `context` budou ve formátu `CONTEXT` struktury Win32.</span><span class="sxs-lookup"><span data-stu-id="6edd5-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="6edd5-111">Kontext určuje data registru pro konkrétní procesor, takže definice struktury `CONTEXT` Win32 závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="6edd5-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="6edd5-112">Definici struktury `CONTEXT` Win32 najdete v souboru hlaviček WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="6edd5-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6edd5-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6edd5-113">Remarks</span></span>  
 <span data-ttu-id="6edd5-114">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="6edd5-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6edd5-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6edd5-115">Requirements</span></span>  
 <span data-ttu-id="6edd5-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6edd5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6edd5-117">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="6edd5-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6edd5-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6edd5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6edd5-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6edd5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6edd5-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6edd5-120">See also</span></span>

- [<span data-ttu-id="6edd5-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6edd5-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
