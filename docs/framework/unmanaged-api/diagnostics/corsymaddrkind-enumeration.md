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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 389cf2e77728002ce1078f63df3d741d1847c105
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744970"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind – výčet
Určuje typ přidávané adresy paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`ADDR_IL_OFFSET`|Označuje, Microsoft intermediate language (MSIL) místní proměnná nebo parametr indexu.|  
|`ADDR_NATIVE_RVA`|Určuje relativní virtuální adresu do modulu.|  
|`ADDR_NATIVE_REGISTER`|Označuje registru procesoru.|  
|`ADDR_NATIVE_REGREL`|Označuje, že první adresa registru a druhá adresa je posun.|  
|`ADDR_NATIVE_OFFSET`|Určuje posun od základní adresa.|  
|`ADDR_NATIVE_REGREG`|Označuje, že první adresa je nízká část registru a druhá adresa je vysoké.|  
|`ADDR_NATIVE_REGSTK`|Označuje, že první adresa je nízká část registru, druhá je vysoká část a třetí je posun.|  
|`ADDR_NATIVE_STKREG`|Označuje, že první adresa je registr, posun je druhý a třetí je vysoká část do registru.|  
|`ADDR_BITFIELD`|Označuje, že první adresa je začátek pole a druhý adresa je délka pole.|  
|`ADDR_NATIVE_ISECTOFFSET`|Označuje, že první adresa je oddíl a druhá adresa je posun.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [Výčty pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
