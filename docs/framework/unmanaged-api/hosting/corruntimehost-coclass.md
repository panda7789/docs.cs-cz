---
title: "CorRuntimeHost – třída typu coclass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRuntimeHost
helpviewer_keywords: CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23bee1a79dfb54a696495fdb61a7ba9ba4b4c143
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="497bc-102">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="497bc-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="497bc-103">Poskytuje rozhraní pro správu aplikací, které se spouštějí modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="497bc-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="497bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="497bc-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="497bc-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="497bc-105">Interfaces</span></span>  
  
|<span data-ttu-id="497bc-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="497bc-106">Interface</span></span>|<span data-ttu-id="497bc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="497bc-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="497bc-108">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="497bc-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="497bc-109">Poskytuje metody pro konfiguraci common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="497bc-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="497bc-110">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="497bc-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="497bc-111">Poskytuje metody, které umožní hostitele spuštění a zastavení modulu CLR explicitně, vytvořte a nakonfigurujte aplikační domény, pro přístup k výchozí doméně a chcete získat výčet všech domén, které jsou spuštěné v procesu.</span><span class="sxs-lookup"><span data-stu-id="497bc-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="497bc-112">IDebuggerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="497bc-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="497bc-113">Poskytuje metody pro získání informací o stavu služby ladění.</span><span class="sxs-lookup"><span data-stu-id="497bc-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="497bc-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="497bc-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="497bc-115">Poskytuje metody pro získání informací o systém kolekce paměti a řízení některých aspektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="497bc-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="497bc-116">IValidator "–"</span><span class="sxs-lookup"><span data-stu-id="497bc-116">"IValidator"</span></span>|<span data-ttu-id="497bc-117">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie a podrobné sestavy chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="497bc-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="497bc-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="497bc-118">Requirements</span></span>  
 <span data-ttu-id="497bc-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="497bc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="497bc-120">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="497bc-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="497bc-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="497bc-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="497bc-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="497bc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497bc-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="497bc-123">See Also</span></span>  
 [<span data-ttu-id="497bc-124">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="497bc-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
