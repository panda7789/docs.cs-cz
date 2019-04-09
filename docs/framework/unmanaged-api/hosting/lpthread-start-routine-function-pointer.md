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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27d1837f9f9f11ad34140f50ec41aa6fe8a62160
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119311"
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="84bdf-102">LPTHREAD_START_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="84bdf-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="84bdf-103">Odkazuje na funkci, která upozorňuje hostitele na spuštěný podproces ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="84bdf-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="84bdf-104">Tento ukazatel na funkci se už nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84bdf-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84bdf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84bdf-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84bdf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="84bdf-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="84bdf-107">[in] Ukazatel na kód, který byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="84bdf-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84bdf-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84bdf-108">Remarks</span></span>  
 <span data-ttu-id="84bdf-109">Funkce, které `LPTHREAD_START_ROUTINE` body je funkce zpětného volání a musí být implementováno tvůrci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="84bdf-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84bdf-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84bdf-110">Requirements</span></span>  
 <span data-ttu-id="84bdf-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84bdf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84bdf-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="84bdf-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84bdf-113">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="84bdf-113">**Library:** MSCorWks.dll</span></span>  
  
 **<span data-ttu-id="84bdf-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="84bdf-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="84bdf-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84bdf-115">See also</span></span>

- [<span data-ttu-id="84bdf-116">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="84bdf-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
