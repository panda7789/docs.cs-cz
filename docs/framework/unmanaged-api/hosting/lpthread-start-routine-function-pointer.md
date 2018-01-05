---
title: "LPTHREAD_START_ROUTINE – ukazatel na funkci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LPTHREAD_START_ROUTINE
api_location: mscoree.dll
api_type: COM
f1_keywords: LPTHREAD_START_ROUTINE
helpviewer_keywords: LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d28cdbfa2cb6c2c1f6b730e34b623a621119bc3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="e7842-102">LPTHREAD_START_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="e7842-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="e7842-103">Odkazuje na funkci, která upozorní hostitele, který spustil vlákno k provedení.</span><span class="sxs-lookup"><span data-stu-id="e7842-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="e7842-104">Tento ukazatel na funkci se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7842-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7842-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7842-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7842-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7842-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="e7842-107">[v] Ukazatel na kód, který byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="e7842-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7842-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7842-108">Remarks</span></span>  
 <span data-ttu-id="e7842-109">Funkce, ke kterému `LPTHREAD_START_ROUTINE` body je funkce zpětného volání a musí být implementována zapisovačem hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e7842-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7842-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7842-110">Requirements</span></span>  
 <span data-ttu-id="e7842-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7842-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7842-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e7842-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7842-113">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="e7842-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="e7842-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7842-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7842-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7842-115">See Also</span></span>  
 [<span data-ttu-id="e7842-116">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="e7842-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
