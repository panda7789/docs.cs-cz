---
title: "CorSymAddrKind – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymAddrKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymAddrKind
helpviewer_keywords: CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 300913f9ea89044e425f9f05856d13fa15cdc015
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
