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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54d239c3091b29424b26fbab4cb4eb9152ff9ad9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442163"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets – výčet
Určuje prvky aplikace, na kterých je platná pro použití atributu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`catAssembly`|Atribut lze použít k sestavení.|  
|`catModule`|Atribut lze použít k přenosné modulu spustitelný soubor (.exe nebo .dll).|  
|`catClass`|Atribut lze použít na třídu.|  
|`catStruct`|Atribut lze použít pro strukturu; To znamená zadejte hodnotu.|  
|`catEnum`|Atribut lze použít k výčtu.|  
|`catConstructor`|Atribut lze použít k konstruktor.|  
|`catMethod`|Atribut může být použitý na metodu.|  
|`catProperty`|Atribut lze použít na vlastnost.|  
|`catField`|Atribut lze použít pro pole.|  
|`catEvent`|Atribut lze použít k události.|  
|`catInterface`|Atribut lze použít k rozhraní.|  
|`catParameter`|Atribut lze použít na parametr.|  
|`catDelegate`|Atribut lze použít s delegátem.|  
|`catGenericParameter`|Atribut lze použít pro obecný parametr.|  
|`catAll`|Atribut lze použít pro libovolný element, aplikace.|  
|`catClassMembers`|Atribut lze použít na člena třídy.|  
  
## <a name="remarks"></a>Poznámky  
 `CorAttributeTargets` Hodnot výčtu mohou být kombinovány s bitové operace OR k získání upřednostňované kombinace.  
  
 `CorAttributeTargets` Je paralelní spravovaný <xref:System.AttributeTargets?displayProperty=nameWithType> výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
