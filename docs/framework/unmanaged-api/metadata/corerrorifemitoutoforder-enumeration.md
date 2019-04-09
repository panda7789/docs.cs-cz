---
title: CorErrorIfEmitOutOfOrder – výčet
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 628ca1b555d80319312450d784981cfed1bda947
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160443"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder – výčet
Obsahuje příznak hodnoty, které určují podmínky, za kterých by měl být vygenerován chybovou zprávu, když metadat je vygenerován mimo pořadí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|Určuje výchozí chování, které nejsou generovány chybové zprávy.|  
|`MDErrorOutOfOrderNone`|Označuje, že kompilátor by neměl generovat chybové zprávy.|  
|`MDErrorOutOfOrderAll`|Označuje, že by měl kompilátor generovat chybovou zprávu, když pole, vlastnosti, události, metody nebo parametr je vygenerován mimo pořadí.|  
|`MDMethodOutOfOrder`|Označuje, že kompilátor by měl generovat chybovou zprávu, když metoda je vygenerován mimo pořadí.|  
|`MDFieldOutOfOrder`|Označuje, že by měl kompilátor generovat chybovou zprávu, když pole je vygenerován mimo pořadí.|  
|`MDParamOutOfOrder`|Označuje, že by měl kompilátor generovat chybovou zprávu, pokud parametr je vygenerován mimo pořadí.|  
|`MDPropertyOutOfOrder`|Označuje, že by měl kompilátor generovat chybovou zprávu, když vlastnost je vygenerován mimo pořadí.|  
|`MDEventOutOfOrder`|Označuje, že by měl kompilátor generovat chybovou zprávu při události je vygenerován mimo pořadí.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
