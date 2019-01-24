---
title: WAITORTIMERCALLBACK – ukazatel na funkci
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d36ae3ef63c1324f77786ad55674bbdc257d984
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607131"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="d40f3-102">WAITORTIMERCALLBACK – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="d40f3-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="d40f3-103">Odkazuje na funkci, která upozorňuje hostitele, popisovače čekání (<xref:System.Threading.WaitHandle>) buď byl signalizován nebo vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="d40f3-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="d40f3-104">Tento ukazatel na funkci se už nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d40f3-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d40f3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d40f3-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d40f3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d40f3-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="d40f3-107">[in] Ukazatel na objekt, který obsahuje informace stanovené hostitelem.</span><span class="sxs-lookup"><span data-stu-id="d40f3-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="d40f3-108">[in] `true` Pokud popisovač čekání vypršel časový limit, nebo `false` Pokud bylo signalizováno.</span><span class="sxs-lookup"><span data-stu-id="d40f3-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d40f3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d40f3-109">Remarks</span></span>  
 <span data-ttu-id="d40f3-110">Funkce, které `WAITORTIMERCALLBACK` body je funkce zpětného volání a musí být implementováno tvůrci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="d40f3-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d40f3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d40f3-111">Requirements</span></span>  
 <span data-ttu-id="d40f3-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d40f3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d40f3-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d40f3-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d40f3-114">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="d40f3-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="d40f3-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d40f3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40f3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d40f3-116">See also</span></span>
- [<span data-ttu-id="d40f3-117">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="d40f3-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
