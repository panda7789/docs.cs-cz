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
ms.openlocfilehash: fa2b5052a1d569487f0c6c72699ff9ab571beefc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504391"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure – výčet
V této části najdete popis sady selhání, pro které může hostitel nastavit akce zásad.  
  
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
  
|Člen|Description|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|Došlo k chybě při pokusu o přidělení prostředku (například vlákna, bloku paměti nebo zámku) v nekritické oblasti kódu.|  
|`FAIL_CriticalResource`|Došlo k chybě při pokusu o přidělení prostředku (například vlákna, bloku paměti nebo zámku) v kritické oblasti kódu.|  
|`FAIL_FatalRuntime`|Modul CLR (Common Language Runtime) již nemůže v procesu spustit spravovaný kód. Následně volání všech hostujících funkcí vrátí hodnotu HRESULT HOST_E_CLRNOTAVAILABLE.|  
|`FAIL_OrphanedLock`|Vlákno nedokázalo uvolnit zámek při návratu z <xref:System.AppDomain> objektu. Hostitel nemůže tuto chybu nastavit, aby mohla způsobit přerušení vlákna.|  
|`FAIL_StackOverflow`|Došlo k přetečení zásobníku.|  
|`FAIL_AccessViolation`|Byl proveden pokus o čtení nebo zápis chráněné paměti. Nepodporováno v .NET Framework 4.|  
|`FAIL_CodeContract`|Došlo k chybě kontraktu kódu. Viz [kontrakty kódu](../../debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Poznámky  
 V tématu metoda [ICLRPolicyManager:: SetActionOnFailure –](iclrpolicymanager-setactiononfailure-method.md) najdete seznam hodnot [EPolicyAction –](epolicyaction-enumeration.md) , které může hostitel použít k určení akcí zásad pro podmínky selhání. Další informace o kritických a nekritických oblastech kódu naleznete v tématu [EClrOperation –](eclroperation-enumeration.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRPolicyManager – rozhraní](iclrpolicymanager-interface.md)
- [SetActionOnFailure – metoda](iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager – rozhraní](ihostpolicymanager-interface.md)
- [Výčty hostování](hosting-enumerations.md)
