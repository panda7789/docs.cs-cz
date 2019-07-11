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
ms.openlocfilehash: a0ea4bd222500015f6c78cb0455539aa2c24e681
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765613"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="c4e8f-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime – metoda</span><span class="sxs-lookup"><span data-stu-id="c4e8f-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="c4e8f-103">Vytvoří vazbu aktuální modul runtime pro všechny starší verze common language runtime (CLR) verze 2 aktivace rozhodnutí o zásadách.</span><span class="sxs-lookup"><span data-stu-id="c4e8f-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4e8f-104">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c4e8f-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c4e8f-105">Return Value</span></span>  
 <span data-ttu-id="c4e8f-106">Tato metoda vrátí následující konkrétní HRESULT:</span><span class="sxs-lookup"><span data-stu-id="c4e8f-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="c4e8f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4e8f-107">HRESULT</span></span>|<span data-ttu-id="c4e8f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="c4e8f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4e8f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4e8f-109">S_OK</span></span>|<span data-ttu-id="c4e8f-110">Byla vazba úspěšná, nebo tento modul runtime již byl vázaný jako starší verze runtime 2 Aktivace zásady CLR verze.</span><span class="sxs-lookup"><span data-stu-id="c4e8f-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="c4e8f-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="c4e8f-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="c4e8f-112">Jiný modul runtime je již vázán na starší verze 2 Aktivace zásady CLR verze.</span><span class="sxs-lookup"><span data-stu-id="c4e8f-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4e8f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4e8f-113">Remarks</span></span>  
 <span data-ttu-id="c4e8f-114">Pokud aktuální modul runtime je již vázán pro všechny starší verze CLR verze 2 aktivace rozhodnutí o zásadách (například pomocí `useLegacyV2RuntimeActivationPolicy` atribut na [ \<spuštění > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) v konfiguračním souboru), tato metoda nevrátí chybného výsledku; Výsledkem je místo toho S_OK, stejně jako by bylo, pokud metoda bylo úspěšně navázán Zásady aktivace starší verze.</span><span class="sxs-lookup"><span data-stu-id="c4e8f-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4e8f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4e8f-115">Requirements</span></span>  
 <span data-ttu-id="c4e8f-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4e8f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4e8f-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c4e8f-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c4e8f-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4e8f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4e8f-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4e8f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e8f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4e8f-120">See also</span></span>

- [<span data-ttu-id="c4e8f-121">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4e8f-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c4e8f-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c4e8f-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="c4e8f-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="c4e8f-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="c4e8f-124">\<Po spuštění > – Element</span><span class="sxs-lookup"><span data-stu-id="c4e8f-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
