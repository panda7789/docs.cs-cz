---
title: EClrFailure – výčet
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef4e12015adc3d6e67ad9c8ba8b152cd775b85e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431926"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure – výčet
Popisuje sadu chyb, pro které hostitele může nastavit zásady akce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|Došlo k chybě při pokusu o přidělení prostředků (například vlákno, blok paměti nebo zámek) v oblasti nekritické kódu.|  
|`FAIL_CriticalResource`|Došlo k chybě při pokusu o přidělení prostředků (například vlákno, blok paměti nebo zámek) v oblasti kritické kódu.|  
|`FAIL_FatalRuntime`|Modul CLR (CLR) je již možné spouštět spravovaného kódu v procesu. Volání jakékoli hostování funkce vrací od nynějška, má hodnotu HRESULT HOST_E_CLRNOTAVAILABLE.|  
|`FAIL_OrphanedLock`|Vlákno se nepodařilo uvolnit zámek při vrácení z <xref:System.AppDomain> objektu. Hostitele nelze nastavit této chyby a způsobit, že vlákno k přerušení.|  
|`FAIL_StackOverflow`|Došlo k přetečení zásobníku.|  
|`FAIL_AccessViolation`|Došlo k pokusu o čtení nebo zápisu chráněné paměti. Není podporováno v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].|  
|`FAIL_CodeContract`|Kontrakt kódu došlo k chybě. V tématu [Code kontrakty](../../../../docs/framework/debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Poznámky  
 Najdete v článku [iclrpolicymanager::setactiononfailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metoda seznam [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, které jsou hostiteli můžete použít k určení akce zásad podmínky při selhání. Další informace o oblastech kritické a nekritické kódu najdete v tématu [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [SetActionOnFailure – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)  
 [IHostPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
