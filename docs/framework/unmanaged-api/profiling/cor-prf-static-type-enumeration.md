---
title: COR_PRF_STATIC_TYPE – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 753c3b38187dd69593dcb0520acef9ce4b137039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751907"
---
# <a name="corprfstatictype-enumeration"></a>COR_PRF_STATIC_TYPE – výčet
Určuje, jestli je statická pole, a pokud ano, statické kvality platí pro pole. Tyto hodnoty lze spojovat pomocí bitová operace OR k označení, že pole má několik různých statických kvality.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|Pole není statická.|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|Toto pole je statická domény aplikace.|  
|`COR_PRF_FIELD_THREAD_STATIC`|Toto pole je statická na úrovni vlákna.|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|Toto pole je statického kontextu.|  
|`COR_PRF_FIELD_RVA_STATIC`|Pole je relativní virtuální adresu (RVA) – statické.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
