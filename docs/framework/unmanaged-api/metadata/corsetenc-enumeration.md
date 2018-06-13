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
ms.openlocfilehash: 3e09bf424a41445f7e36397775d1578cdf4e7e75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442784"
---
# <a name="corsetenc-enumeration"></a>CorSetENC – výčet
Obsahuje hodnoty používané k ovlivnění chování při generování metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`MDUpdateENC`|Označuje, že můžete aktualizovat metadata, nelze přesunout tokeny.|  
|`MDUpdateFull`|Označuje, že tokeny je možné přesouvat během aktualizace.|  
|`MDUpdateExtension`|Označuje, že aktualizace se může skládat pouze z dodatky. Tokeny nelze přesunout.|  
|`MDUpdateIncremental`|Označuje, že je přírůstkové kompilace.|  
|`MDUpdateDelta`|Označuje, že má být uložen aby pouze změněné metadata.|  
|`MDUpdateMask`|Zahrnuje `MDUpdateENC`, `MDUpdateFull` a `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
