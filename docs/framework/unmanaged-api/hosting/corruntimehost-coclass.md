---
title: "CorRuntimeHost – třída typu coclass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRuntimeHost
helpviewer_keywords: CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23bee1a79dfb54a696495fdb61a7ba9ba4b4c143
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost – třída typu coclass
Poskytuje rozhraní pro správu aplikací, které se spouštějí modul common language runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|[ICorConfiguration – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|Poskytuje metody pro konfiguraci common language runtime (CLR).|  
|[ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|Poskytuje metody, které umožní hostitele spuštění a zastavení modulu CLR explicitně, vytvořte a nakonfigurujte aplikační domény, pro přístup k výchozí doméně a chcete získat výčet všech domén, které jsou spuštěné v procesu.|  
|[IDebuggerInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|Poskytuje metody pro získání informací o stavu služby ladění.|  
|[IGCHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|Poskytuje metody pro získání informací o systém kolekce paměti a řízení některých aspektů uvolňování paměti.|  
|IValidator "–"|Poskytuje metody pro ověřování přenosné spustitelné bitové kopie a podrobné sestavy chyb ověřování.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.idl  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Třídy typu coclass pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
