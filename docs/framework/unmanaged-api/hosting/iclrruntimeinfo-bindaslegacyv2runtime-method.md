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
ms.openlocfilehash: d37ec8e17e62f58212a5f79f4d6b6aa75f57bf7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120261"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="c33ea-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime – metoda</span><span class="sxs-lookup"><span data-stu-id="c33ea-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="c33ea-103">Váže aktuální modul runtime pro všechna starší verze modulu CLR (Common Language Runtime) verze 2 – rozhodnutí zásad aktivace.</span><span class="sxs-lookup"><span data-stu-id="c33ea-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c33ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c33ea-104">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c33ea-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c33ea-105">Return Value</span></span>  
 <span data-ttu-id="c33ea-106">Tato metoda vrací následující konkrétní hodnoty HRESULT:</span><span class="sxs-lookup"><span data-stu-id="c33ea-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="c33ea-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c33ea-107">HRESULT</span></span>|<span data-ttu-id="c33ea-108">Popis</span><span class="sxs-lookup"><span data-stu-id="c33ea-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c33ea-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="c33ea-109">S_OK</span></span>|<span data-ttu-id="c33ea-110">Buď byla vazba úspěšná, nebo tento modul runtime již byl svázán jako starší modul runtime zásad aktivace CLR verze 2.</span><span class="sxs-lookup"><span data-stu-id="c33ea-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="c33ea-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="c33ea-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="c33ea-112">Jiný modul runtime již byl svázán se staršími zásadami aktivace CLR verze 2.</span><span class="sxs-lookup"><span data-stu-id="c33ea-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c33ea-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c33ea-113">Remarks</span></span>  
 <span data-ttu-id="c33ea-114">Pokud je aktuální modul runtime již svázán pro všechna starší rozhodnutí zásad aktivace CLR verze 2 (například pomocí atributu `useLegacyV2RuntimeActivationPolicy` v [prvku\<startup >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) v konfiguračním souboru), tato metoda nevrátí výsledek chyby. místo toho je výsledkem S_OK, stejně jako by to bylo, kdyby byla metoda úspěšně vázaná na starší Zásady aktivace.</span><span class="sxs-lookup"><span data-stu-id="c33ea-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c33ea-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c33ea-115">Requirements</span></span>  
 <span data-ttu-id="c33ea-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c33ea-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c33ea-117">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c33ea-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c33ea-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c33ea-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c33ea-119">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c33ea-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c33ea-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c33ea-120">See also</span></span>

- [<span data-ttu-id="c33ea-121">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c33ea-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c33ea-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c33ea-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="c33ea-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="c33ea-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="c33ea-124">\<> element Startup</span><span class="sxs-lookup"><span data-stu-id="c33ea-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
