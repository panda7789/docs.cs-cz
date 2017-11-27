---
title: "CorGenericParamAttr – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGenericParamAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorGenericParamAttr
helpviewer_keywords: CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 95d7a6097766c8e2389e9828f54e81e37ffea454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr – výčet
Obsahuje hodnoty, které popisují <xref:System.Type> parametry pro obecné typy, jako používá volání [imetadataemit2::definegenericparam –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`gpVarianceMask`|Parametr odchylky platí pouze pro obecné parametry pro rozhraní a delegáti.|  
|`gpNonVariant`|Ukazuje na nepřítomnost odchylky.|  
|`gpCovariant`|Označuje kovariance.|  
|`gpContravariant`|Označuje kontravariance.|  
|`gpSpecialConstraintMask`|Můžete použít zvláštní omezení pro libovolné <xref:System.Type> parametr.|  
|`gpNoSpecialConstraint`|Označuje, že žádné omezení platí pro <xref:System.Type> parametr.|  
|`gpReferenceTypeConstraint`|Určuje, že <xref:System.Type> parametr musí být odkazového typu.|  
|`gpNotNullableValueTypeConstraint`|Určuje, že <xref:System.Type> parametr musí být typ hodnoty, který nemůže mít hodnotu null.|  
|`gpDefaultConstructorConstraint`|Určuje, že <xref:System.Type> parametr musí mít výchozí veřejný konstruktor, které nepřijímá žádné parametry.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
