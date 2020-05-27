---
title: COR_FIELD_OFFSET – struktura
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
ms.openlocfilehash: 70fb637cd1edf81be140b0e3306e3b0a483653a6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007985"
---
# <a name="cor_field_offset-structure"></a>COR_FIELD_OFFSET – struktura
Ukládá posun v rámci třídy zadaného pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`ridOfField`|`mdFieldDef`Token metadat, který představuje pole.|  
|`ulOffset`|Posun pole v rámci jeho třídy.|  
  
## <a name="remarks"></a>Poznámky  
 [IMetaDataImport:: GetClassLayout –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) a [IMetaDataEmit:: SetClassLayout –](imetadataemit-setclasslayout-method.md) metody přebírají parametr typu `COR_FIELD_OFFSET` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h, CorProf. idl  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro metadata](metadata-structures.md)
- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
