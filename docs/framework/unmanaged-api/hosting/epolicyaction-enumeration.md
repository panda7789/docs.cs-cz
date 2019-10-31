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
ms.openlocfilehash: eaba6b2166a82cfe825ffb98db515e24d4656462
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138234"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction – výčet
Popisuje akce zásad, které může hostitel nastavit pro operace popsané v [EClrOperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) a chyby popsané v [EClrFailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`eAbortThread`|Určuje, že modul CLR (Common Language Runtime) by měl plynule přerušit vlákno. Bezproblémové přerušení zahrnuje pokusy o spuštění všech bloků `finally`, všechny `catch` bloky související s přerušením vlákna a finalizační metody.|  
|`eDisableRuntime`|Určuje, že CLR by měl vstoupit do zakázaného stavu. V ovlivněném procesu nelze provádět žádné další spravované kódy a vlákna jsou blokována při zadávání CLR.|  
|`eExitProcess`|Určuje, že se má modul CLR pokusit o řádné ukončení procesu, včetně spuštění finalizační metody a provádění operací vyčištění a protokolování.|  
|`eFastExitProcess`|Určuje, že modul CLR má okamžitě ukončit proces, aniž by musel spouštět finalizační metody nebo provádět operace vyčištění a protokolování. Oznámení je však odesláno do ladicího programu.|  
|`eNoAction`|Určuje, že by neměla být provedena žádná akce.|  
|`eRudeAbortThread`|Určuje, že modul CLR má provést přerušení hrubé vlákna. Jsou spuštěny pouze ty `catch` a `finally` bloky označené <xref:System.EnterpriseServices.MustRunInClientContextAttribute>.|  
|`eRudeExitProcess`|Určuje, že modul CLR má ukončit proces bez spuštění finalizační metody nebo operací protokolování.|  
|`eRudeUnloadAppDomain`|Určuje, že modul CLR má provést hrubé uvolnění <xref:System.AppDomain>. Jsou spuštěny pouze finalizační metody označené <xref:System.EnterpriseServices.MustRunInClientContextAttribute>. Podobně všechny podprocesy s tímto <xref:System.AppDomain> v zásobníku obdrží `ThreadAbortException`, ale spustí se pouze ty `catch` a `finally` bloky označené <xref:System.EnterpriseServices.MustRunInClientContextAttribute>.|  
|`eThrowException`|Určuje, že by měla být vyvolána výjimka, která je vhodná pro podmínku, jako je například nedostatek paměti, přetečení vyrovnávací paměti a tak dále.|  
|`eUnloadAppDomain`|Určuje, že se má <xref:System.AppDomain> uvolnit. Modul CLR se pokusí spustit finalizační metody.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel nastavuje akce zásad voláním metod rozhraní [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) . Informace o hrubé a bezproblémovém přerušení najdete v tématu výčet [EClrOperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
