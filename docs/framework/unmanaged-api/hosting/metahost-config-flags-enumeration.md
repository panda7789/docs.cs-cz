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
ms.openlocfilehash: 13a7ad5b59dd318f823645d28f9c3ccbec8a8cb0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781090"
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="a3a28-102">METAHOST_CONFIG_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="a3a28-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="a3a28-103">Popisuje možné příznaky vrácené v `pdwConfigFlags` parametr [iclrmetahostpolicy::getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda udávající přítomnost a nastavení `useLegacyV2RuntimeActivationPolicy` atribut [ \<spouštěný > prvku](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a3a28-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3a28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3a28-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="a3a28-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a3a28-105">Members</span></span>  
  
|<span data-ttu-id="a3a28-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a3a28-106">Member</span></span>|<span data-ttu-id="a3a28-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a3a28-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="a3a28-108">`useLegacyV2RuntimeActivationPolicy` Nebyl k dispozici v atributu [ \<spuštění > Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="a3a28-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="a3a28-109">`useLegacyV2RuntimeActivationPolicy` Atribut byl k dispozici a nastavené na `true`.</span><span class="sxs-lookup"><span data-stu-id="a3a28-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="a3a28-110">`useLegacyV2RuntimeActivationPolicy` Atribut byl k dispozici a nastavené na `false`.</span><span class="sxs-lookup"><span data-stu-id="a3a28-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="a3a28-111">Použití této masky hodnotu vrácenou v `pdwConfigFlags` abyste získali hodnoty pro relevantní `useLegacyV2RuntimeActivationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="a3a28-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3a28-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3a28-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3a28-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3a28-113">Requirements</span></span>  
 <span data-ttu-id="a3a28-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3a28-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3a28-115">**Záhlaví:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="a3a28-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="a3a28-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3a28-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3a28-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3a28-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a28-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3a28-118">See also</span></span>

- [<span data-ttu-id="a3a28-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="a3a28-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="a3a28-120">GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="a3a28-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="a3a28-121">\<Po spuštění > – Element</span><span class="sxs-lookup"><span data-stu-id="a3a28-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
