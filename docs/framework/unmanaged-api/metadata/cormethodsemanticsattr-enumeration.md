---
title: CorMethodSemanticsAttr – výčet
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f888c39160e52e550d07f58b9c5bcd11fd625658
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564078"
---
# <a name="cormethodsemanticsattr-enumeration"></a>CorMethodSemanticsAttr – výčet
Obsahuje hodnoty, které popisují vztah mezi metodu a přidružené vlastnosti nebo události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`msSetter`|Určuje, že metoda je `set` přistupujícího objektu vlastnosti.|  
|`msGetter`|Určuje, že metoda je `get` přistupujícího objektu vlastnosti.|  
|`msOther`|Určuje, že tato metoda má vztah k vlastnosti nebo události než ty, které jsou zde definovány.|  
|`msAddOn`|Určuje, že metoda přidá metody obslužné rutiny události.|  
|`msRemoveOn`|Určuje, že metoda odebere metody obslužné rutiny události.|  
|`msFire`|Určuje, že metoda vyvolá událost.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
