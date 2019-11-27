---
title: CorSetENC – výčet
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: 39f72e670ddc700c257f50f6bad6fab702ec21b6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432770"
---
# <a name="corsetenc-enumeration"></a>CorSetENC – výčet
Obsahuje hodnoty, které slouží k ovlivnění chování během generování metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a>Members  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDSetENCOn`|Zastaralé.|  
|`MDSetENCOff`|Zastaralé.|  
|`MDUpdateENC`|Označuje, že je možné aktualizovat metadata, a tokeny nelze přesunout.|  
|`MDUpdateFull`|Označuje, že tokeny lze během aktualizací přesunout.|  
|`MDUpdateExtension`|Označuje, že aktualizace mohou sestávat pouze z dodatků. Tokeny nejde přesunout.|  
|`MDUpdateIncremental`|Indikuje, že je kompilace přírůstková.|  
|`MDUpdateDelta`|Indikuje, že se mají ukládat jenom změněná metadata.|  
|`MDUpdateMask`|Zahrnuje `MDUpdateENC`, `MDUpdateFull` a `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
