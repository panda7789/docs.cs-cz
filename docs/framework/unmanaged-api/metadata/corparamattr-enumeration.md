---
title: CorParamAttr – výčet
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
ms.openlocfilehash: e8afcb972cab9757458c7032c3678d45c6418fac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007569"
---
# <a name="corparamattr-enumeration"></a>CorParamAttr – výčet
Obsahuje hodnoty, které popisují metadata parametru metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`pdIn`|Určuje, že se parametr předává do volání metody.|  
|`pdOut`|Určuje, že se parametr předává z návratové metody.|  
|`pdOptional`|Určuje, že parametr je nepovinný.|  
|`pdReservedMask`|Vyhrazeno pro interní použití modulem CLR (Common Language Runtime).|  
|`pdHasDefault`|Určuje, že parametr má výchozí hodnotu.|  
|`pdHasFieldMarshal`|Určuje, že má parametr zařazovací informace.|  
|`pdUnused`|Nepoužívá se.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
