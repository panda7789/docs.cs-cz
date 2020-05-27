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
ms.openlocfilehash: fec049297bfa12d86cb2a7f7950e84ae540832b1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007428"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder – výčet
Obsahuje hodnoty příznaků, které určují podmínky, za kterých by se měla generovat chybová zpráva při vygenerování metadat mimo pořadí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
|Člen|Description|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|Označuje výchozí chování, které negeneruje chybové zprávy.|  
|`MDErrorOutOfOrderNone`|Označuje, že by kompilátor neměl generovat chybové zprávy.|  
|`MDErrorOutOfOrderAll`|Určuje, že má kompilátor generovat chybovou zprávu, pokud je vygenerováno pole, vlastnost, událost, metoda nebo parametr.|  
|`MDMethodOutOfOrder`|Označuje, že by kompilátor měl generovat chybovou zprávu, pokud je vygenerována metoda mimo pořadí.|  
|`MDFieldOutOfOrder`|Označuje, že by kompilátor měl generovat chybovou zprávu, pokud je vygenerováno pole mimo pořadí.|  
|`MDParamOutOfOrder`|Určuje, že má kompilátor vygenerovat chybovou zprávu, pokud je vygenerována chyba v příkazu.|  
|`MDPropertyOutOfOrder`|Označuje, že by kompilátor měl generovat chybovou zprávu, pokud je vygenerována vlastnost mimo pořadí.|  
|`MDEventOutOfOrder`|Určuje, že má kompilátor generovat chybovou zprávu, pokud je vyvolána událost mimo pořadí.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
