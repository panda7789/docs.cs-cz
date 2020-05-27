---
title: LPTHREAD_START_ROUTINE – ukazatel na funkci
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
ms.openlocfilehash: 84cdb42b11ad70f54f21ae36ca2734dc794d06d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008466"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="87eb5-102">LPTHREAD_START_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="87eb5-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="87eb5-103">Odkazuje na funkci, která upozorňuje hostitele na spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="87eb5-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="87eb5-104">Tento ukazatel funkce je zastaralý v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="87eb5-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87eb5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87eb5-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87eb5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="87eb5-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="87eb5-107">pro Ukazatel na kód, který zahájil provádění.</span><span class="sxs-lookup"><span data-stu-id="87eb5-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87eb5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87eb5-108">Remarks</span></span>  
 <span data-ttu-id="87eb5-109">Funkce, na které `LPTHREAD_START_ROUTINE` jsou body funkce zpětného volání a které musí být implementovány zapisovačí hostující aplikace.</span><span class="sxs-lookup"><span data-stu-id="87eb5-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87eb5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87eb5-110">Requirements</span></span>  
 <span data-ttu-id="87eb5-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87eb5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87eb5-112">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="87eb5-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87eb5-113">**Knihovna:** Knihovny Mscorwks. dll</span><span class="sxs-lookup"><span data-stu-id="87eb5-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="87eb5-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87eb5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87eb5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="87eb5-115">See also</span></span>

- [<span data-ttu-id="87eb5-116">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="87eb5-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
