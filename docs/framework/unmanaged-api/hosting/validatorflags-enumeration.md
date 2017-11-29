---
title: "ValidatorFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ValidatorFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ValidatorFlags
helpviewer_keywords: ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f283beb79ec47454185800bd772904c3c696c7c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags – výčet
Obsahuje hodnoty, které označují typ ověření, která má být provedena ve volání [iclrvalidator::Validate –](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) metoda.  
  
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
|`VALIDATOR_CHECK_ILONLY`|Určuje, zda má být ověřen pouze Microsoft (MSIL intermediate language) ve spustitelném souboru.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Určuje, zda má být ověřen pouze formát spustitelného souboru.|  
|`VALIDATOR_EXTRA_VERBOSE`|Určuje, že všechny typy ověření, které by měl být provést a ohlášeny.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Určuje, že formát spustitelného souboru by neměl ověřit.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Určuje, že chybových zpráv ověření by měl obsahovat řádky zdrojového kódu, které vyvolat chyby ověření. Tato hodnota pole není platný v rozhraní .NET Framework verze 2.0.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** IValidator.idl, IValidator.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iclrerrorreportingmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [Výčty hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
