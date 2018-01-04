---
title: "ICLRMetaHostPolicy – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHostPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHostPolicy
helpviewer_keywords: ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type: apiref
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd9b8d6aef2289833a0bd192b838e6f70ea8c0ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy – rozhraní
Poskytuje [getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodu, která vrací ukazatel na společné rozhraní language runtime (CLR) na základě zásad kritérií, spravované sestavení, verzi a konfiguračnímu souboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetRequestedRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|Poskytuje upřednostňované CLR rozhraní na základě zásad kritérií, spravované sestavení, verzi a konfiguračnímu souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Odkaz na tohoto rozhraní můžete získat voláním [clrcreateinstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fungovat, jak je znázorněno v následujícím kódu:  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  Toto rozhraní není ve skutečnosti načíst nebo aktivace CLR, ale jednoduše vrátí upřednostňovaný verze CLR, závisí na dostupných verzí, které jsou nainstalovány nebo načíst.  
  
 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Hostující rozhraní API konsoliduje zásady tak, aby hostiteli s potřeb může používat základní funkce aniž by docházelo k neúmyslnému postihy. Například mnoho exporty MSCorEE.dll vytvoří vazbu k určité CLR, i když metody nemusejí být nutné logicky ho. [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) výčtu poskytuje vazby zásady, které jsou společné pro většinu hostitelů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
