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
ms.openlocfilehash: 57460ba30a8ce974b5ca89f76796c4dcf49ffecf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443583"
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
  
|Člen|Popis|  
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
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
