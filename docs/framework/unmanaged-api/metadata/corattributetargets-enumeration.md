---
title: CorAttributeTargets – výčet
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: 51741aa3a6d965c1e9743081628d8ad62e8fb04e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176198"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets – výčet
Určuje prvky aplikace, na kterých je platný použít atribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =
        catAssembly | catModule | catClass | catStruct |
        catEnum | catConstructor | catMethod | catProperty |
        catField | catEvent | catInterface | catParameter |
        catDelegate | catGenericParameter,  
  
    catClassMembers        =
        catClass | catStruct | catEnum | catConstructor |
        catMethod | catProperty | catField | catEvent |
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`catAssembly`|Atribut lze použít pro sestavení.|  
|`catModule`|Atribut lze použít u přenosného spustitelného souboru (.dll nebo .exe) modulu.|  
|`catClass`|Atribut lze použít pro třídu.|  
|`catStruct`|Atribut lze použít na strukturu; to znamená typ hodnoty.|  
|`catEnum`|Atribut lze použít pro výčet.|  
|`catConstructor`|Atribut lze použít na konstruktoru.|  
|`catMethod`|Atribut lze použít na metodu.|  
|`catProperty`|Atribut lze použít na vlastnost.|  
|`catField`|Atribut lze použít pro pole.|  
|`catEvent`|Atribut lze použít na událost.|  
|`catInterface`|Atribut lze použít na rozhraní.|  
|`catParameter`|Atribut lze použít na parametr.|  
|`catDelegate`|Atribut lze použít pro delegáta.|  
|`catGenericParameter`|Atribut lze použít na obecný parametr.|  
|`catAll`|Atribut lze použít pro libovolný prvek aplikace.|  
|`catClassMembers`|Atribut lze použít na člena třídy.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty `CorAttributeTargets` výčtu lze kombinovat s bitovou operací OR, abyste získali upřednostňovanou kombinaci.  
  
 Paralely `CorAttributeTargets` spravované <xref:System.AttributeTargets?displayProperty=nameWithType> výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
