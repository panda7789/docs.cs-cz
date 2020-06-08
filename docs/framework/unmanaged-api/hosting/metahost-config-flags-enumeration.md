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
ms.openlocfilehash: 6b37fcfc04e3ec880c67f102ec12d7f3e4b06a43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493159"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="7ebad-102">METAHOST_CONFIG_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="7ebad-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="7ebad-103">Popisuje možné příznaky vrácené v `pdwConfigFlags` parametru metody [ICLRMetaHostPolicy –:: GetRequestedRuntime –](iclrmetahostpolicy-getrequestedruntime-method.md) , která označuje přítomnost a nastavení `useLegacyV2RuntimeActivationPolicy` atributu v [ \<startup> elementu](../../configure-apps/file-schema/startup/startup-element.md) konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7ebad-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ebad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ebad-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="7ebad-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7ebad-105">Members</span></span>  
  
|<span data-ttu-id="7ebad-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7ebad-106">Member</span></span>|<span data-ttu-id="7ebad-107">Description</span><span class="sxs-lookup"><span data-stu-id="7ebad-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="7ebad-108">`useLegacyV2RuntimeActivationPolicy`Atribut nebyl v [ \<startup> elementu](../../configure-apps/file-schema/startup/startup-element.md)přítomen.</span><span class="sxs-lookup"><span data-stu-id="7ebad-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="7ebad-109">`useLegacyV2RuntimeActivationPolicy`Atribut byl přítomen a nastaven na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="7ebad-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="7ebad-110">`useLegacyV2RuntimeActivationPolicy`Atribut byl přítomen a nastaven na hodnotu `false` .</span><span class="sxs-lookup"><span data-stu-id="7ebad-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="7ebad-111">Použijte tuto masku na hodnotu vrácenou v `pdwConfigFlags` , abyste získali hodnoty relevantní pro `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="7ebad-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ebad-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ebad-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ebad-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ebad-113">Requirements</span></span>  
 <span data-ttu-id="7ebad-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ebad-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ebad-115">**Hlavička:** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="7ebad-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="7ebad-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7ebad-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ebad-117">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ebad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ebad-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ebad-118">See also</span></span>

- [<span data-ttu-id="7ebad-119">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="7ebad-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="7ebad-120">GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="7ebad-120">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="7ebad-121">\<startup>Objekt</span><span class="sxs-lookup"><span data-stu-id="7ebad-121">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
