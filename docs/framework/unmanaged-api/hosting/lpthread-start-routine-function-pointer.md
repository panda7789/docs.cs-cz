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
ms.openlocfilehash: f29e4e52f9629073d676903e3f828a84023065bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="8f0e4-102">LPTHREAD_START_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="8f0e4-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="8f0e4-103">Odkazuje na funkci, která upozorní hostitele, který spustil vlákno k provedení.</span><span class="sxs-lookup"><span data-stu-id="8f0e4-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="8f0e4-104">Tento ukazatel na funkci se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f0e4-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f0e4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f0e4-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f0e4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f0e4-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="8f0e4-107">[v] Ukazatel na kód, který byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="8f0e4-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f0e4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f0e4-108">Remarks</span></span>  
 <span data-ttu-id="8f0e4-109">Funkce, ke kterému `LPTHREAD_START_ROUTINE` body je funkce zpětného volání a musí být implementována zapisovačem hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8f0e4-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f0e4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f0e4-110">Requirements</span></span>  
 <span data-ttu-id="8f0e4-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f0e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f0e4-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8f0e4-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f0e4-113">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="8f0e4-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="8f0e4-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f0e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f0e4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f0e4-115">See Also</span></span>  
 [<span data-ttu-id="8f0e4-116">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="8f0e4-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
