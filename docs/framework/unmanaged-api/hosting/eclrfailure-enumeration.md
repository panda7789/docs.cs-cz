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
ms.openlocfilehash: 5f3e39d94996f14f1ae6593b9adaa5db3ef674c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769663"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure – výčet
Popisuje sadu selhání, pro které hostitele může nastavit akce zásad.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`FAIL_NonCriticalResource`|Došlo k chybě při pokusu o přidělení prostředků (například vlákně, blok paměti nebo zámek) v méně důležité oblasti kódu.|  
|`FAIL_CriticalResource`|Došlo k chybě při pokusu o přidělení prostředků (například vlákně, blok paměti nebo zámek) v oblasti, kritický kód.|  
|`FAIL_FatalRuntime`|Modul CLR (CLR) již není možné spouštět spravovaný kód v procesu. Od nynějška volání jakékoli hostitelské funkce vrací hodnotu HRESULT HOST_E_CLRNOTAVAILABLE.|  
|`FAIL_OrphanedLock`|Vlákno se nepodařilo uvolnit zámek při návratu z <xref:System.AppDomain> objektu. Hostitele nelze nastavit této chyby a způsobit, že vlákno pro přerušení.|  
|`FAIL_StackOverflow`|Došlo k přetečení zásobníku.|  
|`FAIL_AccessViolation`|Došlo pokusu o čtení nebo zápis v chráněné paměti. Není podporován v rozhraní .NET Framework 4.|  
|`FAIL_CodeContract`|Došlo k chybě kontraktu kódu. Zobrazit [kontrakty kódu](../../../../docs/framework/debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Poznámky  
 Zobrazit [iclrpolicymanager::setactiononfailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metoda seznam [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty hostitele můžete použít k určení akce zásad pro podmínky při selhání. Další informace o oblastech kritické a nekritické kód, naleznete v tématu [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [SetActionOnFailure – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
