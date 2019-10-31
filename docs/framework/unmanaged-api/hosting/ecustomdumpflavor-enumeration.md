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
ms.openlocfilehash: 057794fe524a0ee01f6f090ca7e11a4a4b523047
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124932"
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
|`DUMP_FLAVOR_Mini`|Určuje, že by se měl spustit výpis vlastní haldy jako s minimálním výpisem a zahrnout další data určená všemi instancemi [CustomDumpItem –](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) předanými do stejné metody.|  
|`DUMP_FLAVOR_NonHeapCLRState`|Určuje, že by měl být ve vlastním výpisu haldy shromažďována všechna data běhového stavu, která nebyla dynamicky přidělena.|  
  
## <a name="remarks"></a>Poznámky  
 Do metody [ICLRErrorReportingManager:: BeginCustomDump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) se předává parametr typu `ECustomDumpFlavor`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ECustomDumpItemKind – výčet](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [ICLRErrorReportingManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
