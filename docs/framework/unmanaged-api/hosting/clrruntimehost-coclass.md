---
title: "CLRRuntimeHost – třída typu coclass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CLRRuntimeHost
helpviewer_keywords: CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 372b2466baaa76ba47a6710447d93f9fa6bb967f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="cf48d-102">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="cf48d-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="cf48d-103">Poskytuje rozhraní pro správu provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="cf48d-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf48d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf48d-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="cf48d-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf48d-105">Interfaces</span></span>  
  
|<span data-ttu-id="cf48d-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf48d-106">Interface</span></span>|<span data-ttu-id="cf48d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cf48d-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="cf48d-108">Iclrruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf48d-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="cf48d-109">Poskytuje metody pro řízení provádění aplikací modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="cf48d-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="cf48d-110">Iclrvalidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf48d-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="cf48d-111">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie a podrobné sestavy chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="cf48d-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf48d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf48d-112">Requirements</span></span>  
 <span data-ttu-id="cf48d-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf48d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf48d-114">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="cf48d-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="cf48d-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf48d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf48d-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf48d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf48d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf48d-117">See Also</span></span>  
 [<span data-ttu-id="cf48d-118">Třídy typu coclass hostování</span><span class="sxs-lookup"><span data-stu-id="cf48d-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
