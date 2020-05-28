---
title: CorElementType – výčet
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
ms.openlocfilehash: 25fb3278e576ebe4a538379918e868b2e5f87911
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007868"
---
# <a name="corelementtype-enumeration"></a>CorElementType – výčet

Určuje modul CLR (Common Language Runtime) <xref:System.Type> , modifikátor typu nebo informace o typu v signatuře typu metadat.

## <a name="syntax"></a>Syntaxe

```cpp
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

|Člen|Description|
|------------|-----------------|
|`ELEMENT_TYPE_END`|Používá se interně.|
|`ELEMENT_TYPE_VOID`|Typ void.|
|`ELEMENT_TYPE_BOOLEAN`|Typ Boolean|
|`ELEMENT_TYPE_CHAR`|Typ znaku.|
|`ELEMENT_TYPE_I1`|Celé číslo se znaménkem na 1 bajt.|
|`ELEMENT_TYPE_U1`|Celé číslo s nepodepsaným 1 bajtem.|
|`ELEMENT_TYPE_I2`|Celé číslo se znaménkem na 2 bajt.|
|`ELEMENT_TYPE_U2`|Celé číslo bez znaménka 2-Byte.|
|`ELEMENT_TYPE_I4`|Celé číslo se znaménkem o velikosti 4 bajty.|
|`ELEMENT_TYPE_U4`|Celé číslo se znaménkem a 4 bajty.|
|`ELEMENT_TYPE_I8`|Celé 8bitové číslo se znaménkem.|
|`ELEMENT_TYPE_U8`|Celé číslo bez znaménka na 8 bajtů.|
|`ELEMENT_TYPE_R4`|Desetinná čárka se čtyřmi bajty.|
|`ELEMENT_TYPE_R8`|Plovoucí desetinná čárka (8 bajtů).|
|`ELEMENT_TYPE_STRING`|Typ System. String.|
|`ELEMENT_TYPE_PTR`|Modifikátor typu ukazatele.|
|`ELEMENT_TYPE_BYREF`|Modifikátor typu odkazu.|
|`ELEMENT_TYPE_VALUETYPE`|Modifikátor typu hodnoty.|
|`ELEMENT_TYPE_CLASS`|Modifikátor typu třídy.|
|`ELEMENT_TYPE_VAR`|Modifikátor typu proměnné třídy.|
|`ELEMENT_TYPE_ARRAY`|Modifikátor typu multidimenzionálního pole.|
|`ELEMENT_TYPE_GENERICINST`|Modifikátor typu pro obecné typy.|
|`ELEMENT_TYPE_TYPEDBYREF`|Zadaný odkaz.|
|`ELEMENT_TYPE_I`|Velikost nativního celého čísla.|
|`ELEMENT_TYPE_U`|Velikost nativního celého čísla bez znaménka.|
|`ELEMENT_TYPE_FNPTR`|Ukazatel na funkci.|
|`ELEMENT_TYPE_OBJECT`|Typ System. Object.|
|`ELEMENT_TYPE_SZARRAY`|Jednorozměrné, nulový modifikátor typu pole s nižším rozsahem.|
|`ELEMENT_TYPE_MVAR`|Modifikátor typu proměnné metody.|
|`ELEMENT_TYPE_CMOD_REQD`|Modifikátor vyžadovaný jazykem jazyka C.|
|`ELEMENT_TYPE_CMOD_OPT`|Volitelný modifikátor jazyka C.|
|`ELEMENT_TYPE_INTERNAL`|Používá se interně.|
|`ELEMENT_TYPE_MAX`|Neplatný typ.|
|`ELEMENT_TYPE_MODIFIER`|Používá se interně.|
|`ELEMENT_TYPE_SENTINEL`|Modifikátor typu, který je Sentinel pro seznam variabilního počtu parametrů.|
|`ELEMENT_TYPE_PINNED`|Používá se interně.|

## <a name="remarks"></a>Poznámky

Modifikátory typu tvoří základ pro reprezentace složitějších typů. `CorElementType`Hodnota modifikátoru typu se aplikuje na hodnotu, která se na Signature typu hned doplní. Hodnota, která následuje jako `CorElementType` hodnota modifikátoru typu, může být `CorElementType` jednoduchá hodnota typu, token metadat nebo jiná hodnota, jak je uvedeno v následující tabulce.

> [!NOTE]
> Všechna čísla (*číslo*, *počet argumentů*, *token metadat*, *pořadí*, *počet*a *mez*) jsou ukládána jako komprimovaná celá čísla. Podrobnosti najdete v tématu [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) na webu ECMA.

|Modifikátor typu|Formát|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|ELEMENT_TYPE_PTR\<a `CorElementType` value>|
|`ELEMENT_TYPE_BYREF`|ELEMENT_TYPE_BYREF\<a `CorElementType` value>|
|`ELEMENT_TYPE_VALUETYPE`|ELEMENT_TYPE_VALUETYPE\<an `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_CLASS`|ELEMENT_TYPE_CLASS\<an `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR\<number>|
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN>\<boundN>|
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ...\<argN>|
|`ELEMENT_TYPE_FNPTR`|ELEMENT_TYPE_FNPTR\<complete signature for the function, including calling convention>|
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY\<a `CorElementType` value>|
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR\<number>|
|`ELEMENT_TYPE_CMOD_REQD`|ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT\<a `mdTypeRef` or `mdTypeDef` metadata token>|

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** CorHdr. h

**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
