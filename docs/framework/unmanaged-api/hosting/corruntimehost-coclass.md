---
title: CorRuntimeHost – třída typu coclass
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2143fc13db1757ac2fa8a9c5a43f104a0c519ca0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218560"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="d5a58-102">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="d5a58-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="d5a58-103">Poskytuje rozhraní pro správu aplikací, které se spouštějí modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d5a58-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5a58-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="d5a58-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5a58-105">Interfaces</span></span>  
  
|<span data-ttu-id="d5a58-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5a58-106">Interface</span></span>|<span data-ttu-id="d5a58-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d5a58-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="d5a58-108">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5a58-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="d5a58-109">Poskytuje metody pro konfiguraci common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d5a58-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="d5a58-110">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5a58-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="d5a58-111">Poskytuje metody, které umožní hostitele ke spouštění a zastavování modul common language runtime explicitně, vytvoření a konfigurace domény aplikace, pro přístup k výchozí doménu a chcete získat výčet všech doménách spuštěných v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d5a58-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="d5a58-112">IDebuggerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5a58-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="d5a58-113">Poskytuje metody pro získání informací o stavu služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="d5a58-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="d5a58-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5a58-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="d5a58-115">Poskytuje metody pro získání informací o systému uvolňování paměti kolekce a pro řízení některé aspekty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d5a58-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="d5a58-116">IValidator "–"</span><span class="sxs-lookup"><span data-stu-id="d5a58-116">"IValidator"</span></span>|<span data-ttu-id="d5a58-117">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie a generování podrobných sestav chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="d5a58-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5a58-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5a58-118">Requirements</span></span>  
 <span data-ttu-id="d5a58-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5a58-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5a58-120">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="d5a58-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d5a58-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5a58-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5a58-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5a58-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a58-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5a58-123">See also</span></span>

- [<span data-ttu-id="d5a58-124">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="d5a58-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
