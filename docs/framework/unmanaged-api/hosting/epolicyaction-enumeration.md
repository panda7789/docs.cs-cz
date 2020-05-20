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
ms.openlocfilehash: 8788d6e2220778a3f0926d5ed3dd59142487bcca
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616187"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction – výčet
Popisuje akce zásad, které může hostitel nastavit pro operace popsané v [EClrOperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) a chyby popsané v [EClrFailure –](eclrfailure-enumeration.md).  
  
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
|`eAbortThread`|Určuje, že modul CLR (Common Language Runtime) by měl plynule přerušit vlákno. Bezproblémové přerušení zahrnuje pokusy o spuštění všech `finally` bloků, všechny `catch` bloky související s přerušením vlákna a finalizační metody.|  
|`eDisableRuntime`|Určuje, že CLR by měl vstoupit do zakázaného stavu. V ovlivněném procesu nelze provádět žádné další spravované kódy a vlákna jsou blokována při zadávání CLR.|  
|`eExitProcess`|Určuje, že se má modul CLR pokusit o řádné ukončení procesu, včetně spuštění finalizační metody a provádění operací vyčištění a protokolování.|  
|`eFastExitProcess`|Určuje, že modul CLR má okamžitě ukončit proces, aniž by musel spouštět finalizační metody nebo provádět operace vyčištění a protokolování. Oznámení je však odesláno do ladicího programu.|  
|`eNoAction`|Určuje, že by neměla být provedena žádná akce.|  
|`eRudeAbortThread`|Určuje, že modul CLR má provést přerušení hrubé vlákna. `catch` `finally` Jsou spuštěny pouze ty a bloky označené pomocí <xref:System.EnterpriseServices.MustRunInClientContextAttribute> .|  
|`eRudeExitProcess`|Určuje, že modul CLR má ukončit proces bez spuštění finalizační metody nebo operací protokolování.|  
|`eRudeUnloadAppDomain`|Určuje, že modul CLR má provést hrubé uvolnění <xref:System.AppDomain> . Jsou spuštěny pouze finalizační metody označené pomocí <xref:System.EnterpriseServices.MustRunInClientContextAttribute> . Podobně všechny podprocesy s tímto <xref:System.AppDomain> objektem v zásobníku obdrží `ThreadAbortException` , ale pouze ty `catch` a `finally` bloky označené pomocí <xref:System.EnterpriseServices.MustRunInClientContextAttribute> jsou spuštěny.|  
|`eThrowException`|Určuje, že by měla být vyvolána výjimka, která je vhodná pro podmínku, jako je například nedostatek paměti, přetečení vyrovnávací paměti a tak dále.|  
|`eUnloadAppDomain`|Určuje, že <xref:System.AppDomain> by mělo být uvolněno. Modul CLR se pokusí spustit finalizační metody.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel nastavuje akce zásad voláním metod rozhraní [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) . Informace o hrubé a bezproblémovém přerušení najdete v tématu výčet [EClrOperation –](eclroperation-enumeration.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [EClrFailure – výčet](eclrfailure-enumeration.md)
- [ICLRPolicyManager – rozhraní](iclrpolicymanager-interface.md)
- [IHostPolicyManager – rozhraní](ihostpolicymanager-interface.md)
- [Výčty hostování](hosting-enumerations.md)
