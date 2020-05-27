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
ms.openlocfilehash: f1836f26af99f91ab1765107573f6b067edd5e95
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007920"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets – výčet
Určuje prvky aplikace, na kterých je platný pro použití atributu.  
  
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
  
|Člen|Description|  
|------------|-----------------|  
|`catAssembly`|Atribut lze použít pro sestavení.|  
|`catModule`|Atribut lze použít pro přenos přenositelného spustitelného souboru (. dll nebo. exe).|  
|`catClass`|Atribut lze použít pro třídu.|  
|`catStruct`|Atribut lze použít pro strukturu; To znamená typ hodnoty.|  
|`catEnum`|Atribut lze použít pro výčet.|  
|`catConstructor`|Atribut lze použít pro konstruktor.|  
|`catMethod`|Atribut lze použít pro metodu.|  
|`catProperty`|Atribut lze použít pro vlastnost.|  
|`catField`|Atribut lze použít pro pole.|  
|`catEvent`|Atribut lze použít pro událost.|  
|`catInterface`|Atribut lze použít na rozhraní.|  
|`catParameter`|Atribut lze použít pro parametr.|  
|`catDelegate`|Atribut lze použít pro delegáta.|  
|`catGenericParameter`|Atribut lze použít pro obecný parametr.|  
|`catAll`|Atribut lze použít pro libovolný element aplikace.|  
|`catClassMembers`|Atribut lze použít pro člena třídy.|  
  
## <a name="remarks"></a>Poznámky  
 `CorAttributeTargets`Hodnoty výčtu lze kombinovat s bitovým nebo operaci pro získání preferované kombinace.  
  
 `CorAttributeTargets`Paralelně spravuje <xref:System.AttributeTargets?displayProperty=nameWithType> výčet.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
