---
title: CorElementType – výčet 1
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5112c3c8d5fef6efada4bffdfa575716503515e6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787711"
---
# <a name="corelementtype-enumeration1"></a>CorElementType – výčet 1
Určuje modul common language runtime <xref:System.Type>, modifikátor typu nebo informace o typu v signatuře typu metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorElementType {  
    ELEMENT_TYPE_END            = 0x0,  
    ELEMENT_TYPE_VOID           = 0x1,  
    ELEMENT_TYPE_BOOLEAN        = 0x2,  
    ELEMENT_TYPE_CHAR           = 0x3,  
    ELEMENT_TYPE_I1             = 0x4,  
    ELEMENT_TYPE_U1             = 0x5,  
    ELEMENT_TYPE_I2             = 0x6,  
    ELEMENT_TYPE_U2             = 0x7,  
    ELEMENT_TYPE_I4             = 0x8,  
    ELEMENT_TYPE_U4             = 0x9,  
    ELEMENT_TYPE_I8             = 0xa,  
    ELEMENT_TYPE_U8             = 0xb,  
    ELEMENT_TYPE_R4             = 0xc,  
    ELEMENT_TYPE_R8             = 0xd,  
    ELEMENT_TYPE_STRING         = 0xe,  
  
    ELEMENT_TYPE_PTR            = 0xf,  
    ELEMENT_TYPE_BYREF          = 0x10,  
  
    ELEMENT_TYPE_VALUETYPE      = 0x11,  
    ELEMENT_TYPE_CLASS          = 0x12,  
    ELEMENT_TYPE_VAR            = 0x13,  
    ELEMENT_TYPE_ARRAY          = 0x14,  
    ELEMENT_TYPE_GENERICINST    = 0x15,  
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,  
  
    ELEMENT_TYPE_I              = 0x18,  
    ELEMENT_TYPE_U              = 0x19,  
    ELEMENT_TYPE_FNPTR          = 0x1B,  
    ELEMENT_TYPE_OBJECT         = 0x1C,  
    ELEMENT_TYPE_SZARRAY        = 0x1D,  
    ELEMENT_TYPE_MVAR           = 0x1e,  
  
    ELEMENT_TYPE_CMOD_REQD      = 0x1F,  
    ELEMENT_TYPE_CMOD_OPT       = 0x20,  
  
    ELEMENT_TYPE_INTERNAL       = 0x21,  
    ELEMENT_TYPE_MAX            = 0x22,  
  
    ELEMENT_TYPE_MODIFIER       = 0x40,  
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,  
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER  
  
} CorElementType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`ELEMENT_TYPE_END`|Interně.|  
|`ELEMENT_TYPE_VOID`|Typ void.|  
|`ELEMENT_TYPE_BOOLEAN`|Typ Boolean|  
|`ELEMENT_TYPE_CHAR`|Typ znaku.|  
|`ELEMENT_TYPE_I1`|1bajtový celé číslo se znaménkem.|  
|`ELEMENT_TYPE_U1`|1bajtový celé číslo bez znaménka.|  
|`ELEMENT_TYPE_I2`|2 bajty celé číslo se znaménkem.|  
|`ELEMENT_TYPE_U2`|2 bajty celé číslo bez znaménka.|  
|`ELEMENT_TYPE_I4`|4 bajty celé číslo se znaménkem.|  
|`ELEMENT_TYPE_U4`|Celé číslo bez znaménka na 4 bajty.|  
|`ELEMENT_TYPE_I8`|8bitové celé číslo se znaménkem.|  
|`ELEMENT_TYPE_U8`|8bitové celé číslo bez znaménka.|  
|`ELEMENT_TYPE_R4`|Bod s plovoucí desetinnou čárkou na 4 bajty.|  
|`ELEMENT_TYPE_R8`|8 bajtů s plovoucí desetinnou čárkou.|  
|`ELEMENT_TYPE_STRING`|Typu System.String.|  
|`ELEMENT_TYPE_PTR`|Modifikátor typu ukazatel.|  
|`ELEMENT_TYPE_BYREF`|Modifikátor typu odkazu.|  
|`ELEMENT_TYPE_VALUETYPE`|Modifikátor typu hodnoty.|  
|`ELEMENT_TYPE_CLASS`|Modifikátor typu třídy.|  
|`ELEMENT_TYPE_VAR`|Typ proměnné Modifikátor třídy.|  
|`ELEMENT_TYPE_ARRAY`|Modifikátor typu vícerozměrné pole.|  
|`ELEMENT_TYPE_GENERICINST`|Modifikátor typu pro obecné typy.|  
|`ELEMENT_TYPE_TYPEDBYREF`|Zadaný odkaz.|  
|`ELEMENT_TYPE_I`|Velikost nativní celé číslo.|  
|`ELEMENT_TYPE_U`|Velikost celé číslo bez znaménka nativní.|  
|`ELEMENT_TYPE_FNPTR`|Ukazatel na funkci.|  
|`ELEMENT_TYPE_OBJECT`|Typ System.Object.|  
|`ELEMENT_TYPE_SZARRAY`|Jednorozměrná, nula dolní mez pole modifikátor typu.|  
|`ELEMENT_TYPE_MVAR`|Metoda modifikátor typu proměnné.|  
|`ELEMENT_TYPE_CMOD_REQD`|Jazyk C vyžaduje modifikátor.|  
|`ELEMENT_TYPE_CMOD_OPT`|Jazyk C volitelný modifikátor.|  
|`ELEMENT_TYPE_INTERNAL`|Interně.|  
|`ELEMENT_TYPE_MAX`|Neplatný typ.|  
|`ELEMENT_TYPE_MODIFIER`|Interně.|  
|`ELEMENT_TYPE_SENTINEL`|Modifikátor typu, který je sentinel seznam proměnný počet parametrů.|  
|`ELEMENT_TYPE_PINNED`|Interně.|  
  
