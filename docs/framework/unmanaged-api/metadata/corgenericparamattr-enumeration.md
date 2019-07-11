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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 981829500e499be05a8de7c1ffb4683429a903e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781850"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr – výčet
Obsahuje hodnoty, které popisují <xref:System.Type> parametry pro obecné typy, jako používá ve volání [imetadataemit2::definegenericparam –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
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
|`gpVarianceMask`|Parametr variance platí pouze pro obecné parametry pro rozhraní a delegátů.|  
|`gpNonVariant`|Ukazuje na nepřítomnost variance.|  
|`gpCovariant`|Označuje kovariance.|  
|`gpContravariant`|Označuje kontravariance.|  
|`gpSpecialConstraintMask`|Zvláštní omezení můžete použít pro libovolné <xref:System.Type> parametru.|  
|`gpNoSpecialConstraint`|Označuje, že žádná omezení platí pro <xref:System.Type> parametru.|  
|`gpReferenceTypeConstraint`|Označuje, že <xref:System.Type> parametr musí být typ odkazu.|  
|`gpNotNullableValueTypeConstraint`|Označuje, že <xref:System.Type> parametr musí být typ hodnoty, který nemůže mít hodnotu null.|  
|`gpDefaultConstructorConstraint`|Označuje, že <xref:System.Type> parametr musí mít výchozí veřejný konstruktor, který nepřijímá žádné parametry.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
