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
ms.openlocfilehash: ea84b742c901ba58a3bb730f1f5033a0d90610ce
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007374"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr – výčet
Obsahuje hodnoty, které popisují <xref:System.Type> parametry pro obecné typy, jak se používají v voláních [IMetaDataEmit2::D efinegenericparam](imetadataemit2-definegenericparam-method.md).  
  
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
  
|Člen|Description|  
|------------|-----------------|  
|`gpVarianceMask`|Variance parametru se vztahuje pouze na Obecné parametry pro rozhraní a delegáty.|  
|`gpNonVariant`|Označuje absenci odchylky.|  
|`gpCovariant`|Označuje kovarianci.|  
|`gpContravariant`|Označuje kontravariance.|  
|`gpSpecialConstraintMask`|Speciální omezení se můžou vztahovat na libovolný <xref:System.Type> parametr.|  
|`gpNoSpecialConstraint`|Označuje, že se pro parametr neplatí žádné omezení <xref:System.Type> .|  
|`gpReferenceTypeConstraint`|Označuje, že <xref:System.Type> parametr musí být typ odkazu.|  
|`gpNotNullableValueTypeConstraint`|Označuje, že <xref:System.Type> parametr musí být typ hodnoty, který nemůže být hodnota null.|  
|`gpDefaultConstructorConstraint`|Označuje, že <xref:System.Type> parametr musí mít výchozí veřejný konstruktor, který nepřijímá žádné parametry.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
