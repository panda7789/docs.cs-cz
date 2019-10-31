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
ms.openlocfilehash: c6e0c02af93b9df726202f397bbb2afc306f3b3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090880"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="87c25-102">LPTHREAD_START_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="87c25-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="87c25-103">Odkazuje na funkci, která upozorňuje hostitele na spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="87c25-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="87c25-104">Tento ukazatel funkce je zastaralý v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="87c25-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c25-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87c25-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87c25-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="87c25-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="87c25-107">pro Ukazatel na kód, který zahájil provádění.</span><span class="sxs-lookup"><span data-stu-id="87c25-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87c25-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87c25-108">Remarks</span></span>  
 <span data-ttu-id="87c25-109">Funkce, na kterou `LPTHREAD_START_ROUTINE` body, je funkce zpětného volání a musí být implementována zapisovačí hostující aplikace.</span><span class="sxs-lookup"><span data-stu-id="87c25-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87c25-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87c25-110">Requirements</span></span>  
 <span data-ttu-id="87c25-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87c25-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87c25-112">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="87c25-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87c25-113">**Knihovna:** Knihovny Mscorwks. dll</span><span class="sxs-lookup"><span data-stu-id="87c25-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="87c25-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87c25-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c25-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87c25-115">See also</span></span>

- [<span data-ttu-id="87c25-116">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="87c25-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
