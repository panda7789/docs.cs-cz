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
ms.openlocfilehash: 45b6b8593331801dd237d0a730afbd5a6a714bbf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774178"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy – výčet
Obsahuje hodnoty, které nastavení zásad pro čtení souborů databáze (PDB) programu.  
  
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
|`eSymbolReadingFullTrustOnly`|Určuje, že by měl ladicí program číst pouze soubory PDB, které jsou spojeny s plnou důvěryhodností sestavení.|  
|`eSymbolReadingNever`|Určuje, že ladicí program nikdy číst soubory PDB.|  
  
## <a name="remarks"></a>Poznámky  
 `ESymbolReadingPolicy` Výčtu se používá s [iclrdebugmanager::setsymbolreadingpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
