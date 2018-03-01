---
title: "CLRRuntimeHost – třída typu coclass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18e4518a2e321609a8add06c399ed9588748d1ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="219ff-102">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="219ff-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="219ff-103">Poskytuje rozhraní pro správu provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="219ff-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="219ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="219ff-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="219ff-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="219ff-105">Interfaces</span></span>  
  
|<span data-ttu-id="219ff-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="219ff-106">Interface</span></span>|<span data-ttu-id="219ff-107">Popis</span><span class="sxs-lookup"><span data-stu-id="219ff-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="219ff-108">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="219ff-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="219ff-109">Poskytuje metody pro řízení provádění aplikací modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="219ff-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="219ff-110">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="219ff-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="219ff-111">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie a podrobné sestavy chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="219ff-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="219ff-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="219ff-112">Requirements</span></span>  
 <span data-ttu-id="219ff-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="219ff-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="219ff-114">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="219ff-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="219ff-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="219ff-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="219ff-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="219ff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="219ff-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="219ff-117">See Also</span></span>  
 [<span data-ttu-id="219ff-118">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="219ff-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
