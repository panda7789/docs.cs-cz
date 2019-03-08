---
title: EPolicyAction – výčet
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa8589b3f27ba97d32e77dbfecb190edc69dbc18
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677328"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction – výčet
Popisuje akce zásad hostitele můžete nastavit pro operace popsal [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) a selhání popsal [eclrfailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
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
|`eAbortThread`|Určuje, že modul CLR (CLR) by měl přerušit vlákno bez výpadku. Bezproblémové přerušení zahrnuje pokusy o spuštění všech `finally` blokuje všechny `catch` bloky týkající se přeruší vlákna a finalizační metody.|  
|`eDisableRuntime`|Určuje, že modul CLR by měla zadat zakázaném stavu. Žádné další spravovaného kódu mohou být provedeny v procesu ovlivněná a jsou blokovaná vlákna vstupují do platformy CLR.|  
|`eExitProcess`|Určuje, že modul CLR pokusit o řádné ukončení procesu, včetně spuštění finalizační metody a vyčištění a operace protokolování.|  
|`eFastExitProcess`|Určuje, že modul CLR by měla opustí proces okamžitě, bez spuštění finalizační metody nebo vyčištění a operace protokolování. Nicméně je oznámení odeslané ladicímu programu.|  
|`eNoAction`|Určuje, že by měla být provedena žádná akce.|  
|`eRudeAbortThread`|Určuje, že modul CLR by měl provádět přerušení článku neslušní vlákna. Pouze ty `catch` a `finally` bloky označené <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provádějí.|  
|`eRudeExitProcess`|Určuje, že modul CLR má ukončit proces bez spuštění finalizační metody nebo protokolování operations.|  
|`eRudeUnloadAppDomain`|Určuje, že modul CLR by měl provádět článku neslušní uvolnění <xref:System.AppDomain>. Pouze finalizační metody označené <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provádějí. Podobně platí, všechna vlákna s tímto <xref:System.AppDomain> v jejich zásobníku přijímat `ThreadAbortException`, ale jenom na ty `catch` a `finally` bloky označené <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provádějí.|  
|`eThrowException`|Určuje, že by měl vyvolána výjimka pro podmínku, třeba na více instancí z důvodu nedostatku paměti, přetečení vyrovnávací paměti a tak dále.|  
|`eUnloadAppDomain`|Určuje, že <xref:System.AppDomain> by měla být uvolněna. Modul CLR se pokusí o spuštění finalizační metody.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel nastaví akce zásad voláním metod [iclrpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) rozhraní. Informace o článku neslušní a bezproblémové přeruší, najdete v článku [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
