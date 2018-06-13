---
title: ESymbolReadingPolicy – výčet
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28f6bdbc3e382f82b7fdd632b9fc8c4d422629c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429729"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy – výčet
Obsahuje hodnoty, které nastavit zásady pro soubory databáze (PDB) program pro čtení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eSymbolReadingAlways`|Určuje, že ladicí program vždy číst soubory PDB.|  
|`eSymbolReadingFullTrustOnly`|Určuje, že ladicí program by měl číst pouze soubory PDB, které jsou přidruženy sestavení plné důvěryhodnosti.|  
|`eSymbolReadingNever`|Určuje, že ladicího programu nikdy číst soubory PDB.|  
  
## <a name="remarks"></a>Poznámky  
 `ESymbolReadingPolicy` Výčtu se používá s [iclrdebugmanager::setsymbolreadingpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
