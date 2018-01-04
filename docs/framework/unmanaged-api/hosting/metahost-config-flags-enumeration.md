---
title: "METAHOST_CONFIG_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: METAHOST_CONFIG_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: METAHOST_CONFIG_FLAGS
helpviewer_keywords: METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5743356cdb2a99c4c5eb0c958bc5ca0815146d4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="ce708-102">METAHOST_CONFIG_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="ce708-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="ce708-103">Popisuje možné příznaky, vrátí se v `pdwConfigFlags` parametr [iclrmetahostpolicy::getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda označující přítomnosti a nastavení `useLegacyV2RuntimeActivationPolicy` atribut [ \<spuštění > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ce708-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce708-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce708-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="ce708-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ce708-105">Members</span></span>  
  
|<span data-ttu-id="ce708-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ce708-106">Member</span></span>|<span data-ttu-id="ce708-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ce708-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="ce708-108">`useLegacyV2RuntimeActivationPolicy` Atribut nebyl nalezen v [ \<spuštění > Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="ce708-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="ce708-109">`useLegacyV2RuntimeActivationPolicy` Atribut byl přítomen a nastavené na `true`.</span><span class="sxs-lookup"><span data-stu-id="ce708-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="ce708-110">`useLegacyV2RuntimeActivationPolicy` Atribut byl přítomen a nastavené na `false`.</span><span class="sxs-lookup"><span data-stu-id="ce708-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="ce708-111">Tato maska týkají hodnota vrácená v `pdwConfigFlags` získat hodnoty relevantní pro `useLegacyV2RuntimeActivationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="ce708-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce708-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce708-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce708-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce708-113">Requirements</span></span>  
 <span data-ttu-id="ce708-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce708-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce708-115">**Záhlaví:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="ce708-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="ce708-116">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce708-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce708-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce708-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce708-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce708-118">See Also</span></span>  
 [<span data-ttu-id="ce708-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="ce708-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="ce708-120">GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="ce708-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)  
 [<span data-ttu-id="ce708-121">\<spuštění > elementu</span><span class="sxs-lookup"><span data-stu-id="ce708-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
