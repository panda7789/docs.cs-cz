---
title: ECustomDumpFlavor – výčet
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 9b4c1187945b4c243375a3096c3a8a3b22599aef
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616278"
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor – výčet
Obsahuje hodnoty, které určují, které položky se mají zahrnout do vlastní podmnožiny výpisu haldy při vytváření sestav chyb.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|Určuje, že by se měl spustit výpis vlastní haldy jako s minimálním výpisem a zahrnout další data určená všemi instancemi [CustomDumpItem –](customdumpitem-structure.md) předanými do stejné metody.|  
|`DUMP_FLAVOR_NonHeapCLRState`|Určuje, že by měl být ve vlastním výpisu haldy shromažďována všechna data běhového stavu, která nebyla dynamicky přidělena.|  
  
## <a name="remarks"></a>Poznámky  
 Parametr typu `ECustomDumpFlavor` je předán metodě [ICLRErrorReportingManager:: BeginCustomDump –](iclrerrorreportingmanager-begincustomdump-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ECustomDumpItemKind – výčet](ecustomdumpitemkind-enumeration.md)
- [ICLRErrorReportingManager – rozhraní](iclrerrorreportingmanager-interface.md)
- [Výčty hostování](hosting-enumerations.md)
