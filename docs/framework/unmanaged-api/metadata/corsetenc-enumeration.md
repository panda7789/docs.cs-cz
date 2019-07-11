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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2796be32154275387da891683cc5053095f534af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772323"
---
# <a name="corsetenc-enumeration"></a>CorSetENC – výčet
Obsahuje hodnoty použité k ovlivnění chování při generování metadat.  
  
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
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDSetENCOn`|Zastaralé.|  
|`MDSetENCOff`|Zastaralé.|  
|`MDUpdateENC`|Označuje, že je možné aktualizovat metadata, tokeny nelze přesunout.|  
|`MDUpdateFull`|Označuje, že tokeny lze přesunout během aktualizace.|  
|`MDUpdateExtension`|Označuje, že aktualizace může být tvořen pouze doplňky. Tokeny nelze přesunout.|  
|`MDUpdateIncremental`|Označuje, že je přírůstková kompilace.|  
|`MDUpdateDelta`|Označuje, že by se měla uložit tato metadata pouze změněné.|  
|`MDUpdateMask`|Zahrnuje `MDUpdateENC`, `MDUpdateFull` a `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
