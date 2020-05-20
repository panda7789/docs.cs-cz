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
ms.openlocfilehash: fe378307ce2bda6e1a267e46433ead70a0e2299e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616515"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="95c45-102">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="95c45-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="95c45-103">Poskytuje rozhraní pro správu aplikací, které jsou spouštěny modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="95c45-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95c45-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="95c45-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="95c45-105">Interfaces</span></span>  
  
|<span data-ttu-id="95c45-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="95c45-106">Interface</span></span>|<span data-ttu-id="95c45-107">Popis</span><span class="sxs-lookup"><span data-stu-id="95c45-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="95c45-108">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95c45-108">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)|<span data-ttu-id="95c45-109">Poskytuje metody pro konfiguraci modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="95c45-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="95c45-110">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95c45-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)|<span data-ttu-id="95c45-111">Poskytuje metody, které umožňují hostiteli explicitně spustit a zastavit modul CLR (Common Language Runtime), vytvořit a nakonfigurovat domény aplikace, získat přístup k výchozí doméně a vytvořit výčet všech domén spuštěných v procesu.</span><span class="sxs-lookup"><span data-stu-id="95c45-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="95c45-112">IDebuggerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95c45-112">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)|<span data-ttu-id="95c45-113">Poskytuje metody pro získání informací o stavu služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="95c45-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="95c45-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95c45-114">IGCHost Interface</span></span>](igchost-interface.md)|<span data-ttu-id="95c45-115">Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="95c45-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="95c45-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="95c45-116">"IValidator"</span></span>|<span data-ttu-id="95c45-117">Poskytuje metody pro ověřování přenosných spustitelných imagí a podrobné hlášení chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="95c45-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95c45-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95c45-118">Requirements</span></span>  
 <span data-ttu-id="95c45-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95c45-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c45-120">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="95c45-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="95c45-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="95c45-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95c45-122">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95c45-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c45-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="95c45-123">See also</span></span>

- [<span data-ttu-id="95c45-124">Třídy typu coclass hostování</span><span class="sxs-lookup"><span data-stu-id="95c45-124">Hosting Coclasses</span></span>](hosting-coclasses.md)
