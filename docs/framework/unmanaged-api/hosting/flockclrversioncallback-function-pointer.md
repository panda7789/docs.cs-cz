---
title: "FLockClrVersionCallback – ukazatel na funkci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FLockClrVersionCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: FLockClrVersionCallback
helpviewer_keywords: FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90b3bd053eb2e1161d6bb107afe9b3c627b1b207
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="4f3bf-102">FLockClrVersionCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="4f3bf-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="4f3bf-103">Odkazuje na funkci, která běžné volání language runtime (CLR) označíte, že inicializace má buď spustit nebo byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="4f3bf-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="4f3bf-104">Tento ukazatel na funkci se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f3bf-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f3bf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f3bf-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="4f3bf-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f3bf-106">Remarks</span></span>  
 <span data-ttu-id="4f3bf-107">Tato funkce je implementováno modulem hostitele.</span><span class="sxs-lookup"><span data-stu-id="4f3bf-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f3bf-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f3bf-108">Requirements</span></span>  
 <span data-ttu-id="4f3bf-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f3bf-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f3bf-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4f3bf-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f3bf-111">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="4f3bf-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="4f3bf-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f3bf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f3bf-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f3bf-113">See Also</span></span>  
 [<span data-ttu-id="4f3bf-114">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="4f3bf-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 [<span data-ttu-id="4f3bf-115">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="4f3bf-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
