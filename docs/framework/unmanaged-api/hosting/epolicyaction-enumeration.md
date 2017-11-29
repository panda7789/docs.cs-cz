---
title: "EPolicyAction – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EPolicyAction
api_location: mscoree.dll
api_type: COM
f1_keywords: EPolicyAction
helpviewer_keywords: EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f2c3a4138adfa354de07bc6df4e51d7697598b67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction – výčet
Popisuje akce zásad, které jsou hostiteli můžete nastavit pro operace popsaného [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) a selhání popsaného [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eAbortThread`|Určuje, že modul CLR (CLR) by měl abort vlákno řádně. Řádné přerušení zahrnuje pokusí spustit všechny `finally` blokuje, všechny `catch` bloky související s vlákno přerušení a finalizační metody.|  
|`eDisableRuntime`|Určuje, že modulu CLR by měla zadat zakázaném stavu. Žádné další spravovaného kódu, mohou být provedeny v ovlivněných procesu a vláken jsou zablokované ve vstupu modulu CLR.|  
|`eExitProcess`|Určuje, že modulu CLR pokusit o řádné ukončení procesu, včetně spouštění finalizační metody a vyčištění a operace protokolování.|  
|`eFastExitProcess`|Určuje, že modulu CLR by měla opustí proces okamžitě, bez spuštění finalizační metody nebo vyčištění a operace protokolování. Nowever, oznámení se odesílá do ladicího programu.|  
|`eNoAction`|Určuje, že by měla být provedena žádná akce.|  
|`eRudeAbortThread`|Určuje, že modulu CLR by měla provádět přerušení článku neslušní vlákno. Pouze ty `catch` a `finally` bloky označené jako <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provedení.|  
|`eRudeExitProcess`|Určuje, že modulu CLR by měla opustí proces bez spuštění finalizační metody nebo protokolování operace.|  
|`eRudeUnloadAppDomain`|Určuje, že modulu CLR by měla provádět článku neslušní uvolnění z <xref:System.AppDomain>. Pouze finalizační metody označené jako <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provedení. Podobně všechna vlákna s tímto <xref:System.AppDomain> v jejich zásobníku přijímat `ThreadAbortException`, ale pouze ty `catch` a `finally` bloky označené jako <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provedení.|  
|`eThrowException`|Určuje, že by měl vyvolána výjimka příslušné podmínky, například z důvodu nedostatku paměti, přetečení vyrovnávací paměti a tak dále.|  
|`eUnloadAppDomain`|Určuje, že <xref:System.AppDomain> by měla být uvolněna. Modul CLR pokusí o spuštění finalizační metody.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel nastaví akce zásad voláním metod [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) rozhraní. Informace o článku neslušní a řádné přerušení najdete v tématu [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [Ihostpolicymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Výčty hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
