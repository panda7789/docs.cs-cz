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
ms.openlocfilehash: ee5dd611888ec52e360ef45fab4c01e9c5b2d6bb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009444"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="def75-102">WAITORTIMERCALLBACK – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="def75-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="def75-103">Odkazuje na funkci, která upozorňuje hostitele, že obslužná rutina čekání ( <xref:System.Threading.WaitHandle> ) buď byla signalizována, nebo vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="def75-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="def75-104">Tento ukazatel funkce je zastaralý v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="def75-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="def75-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="def75-105">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="def75-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="def75-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="def75-107">pro Ukazatel na objekt, který obsahuje informace definované hostitelem.</span><span class="sxs-lookup"><span data-stu-id="def75-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="def75-108">[in] `true` Pokud vypršel časový limit čekání nebo `false` zda byl signalizována signál.</span><span class="sxs-lookup"><span data-stu-id="def75-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="def75-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="def75-109">Remarks</span></span>  
 <span data-ttu-id="def75-110">Funkce, na které `WAITORTIMERCALLBACK` jsou body funkce zpětného volání a které musí být implementovány zapisovačí hostující aplikace.</span><span class="sxs-lookup"><span data-stu-id="def75-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="def75-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="def75-111">Requirements</span></span>  
 <span data-ttu-id="def75-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="def75-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="def75-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="def75-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="def75-114">**Knihovna:** Knihovny Mscorwks. dll</span><span class="sxs-lookup"><span data-stu-id="def75-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="def75-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="def75-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def75-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="def75-116">See also</span></span>

- [<span data-ttu-id="def75-117">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="def75-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
