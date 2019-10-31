---
title: ValidatorFlags – výčet
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
ms.openlocfilehash: 61aafb8dc99bb908fc603945ff6ea74054f812c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141416"
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags – výčet
Obsahuje hodnoty, které určují typ ověřování, který by měl být proveden při volání metody [ICLRValidator:: Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|Určuje, že by měl být ověřený pouze kód jazyka MSIL (Microsoft Intermediate Language) ve spustitelném souboru.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Určuje, že by měl být ověřený jenom formát spustitelného souboru.|  
|`VALIDATOR_EXTRA_VERBOSE`|Určuje, že by měly být provedeny a hlášeny všechny typy ověřování.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Určuje, že by se neměl ověřit formát spustitelného souboru.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Určuje, že zprávy o chybách ověřování by měly zahrnovat řádky zdrojového kódu, které vyvolávají chyby ověřování. Hodnota tohoto pole není platná v .NET Framework verze 2,0.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** IValidator. idl, IValidator. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRErrorReportingManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
