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
ms.openlocfilehash: 512009e053605e2018f1fcbafa422c1a36ddecc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136910"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="f4243-102">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="f4243-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="f4243-103">Poskytuje rozhraní pro správu aplikací, které jsou spouštěny modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="f4243-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4243-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4243-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="f4243-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4243-105">Interfaces</span></span>  
  
|<span data-ttu-id="f4243-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4243-106">Interface</span></span>|<span data-ttu-id="f4243-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f4243-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="f4243-108">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4243-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="f4243-109">Poskytuje metody pro konfiguraci modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="f4243-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="f4243-110">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4243-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="f4243-111">Poskytuje metody, které umožňují hostiteli explicitně spustit a zastavit modul CLR (Common Language Runtime), vytvořit a nakonfigurovat domény aplikace, získat přístup k výchozí doméně a vytvořit výčet všech domén spuštěných v procesu.</span><span class="sxs-lookup"><span data-stu-id="f4243-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="f4243-112">IDebuggerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4243-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="f4243-113">Poskytuje metody pro získání informací o stavu služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="f4243-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="f4243-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4243-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="f4243-115">Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f4243-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="f4243-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="f4243-116">"IValidator"</span></span>|<span data-ttu-id="f4243-117">Poskytuje metody pro ověřování přenosných spustitelných imagí a podrobné hlášení chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="f4243-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4243-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4243-118">Requirements</span></span>  
 <span data-ttu-id="f4243-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4243-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4243-120">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="f4243-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="f4243-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f4243-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4243-122">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4243-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4243-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4243-123">See also</span></span>

- [<span data-ttu-id="f4243-124">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="f4243-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
