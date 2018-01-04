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
ms.workload: dotnet
ms.openlocfilehash: 5552214f722cd7f9a56c2fce1e7c67de41d5bb1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime – metoda
Vytvoří vazbu aktuálního běhového modulu pro všechny starší verze common language runtime (CLR) verze 2 aktivace rozhodnutí o zásadách.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující hodnoty konkrétní HRESULT:  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Buď byla vazba úspěšná, nebo tento modul runtime byl již je svázaná jako starší verze 2 Aktivace zásady runtime verze CLR.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Jiný modul runtime byl již vázána na starší verzi zásad 2 aktivace verze CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud již je svázaná aktuálního běhového modulu pro všechny starší verze CLR verze 2 aktivace rozhodnutí o zásadách (například pomocí `useLegacyV2RuntimeActivationPolicy` atributu u [ \<spuštění > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) v konfiguračním souboru), tato metoda nevrátí chybného výsledku; Místo toho výsledkem je S_OK, stejně, jako by bylo, pokud metoda byl úspěšně navázán starší verze aktivace zásad.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRRuntimeInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [\<spuštění > elementu](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