## <a name="remarks"></a>Poznámky  
 Modifikátory typu jsou základem představující složitější typy. A `CorElementType` hodnota modifikátor typu je použité pro hodnotu, která bezprostředně následuje v signatuře typu. Hodnota, která následuje `CorElementType` může být hodnota modifikátor typu `CorElementType` hodnota jednoduchého typu, token metadat nebo jiná hodnota, jak je uvedeno v následující tabulce.  
  
> [!NOTE]
>  Všechna čísla (*číslo*, *argumentů Count*, *tokenu metadat*, *pořadí*, *počet*a *vázán*) jsou uloženy jako komprimovaný celá čísla. Zobrazit [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) na webu ECMA podrobnosti.  
  
|Modifikátor typu|Formát|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|Typ ELEMENT_TYPE_PTR < `CorElementType` hodnotu >|  
|`ELEMENT_TYPE_BYREF`|ELEMENT_TYPE_BYREF < `CorElementType` hodnotu >|  
|`ELEMENT_TYPE_VALUETYPE`|Typ ELEMENT_TYPE_VALUETYPE, který < `mdTypeDef` tokenu metadat >|  
|`ELEMENT_TYPE_CLASS`|Za řetězcem ELEMENT_TYPE_CLASS < `mdTypeDef` tokenu metadat >|  
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR \<číslo >|  
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY < `CorElementType` hodnota > \<pořadí > \<count1 > \<bound1 >... \<countN > \<boundN >|  
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST < `mdTypeDef` tokenu metadat > \<argumentů Count > \<arg1 >... \<argN >|  
|`ELEMENT_TYPE_FNPTR`|Typ ELEMENT_TYPE_FNPTR \<úplný podpis pro funkci, včetně konvence volání >|  
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY < `CorElementType` hodnotu >|  
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR \<číslo >|  
|`ELEMENT_TYPE_CMOD_REQD`|Typ ELEMENT_TYPE_ < `mdTypeRef` nebo `mdTypeDef` tokenu metadat >|  
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT < `mdTypeRef` nebo `mdTypeDef` tokenu metadat >|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Comimage_flags  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
