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
ms.openlocfilehash: 07cab119810c4da25d16a4ad7c13f2d2bda16455
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140308"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="b6c30-102">METAHOST_CONFIG_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="b6c30-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="b6c30-103">Popisuje možné příznaky vrácené v parametru `pdwConfigFlags` metody [ICLRMetaHostPolicy –:: GetRequestedRuntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) , která označuje přítomnost a nastavení atributu `useLegacyV2RuntimeActivationPolicy` v [\<spouštění > prvku](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="b6c30-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6c30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6c30-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="b6c30-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b6c30-105">Members</span></span>  
  
|<span data-ttu-id="b6c30-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b6c30-106">Member</span></span>|<span data-ttu-id="b6c30-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b6c30-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="b6c30-108">Atribut `useLegacyV2RuntimeActivationPolicy` nebyl přítomen v [elementu\<startup >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="b6c30-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="b6c30-109">Atribut `useLegacyV2RuntimeActivationPolicy` existoval a byl nastaven na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="b6c30-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="b6c30-110">Atribut `useLegacyV2RuntimeActivationPolicy` existoval a byl nastaven na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="b6c30-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="b6c30-111">Použijte tuto masku na hodnotu vrácenou v `pdwConfigFlags`, abyste získali hodnoty relevantní pro `useLegacyV2RuntimeActivationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="b6c30-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6c30-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6c30-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6c30-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6c30-113">Requirements</span></span>  
 <span data-ttu-id="b6c30-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6c30-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6c30-115">**Hlavička:** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="b6c30-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="b6c30-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b6c30-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6c30-117">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6c30-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c30-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6c30-118">See also</span></span>

- [<span data-ttu-id="b6c30-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="b6c30-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="b6c30-120">GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="b6c30-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="b6c30-121">\<> element Startup</span><span class="sxs-lookup"><span data-stu-id="b6c30-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
