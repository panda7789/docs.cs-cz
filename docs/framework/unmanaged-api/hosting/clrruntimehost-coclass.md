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
ms.openlocfilehash: 841b05ca1037d82046820554878d883f94687d34
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779146"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="22a1e-102">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="22a1e-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="22a1e-103">Poskytuje rozhraní pro správu provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="22a1e-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22a1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22a1e-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="22a1e-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="22a1e-105">Interfaces</span></span>  
  
|<span data-ttu-id="22a1e-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="22a1e-106">Interface</span></span>|<span data-ttu-id="22a1e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="22a1e-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="22a1e-108">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22a1e-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="22a1e-109">Poskytuje metody pro řízení spouštění aplikace modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="22a1e-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="22a1e-110">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22a1e-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="22a1e-111">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie a pro generování podrobných sestav chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="22a1e-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22a1e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22a1e-112">Requirements</span></span>  
 <span data-ttu-id="22a1e-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22a1e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22a1e-114">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="22a1e-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="22a1e-115">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22a1e-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22a1e-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22a1e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a1e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22a1e-117">See also</span></span>

- [<span data-ttu-id="22a1e-118">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="22a1e-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
