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
ms.openlocfilehash: 24a2c3baec0d958302101c295966f945ae98fa78
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490707"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="1f315-102">WAITORTIMERCALLBACK – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="1f315-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="1f315-103">Odkazuje na funkci, která upozorňuje hostitele, popisovače čekání (<xref:System.Threading.WaitHandle>) buď byl signalizován nebo vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="1f315-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="1f315-104">Tento ukazatel na funkci se už nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f315-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f315-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f315-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f315-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f315-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="1f315-107">[in] Ukazatel na objekt, který obsahuje informace stanovené hostitelem.</span><span class="sxs-lookup"><span data-stu-id="1f315-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="1f315-108">[in] `true` Pokud popisovač čekání vypršel časový limit, nebo `false` Pokud bylo signalizováno.</span><span class="sxs-lookup"><span data-stu-id="1f315-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f315-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f315-109">Remarks</span></span>  
 <span data-ttu-id="1f315-110">Funkce, které `WAITORTIMERCALLBACK` body je funkce zpětného volání a musí být implementováno tvůrci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f315-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f315-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f315-111">Requirements</span></span>  
 <span data-ttu-id="1f315-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f315-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f315-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f315-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f315-114">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="1f315-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="1f315-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f315-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f315-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f315-116">See also</span></span>
- [<span data-ttu-id="1f315-117">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="1f315-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
