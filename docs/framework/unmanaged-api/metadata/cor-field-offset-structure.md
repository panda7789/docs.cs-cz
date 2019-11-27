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
ms.openlocfilehash: 646952d5cd55b74081a0ba6171a6eee6b0138512
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443960"
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
  
|Člen|Popis|  
|------------|-----------------|  
|`ridOfField`|Token metadat `mdFieldDef`, který představuje pole.|  
|`ulOffset`|Posun pole v rámci jeho třídy.|  
  
## <a name="remarks"></a>Poznámky  
 [IMetaDataImport:: GetClassLayout –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) a [IMetaDataEmit:: SetClassLayout –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) metody přebírají parametr typu `COR_FIELD_OFFSET`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h, CorProf. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
