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
ms.openlocfilehash: 416c7787e7e68ea0c6864091e92d92fed1a60bf4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650116"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets – výčet
Určuje prvky aplikace, na kterých je platný pro použití atributu.  
  
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
|`catModule`|Atribut lze použít pro přenosný spustitelný soubor modulu (.dll nebo .exe).|  
|`catClass`|Atribut lze použít na třídu.|  
|`catStruct`|Atribut lze použít pro struktury; To znamená zadejte hodnotu.|  
|`catEnum`|Atribut lze použít pro výčet.|  
|`catConstructor`|Atribut lze použít pro konstruktor.|  
|`catMethod`|Atribut lze použít pro metodu.|  
|`catProperty`|Atribut lze použít pro vlastnost.|  
|`catField`|Atribut lze použít pro pole.|  
|`catEvent`|Atribut lze použít k události.|  
|`catInterface`|Atribut lze použít pro rozhraní.|  
|`catParameter`|Atribut lze použít pro parametr.|  
|`catDelegate`|Atribut lze použít pro delegáta.|  
|`catGenericParameter`|Atribut lze použít pro obecný parametr.|  
|`catAll`|Atribut lze použít k libovolnému aplikaci prvku.|  
|`catClassMembers`|Atribut lze použít pro člen třídy.|  
  
## <a name="remarks"></a>Poznámky  
 `CorAttributeTargets` Hodnoty výčtu lze kombinovat s bitová operace OR zobrazíte upřednostňované kombinaci.  
  
 `CorAttributeTargets` Parallels spravovanou <xref:System.AttributeTargets?displayProperty=nameWithType> výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
