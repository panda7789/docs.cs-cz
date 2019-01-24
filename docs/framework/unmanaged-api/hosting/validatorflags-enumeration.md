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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e982fa7f6354f341ff4718440f345e282a1d20d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492219"
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags – výčet
Obsahuje hodnoty, které označují typ ověřování, která má být provedena ve volání [iclrvalidator::Validate –](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`VALIDATOR_CHECK_ILONLY`|Určuje, zda by měl být ověřen pouze Microsoft intermediate language (MSIL) ve spustitelném souboru.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Určuje, zda by měl být ověřen pouze formát spustitelného souboru.|  
|`VALIDATOR_EXTRA_VERBOSE`|Určuje, že všechny typy ověření, které provádí a reportovány.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Určuje, že by neměla ověří Formát spustitelného souboru.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Určuje, že chybových zpráv ověření by měl obsahovat řádky zdrojového kódu, které vyvolávají chyby ověření. Tato hodnota pole není platný v rozhraní .NET Framework verze 2.0.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** IValidator.idl, IValidator.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRErrorReportingManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
