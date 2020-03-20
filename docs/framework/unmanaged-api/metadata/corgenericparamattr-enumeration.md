---
title: CorGenericParamAttr – výčet
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: bf0008ce9429671f0c156df4256bed0b2aaee184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176172"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr – výčet
Obsahuje hodnoty, <xref:System.Type> které popisují parametry pro obecné typy, jak je použito v volání [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`gpVarianceMask`|Odchylka parametrů platí pouze pro obecné parametry pro rozhraní a delegáty.|  
|`gpNonVariant`|Označuje nepřítomnost odchylky.|  
|`gpCovariant`|Označuje kovariance.|  
|`gpContravariant`|Označuje kontravariance.|  
|`gpSpecialConstraintMask`|Zvláštní omezení lze použít <xref:System.Type> na libovolný parametr.|  
|`gpNoSpecialConstraint`|Označuje, že na <xref:System.Type> parametr se nevztahuje žádné omezení.|  
|`gpReferenceTypeConstraint`|Označuje, <xref:System.Type> že parametr musí být typ odkazu.|  
|`gpNotNullableValueTypeConstraint`|Označuje, <xref:System.Type> že parametr musí být typ hodnoty, který nemůže být nulovou hodnotou.|  
|`gpDefaultConstructorConstraint`|Označuje, <xref:System.Type> že parametr musí mít výchozí veřejný konstruktor, který nepřebírá žádné parametry.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
