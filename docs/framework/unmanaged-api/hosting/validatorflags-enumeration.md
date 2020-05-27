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
ms.openlocfilehash: d5eb225241f597baf7a0a5584f4aaf8bf8411ea2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009467"
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags – výčet
Obsahuje hodnoty, které určují typ ověřování, který by měl být proveden při volání metody [ICLRValidator:: Validate](iclrvalidator-validate-method.md) .  
  
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
  
|Člen|Description|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|Určuje, že by měl být ověřený pouze kód jazyka MSIL (Microsoft Intermediate Language) ve spustitelném souboru.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Určuje, že by měl být ověřený jenom formát spustitelného souboru.|  
|`VALIDATOR_EXTRA_VERBOSE`|Určuje, že by měly být provedeny a hlášeny všechny typy ověřování.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Určuje, že by se neměl ověřit formát spustitelného souboru.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Určuje, že zprávy o chybách ověřování by měly zahrnovat řádky zdrojového kódu, které vyvolávají chyby ověřování. Hodnota tohoto pole není platná v .NET Framework verze 2,0.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** IValidator. idl, IValidator. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRErrorReportingManager – rozhraní](iclrerrorreportingmanager-interface.md)
- [Výčty hostování](hosting-enumerations.md)
