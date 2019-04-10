---
title: CLRRuntimeHost – třída typu coclass
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bae2d134c412023d0f126453b5285662d994c78
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207757"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="9d72d-102">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="9d72d-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="9d72d-103">Poskytuje rozhraní pro správu provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="9d72d-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d72d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d72d-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="9d72d-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d72d-105">Interfaces</span></span>  
  
|<span data-ttu-id="9d72d-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d72d-106">Interface</span></span>|<span data-ttu-id="9d72d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9d72d-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="9d72d-108">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d72d-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="9d72d-109">Poskytuje metody pro řízení spouštění aplikace modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="9d72d-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="9d72d-110">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d72d-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="9d72d-111">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie a pro generování podrobných sestav chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="9d72d-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d72d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d72d-112">Requirements</span></span>  
 <span data-ttu-id="9d72d-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d72d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d72d-114">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="9d72d-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="9d72d-115">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d72d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9d72d-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9d72d-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d72d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d72d-117">See also</span></span>

- [<span data-ttu-id="9d72d-118">Třídy typu coclass hostování</span><span class="sxs-lookup"><span data-stu-id="9d72d-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
