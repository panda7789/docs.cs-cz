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
ms.openlocfilehash: 942c9544a6ce868c3b6296569d4a16a44281cdba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758316"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="e37e0-102">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="e37e0-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="e37e0-103">Poskytuje rozhraní pro správu aplikací, které se spouštějí modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="e37e0-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e37e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e37e0-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="e37e0-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="e37e0-105">Interfaces</span></span>  
  
|<span data-ttu-id="e37e0-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="e37e0-106">Interface</span></span>|<span data-ttu-id="e37e0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e37e0-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="e37e0-108">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e37e0-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="e37e0-109">Poskytuje metody pro konfiguraci common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e37e0-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="e37e0-110">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e37e0-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="e37e0-111">Poskytuje metody, které umožní hostitele ke spouštění a zastavování modul common language runtime explicitně, vytvoření a konfigurace domény aplikace, pro přístup k výchozí doménu a chcete získat výčet všech doménách spuštěných v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e37e0-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="e37e0-112">IDebuggerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e37e0-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="e37e0-113">Poskytuje metody pro získání informací o stavu služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="e37e0-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="e37e0-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e37e0-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="e37e0-115">Poskytuje metody pro získání informací o systému uvolňování paměti kolekce a pro řízení některé aspekty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e37e0-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="e37e0-116">IValidator "–"</span><span class="sxs-lookup"><span data-stu-id="e37e0-116">"IValidator"</span></span>|<span data-ttu-id="e37e0-117">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie a generování podrobných sestav chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="e37e0-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e37e0-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e37e0-118">Requirements</span></span>  
 <span data-ttu-id="e37e0-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e37e0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e37e0-120">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="e37e0-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e37e0-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e37e0-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e37e0-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e37e0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37e0-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e37e0-123">See also</span></span>

- [<span data-ttu-id="e37e0-124">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="e37e0-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
