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
ms.openlocfilehash: 786ff6895383fc18dcfedb26fab344f80f04c1df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138209"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy – výčet
Obsahuje hodnoty, které nastavují zásady pro soubory programu pro čtení databáze programu (PDB).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eSymbolReadingAlways`|Určuje, že ladicí program by měl vždy číst soubory PDB.|  
|`eSymbolReadingFullTrustOnly`|Určuje, že ladicí program by měl číst pouze soubory PDB, které jsou přidruženy k sestavením s úplným vztahem důvěryhodnosti.|  
|`eSymbolReadingNever`|Určuje, že ladicí program by neměl nikdy číst soubory PDB.|  
  
## <a name="remarks"></a>Poznámky  
 `ESymbolReadingPolicy` výčet se používá s metodou [ICLRDebugManager:: SetSymbolReadingPolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
