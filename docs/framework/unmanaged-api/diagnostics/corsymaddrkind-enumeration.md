---
title: CorSymAddrKind – výčet
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
ms.openlocfilehash: 12f31d0bf224e38418818122dad3586ec687b2ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448574"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind – výčet
Určuje typ adresy paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|Označuje místní proměnnou nebo index parametru jazyka MSIL (Microsoft Intermediate Language).|  
|`ADDR_NATIVE_RVA`|Označuje relativní virtuální adresu do modulu.|  
|`ADDR_NATIVE_REGISTER`|Označuje registr procesoru.|  
|`ADDR_NATIVE_REGREL`|Označuje, že první adresa je registr a druhá adresa je posun.|  
|`ADDR_NATIVE_OFFSET`|Označuje posun od základní adresy.|  
|`ADDR_NATIVE_REGREG`|Označuje, že první adresa je dolní část registru, a druhá adresa je horní část.|  
|`ADDR_NATIVE_REGSTK`|Označuje, že první adresa je dolní část registru, druhá je horní část a třetí je posun.|  
|`ADDR_NATIVE_STKREG`|Označuje, že první adresa je registr, druhým je posun a třetí je vysoká část registru.|  
|`ADDR_BITFIELD`|Označuje, že první adresa je začátek pole a druhá adresa je délka pole.|  
|`ADDR_NATIVE_ISECTOFFSET`|Označuje, že první adresa je oddíl a druhá adresa je posun.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
