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
ms.openlocfilehash: 98cf49714829b4b2f80e0240c2ebde7fa6c280e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425402"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind – výčet
Určuje typ adresa paměti.  
  
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
|`ADDR_IL_OFFSET`|Označuje Microsoft (MSIL intermediate language) místní proměnné nebo parametru indexem.|  
|`ADDR_NATIVE_RVA`|Určuje relativní virtuální adresy do modulu.|  
|`ADDR_NATIVE_REGISTER`|Označuje registrace procesoru.|  
|`ADDR_NATIVE_REGREL`|Označuje, že první adresa je registr a druhá adresa je posun.|  
|`ADDR_NATIVE_OFFSET`|Určuje posun z bázové adresy.|  
|`ADDR_NATIVE_REGREG`|Označuje, že první adresa je nízkou část do registru a druhá adresa je vysoká část.|  
|`ADDR_NATIVE_REGSTK`|Označuje, že první adresa je nízkou část zaregistrovat, druhý je vysoká část a třetí je posun.|  
|`ADDR_NATIVE_STKREG`|Označuje, že první adresa je registr, posun je druhý a třetí je vysoká část registru.|  
|`ADDR_BITFIELD`|Označuje, že první adresa je začátek pole a druhá adresa je délka pole.|  
|`ADDR_NATIVE_ISECTOFFSET`|Označuje, že první adresa je v části a druhá adresa je posun.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
