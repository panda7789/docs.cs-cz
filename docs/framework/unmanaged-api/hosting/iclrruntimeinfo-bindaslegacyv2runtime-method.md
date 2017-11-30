---
title: "ICLRRuntimeInfo::BindAsLegacyV2Runtime – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 229c5483c02357054f3d2821d8e024c78887e839
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="608bf-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime – metoda</span><span class="sxs-lookup"><span data-stu-id="608bf-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="608bf-103">Vytvoří vazbu aktuálního běhového modulu pro všechny starší verze common language runtime (CLR) verze 2 aktivace rozhodnutí o zásadách.</span><span class="sxs-lookup"><span data-stu-id="608bf-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="608bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="608bf-104">Syntax</span></span>  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="608bf-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="608bf-105">Return Value</span></span>  
 <span data-ttu-id="608bf-106">Tato metoda vrátí následující hodnoty konkrétní HRESULT:</span><span class="sxs-lookup"><span data-stu-id="608bf-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="608bf-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="608bf-107">HRESULT</span></span>|<span data-ttu-id="608bf-108">Popis</span><span class="sxs-lookup"><span data-stu-id="608bf-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="608bf-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="608bf-109">S_OK</span></span>|<span data-ttu-id="608bf-110">Buď byla vazba úspěšná, nebo tento modul runtime byl již je svázaná jako starší verze 2 Aktivace zásady runtime verze CLR.</span><span class="sxs-lookup"><span data-stu-id="608bf-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="608bf-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="608bf-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="608bf-112">Jiný modul runtime byl již vázána na starší verzi zásad 2 aktivace verze CLR.</span><span class="sxs-lookup"><span data-stu-id="608bf-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="608bf-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="608bf-113">Remarks</span></span>  
 <span data-ttu-id="608bf-114">Pokud již je svázaná aktuálního běhového modulu pro všechny starší verze CLR verze 2 aktivace rozhodnutí o zásadách (například pomocí `useLegacyV2RuntimeActivationPolicy` atributu u [ \<spuštění > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) v konfiguračním souboru), tato metoda nevrátí chybného výsledku; Místo toho výsledkem je S_OK, stejně, jako by bylo, pokud metoda byl úspěšně navázán starší verze aktivace zásad.</span><span class="sxs-lookup"><span data-stu-id="608bf-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="608bf-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="608bf-115">Requirements</span></span>  
 <span data-ttu-id="608bf-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="608bf-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="608bf-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="608bf-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="608bf-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="608bf-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="608bf-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="608bf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608bf-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="608bf-120">See Also</span></span>  
 [<span data-ttu-id="608bf-121">Iclrruntimeinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="608bf-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="608bf-122">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="608bf-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="608bf-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="608bf-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="608bf-124">\<spuštění > elementu</span><span class="sxs-lookup"><span data-stu-id="608bf-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
