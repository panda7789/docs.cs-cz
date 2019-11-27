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
ms.openlocfilehash: e4abf876681d5b04555c9f030a94b722874e326e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450279"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr – výčet
Obsahuje hodnoty, které popisují parametry <xref:System.Type> pro obecné typy, jak se používají v voláních [IMetaDataEmit2::D efinegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
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
|`gpVarianceMask`|Variance parametru se vztahuje pouze na Obecné parametry pro rozhraní a delegáty.|  
|`gpNonVariant`|Označuje absenci odchylky.|  
|`gpCovariant`|Označuje kovarianci.|  
|`gpContravariant`|Označuje kontravariance.|  
|`gpSpecialConstraintMask`|Speciální omezení se můžou vztahovat na libovolný <xref:System.Type> parametr.|  
|`gpNoSpecialConstraint`|Indikuje, že se pro parametr <xref:System.Type> neplatí žádné omezení.|  
|`gpReferenceTypeConstraint`|Označuje, že parametr <xref:System.Type> musí být typ odkazu.|  
|`gpNotNullableValueTypeConstraint`|Určuje, že parametr <xref:System.Type> musí být hodnotový typ, který nemůže být hodnota null.|  
|`gpDefaultConstructorConstraint`|Určuje, že parametr <xref:System.Type> musí mít výchozí veřejný konstruktor, který nepřijímá žádné parametry.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
