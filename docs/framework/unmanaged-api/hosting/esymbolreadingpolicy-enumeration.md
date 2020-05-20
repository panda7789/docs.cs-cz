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
ms.openlocfilehash: 5c3d1d0ebc56ee93c950afb4f015c8e10ec6a0f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616172"
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
 `ESymbolReadingPolicy`Výčet se používá s metodou [ICLRDebugManager:: SetSymbolReadingPolicy –](iclrdebugmanager-setsymbolreadingpolicy-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty hostování](hosting-enumerations.md)
