---
title: CorElementType Enumeration1
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
ms.openlocfilehash: ebe2cf95f5637e6924b85c2389f1c59679580298
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449167"
---
# <a name="corelementtype-enumeration1"></a>CorElementType Enumeration1
Určuje modul common language runtime <xref:System.Type>, modifikátor typu, nebo informace o typu v podpis typ metadat.  
  
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
|`ELEMENT_TYPE_VOID`|Typ hodnoty void.|  
|`ELEMENT_TYPE_BOOLEAN`|Typem logická hodnota|  
|`ELEMENT_TYPE_CHAR`|Typy znaků.|  
|`ELEMENT_TYPE_I1`|1bajtový znaménkem.|  
|`ELEMENT_TYPE_U1`|Celé číslo bez znaménka 1bajtový.|  
|`ELEMENT_TYPE_I2`|Podepsaný 2bajtový celočíselný.|  
|`ELEMENT_TYPE_U2`|Celé číslo bez znaménka 2bajtová.|  
|`ELEMENT_TYPE_I4`|4bajtový znaménkem.|  
|`ELEMENT_TYPE_U4`|Celé číslo bez znaménka 4bajtový.|  
|`ELEMENT_TYPE_I8`|Znaménkem 8 bajtů.|  
|`ELEMENT_TYPE_U8`|Celé číslo bez znaménka 8 bajtů.|  
|`ELEMENT_TYPE_R4`|4bajtový plovoucí desetinné čárky.|  
|`ELEMENT_TYPE_R8`|8bajtový plovoucí desetinné čárky.|  
|`ELEMENT_TYPE_STRING`|Typ System.String.|  
|`ELEMENT_TYPE_PTR`|Typ modifikátoru ukazatele.|  
|`ELEMENT_TYPE_BYREF`|Odkaz na typ modifikátoru.|  
|`ELEMENT_TYPE_VALUETYPE`|Typ modifikátoru hodnotu.|  
|`ELEMENT_TYPE_CLASS`|Typ modifikátoru třídy.|  
|`ELEMENT_TYPE_VAR`|Typ proměnné – Modifikátor třídy.|  
|`ELEMENT_TYPE_ARRAY`|Typ modifikátoru multidimenzionální pole.|  
|`ELEMENT_TYPE_GENERICINST`|Typ modifikátoru pro obecné typy.|  
|`ELEMENT_TYPE_TYPEDBYREF`|Zadaný odkaz.|  
|`ELEMENT_TYPE_I`|Velikost nativní celé číslo.|  
|`ELEMENT_TYPE_U`|Velikost celé číslo bez znaménka nativní.|  
|`ELEMENT_TYPE_FNPTR`|Ukazatel na funkci.|  
|`ELEMENT_TYPE_OBJECT`|Typ System.Object.|  
|`ELEMENT_TYPE_SZARRAY`|Jednorozměrná, nulové modifikátor typu pole dolní mez.|  
|`ELEMENT_TYPE_MVAR`|Typ proměnné – modifikátor metoda.|  
|`ELEMENT_TYPE_CMOD_REQD`|Jazyk C vyžaduje modifikátor.|  
|`ELEMENT_TYPE_CMOD_OPT`|Jazyk C volitelné modifikátor.|  
|`ELEMENT_TYPE_INTERNAL`|Interně.|  
|`ELEMENT_TYPE_MAX`|Neplatný typ.|  
|`ELEMENT_TYPE_MODIFIER`|Interně.|  
|`ELEMENT_TYPE_SENTINEL`|Modifikátor typu, který je sentinel seznam proměnný počet parametrů.|  
|`ELEMENT_TYPE_PINNED`|Interně.|  
  
## <a name="remarks"></a>Poznámky  
 Modifikátory typu tvoří základ pro představující více komplexní typy. A `CorElementType` na hodnotu, která následuje v podpis typu, je použita hodnota modifikátor typu. Hodnota, která odpovídá `CorElementType` může být hodnota typu modifikátor `CorElementType` hodnota jednoduchého typu, metadata token nebo jinou hodnotu, jak je uvedeno v následující tabulce.  
  
> [!NOTE]
>  Všechna čísla (*číslo*, *argument počet*, *metadata token*, *pořadí*, *počet*a *vázaný*) jsou uloženy jako komprimovaný celá čísla. V tématu [standardní standardy ECMA-335 - společné jazykové infrastruktury (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487) na webu ECMA podrobnosti.  
  
|Modifikátor typu|Formát|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|ELEMENT_TYPE_PTR < `CorElementType` hodnota >|  
|`ELEMENT_TYPE_BYREF`|Typu ELEMENT_TYPE_BYREF < `CorElementType` hodnota >|  
|`ELEMENT_TYPE_VALUETYPE`|Typ ELEMENT_TYPE_VALUETYPE, který < `mdTypeDef` metadata token >|  
|`ELEMENT_TYPE_CLASS`|ELEMENT_TYPE_CLASS < `mdTypeDef` metadata token >|  
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR \<číslo >|  
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY < `CorElementType` hodnota > \<pořadí > \<count1 > \<bound1 >... \<countN > \<boundN >|  
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST < `mdTypeDef` metadata token > \<argument Count > \<arg1 >... \<argN >|  
|`ELEMENT_TYPE_FNPTR`|ELEMENT_TYPE_FNPTR \<dokončení podpis pro funkce, včetně konvence volání >|  
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY < `CorElementType` hodnota >|  
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR \<číslo >|  
|`ELEMENT_TYPE_CMOD_REQD`|Typ ELEMENT_TYPE_ < `mdTypeRef` nebo `mdTypeDef` metadata token >|  
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT < `mdTypeRef` nebo `mdTypeDef` metadata token >|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
