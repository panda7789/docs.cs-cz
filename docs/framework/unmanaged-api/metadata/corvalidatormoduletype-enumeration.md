---
title: CorValidatorModuleType – výčet
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97e9ae5a7c35b4f9b6e2b4ca7e754b5b7480dfa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444136"
---
# <a name="corvalidatormoduletype-enumeration"></a>CorValidatorModuleType – výčet
Určuje typ modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|Modul je neplatného typu.|  
|`ValidatorModuleTypeMin`|Minimální hodnota `CorValidatorModuleType` výčtu.|  
|`ValidatorModuleTypePE`|Modul je soubor přenosné spustitelný soubor (PE).|  
|`ValidatorModuleTypeObj`|Modul je soubor .obj.|  
|`ValidatorModuleTypeEnc`|Modul je relaci upravit a pokračovat ladicí program.|  
|`ValidatorModuleTypeIncr`|Modul je ten, který přírůstkově sestaven.|  
|`ValidatorModuleTypeMax`|Maximální hodnota, která `CorValidatorModuleType` výčtu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
