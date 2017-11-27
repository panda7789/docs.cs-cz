---
title: "CorSetENC – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSetENC
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSetENC
helpviewer_keywords: CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85a909d92be8bfdb9ada709b54cf252183ff411e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
