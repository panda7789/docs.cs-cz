---
title: CorPropertyAttr – výčet
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
ms.openlocfilehash: 2d49a146a465210cea8466a75666ca3f800b090b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450138"
---
# <a name="corpropertyattr-enumeration"></a>CorPropertyAttr – výčet
Obsahuje hodnoty, které popisují metadata vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`prSpecialName`|Určuje, že vlastnost je zvláštní a že její název popisuje, jak.|  
|`prReservedMask`|Vyhrazeno pro interní použití modulem CLR (Common Language Runtime).|  
|`prRTSpecialName`|Určuje, že vnitřní rozhraní API pro Common Language Runtime metadata by měla kontrolovat kódování názvu vlastnosti.|  
|`prHasDefault`|Určuje, že vlastnost má výchozí hodnotu.|  
|`prUnused`|Nepoužívané.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
