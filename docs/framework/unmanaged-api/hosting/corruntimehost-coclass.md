---
title: CorRuntimeHost – třída typu coclass
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2143fc13db1757ac2fa8a9c5a43f104a0c519ca0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985826"
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
|[ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|Poskytuje metody, které umožní hostitele ke spouštění a zastavování modul common language runtime explicitně, vytvoření a konfigurace domény aplikace, pro přístup k výchozí doménu a chcete získat výčet všech doménách spuštěných v rámci procesu.|  
|[IDebuggerInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|Poskytuje metody pro získání informací o stavu služeb ladění.|  
|[IGCHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|Poskytuje metody pro získání informací o systému uvolňování paměti kolekce a pro řízení některé aspekty uvolňování paměti.|  
|IValidator "–"|Poskytuje metody pro ověřování přenosné spustitelné bitové kopie a generování podrobných sestav chyb ověřování.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.idl  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Třídy typu coclass pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
