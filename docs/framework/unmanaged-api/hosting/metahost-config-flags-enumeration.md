---
title: METAHOST_CONFIG_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e322f5c7119d13c8a872bd87d00c1e55324b581
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135770"
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="d9fb3-102">METAHOST_CONFIG_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="d9fb3-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="d9fb3-103">Popisuje možné příznaky vrácené v `pdwConfigFlags` parametr [iclrmetahostpolicy::getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda udávající přítomnost a nastavení `useLegacyV2RuntimeActivationPolicy` atribut [ \<spouštěný > prvku](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d9fb3-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9fb3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9fb3-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="d9fb3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d9fb3-105">Members</span></span>  
  
|<span data-ttu-id="d9fb3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d9fb3-106">Member</span></span>|<span data-ttu-id="d9fb3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d9fb3-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="d9fb3-108">`useLegacyV2RuntimeActivationPolicy` Nebyl k dispozici v atributu [ \<spuštění > Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="d9fb3-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="d9fb3-109">`useLegacyV2RuntimeActivationPolicy` Atribut byl k dispozici a nastavené na `true`.</span><span class="sxs-lookup"><span data-stu-id="d9fb3-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="d9fb3-110">`useLegacyV2RuntimeActivationPolicy` Atribut byl k dispozici a nastavené na `false`.</span><span class="sxs-lookup"><span data-stu-id="d9fb3-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="d9fb3-111">Použití této masky hodnotu vrácenou v `pdwConfigFlags` abyste získali hodnoty pro relevantní `useLegacyV2RuntimeActivationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="d9fb3-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9fb3-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9fb3-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9fb3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9fb3-113">Requirements</span></span>  
 <span data-ttu-id="d9fb3-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9fb3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9fb3-115">**Záhlaví:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="d9fb3-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="d9fb3-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9fb3-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d9fb3-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d9fb3-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d9fb3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9fb3-118">See also</span></span>

- [<span data-ttu-id="d9fb3-119">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="d9fb3-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="d9fb3-120">GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="d9fb3-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="d9fb3-121">\<Po spuštění > – Element</span><span class="sxs-lookup"><span data-stu-id="d9fb3-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
