---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 647c87b6f42b01922a385d502d72410af3140cd2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095344"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="ac357-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime – metoda</span><span class="sxs-lookup"><span data-stu-id="ac357-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="ac357-103">Vytvoří vazbu aktuální modul runtime pro všechny starší verze common language runtime (CLR) verze 2 aktivace rozhodnutí o zásadách.</span><span class="sxs-lookup"><span data-stu-id="ac357-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac357-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac357-104">Syntax</span></span>  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ac357-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ac357-105">Return Value</span></span>  
 <span data-ttu-id="ac357-106">Tato metoda vrátí následující konkrétní HRESULT:</span><span class="sxs-lookup"><span data-stu-id="ac357-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="ac357-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac357-107">HRESULT</span></span>|<span data-ttu-id="ac357-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ac357-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac357-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac357-109">S_OK</span></span>|<span data-ttu-id="ac357-110">Byla vazba úspěšná, nebo tento modul runtime již byl vázaný jako starší verze runtime 2 Aktivace zásady CLR verze.</span><span class="sxs-lookup"><span data-stu-id="ac357-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="ac357-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="ac357-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="ac357-112">Jiný modul runtime je již vázán na starší verze 2 Aktivace zásady CLR verze.</span><span class="sxs-lookup"><span data-stu-id="ac357-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac357-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac357-113">Remarks</span></span>  
 <span data-ttu-id="ac357-114">Pokud aktuální modul runtime je již vázán pro všechny starší verze CLR verze 2 aktivace rozhodnutí o zásadách (například pomocí `useLegacyV2RuntimeActivationPolicy` atribut na [ \<spuštění > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) v konfiguračním souboru), tato metoda nevrátí chybného výsledku; Výsledkem je místo toho S_OK, stejně jako by bylo, pokud metoda bylo úspěšně navázán Zásady aktivace starší verze.</span><span class="sxs-lookup"><span data-stu-id="ac357-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac357-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac357-115">Requirements</span></span>  
 <span data-ttu-id="ac357-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac357-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac357-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ac357-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ac357-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac357-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac357-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac357-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac357-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac357-120">See also</span></span>

- [<span data-ttu-id="ac357-121">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac357-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ac357-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ac357-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ac357-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="ac357-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="ac357-124">\<Po spuštění > – Element</span><span class="sxs-lookup"><span data-stu-id="ac357-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
