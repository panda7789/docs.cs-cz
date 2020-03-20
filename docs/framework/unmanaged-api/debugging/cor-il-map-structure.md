---
title: COR_IL_MAP – struktura
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: 4c79d0e4e37f3f884651e49c8fff6db72fac4f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179295"
---
# <a name="cor_il_map-structure"></a>COR_IL_MAP – struktura
Určuje změny v relativním odsazení funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`oldOffset`|Starý microsoft zprostředkující jazyk (MSIL) posun vzhledem k začátku funkce.|  
|`newOffset`|Nový posun MSIL vzhledem k začátku funkce.|  
|`fAccurate`|`true`je-li známo, že mapování je přesné; v `false`opačném případě .|  
  
## <a name="remarks"></a>Poznámky  
 Formát mapy je následující: Ladicí program bude `oldOffset` předpokládat, že odkazuje na posun MSIL v rámci původního, neupraveného kódu MSIL. Parametr `newOffset` odkazuje na odpovídající posun MSIL v rámci nového instrumentovaného kódu.  
  
 Pro krokování správně fungovat, by měly být splněny následující požadavky:  
  
- Mapa by měla být seřazena vzestupně.  
  
- Instrumentovaný kód MSIL by neměl být přeřazen.  
  
- Původní kód MSIL by neměl být odebrán.  
  
- Mapa by měla obsahovat položky k mapování všech sekvenčních bodů ze souboru databáze programu (PDB).  
  
 Mapa neinterpoluje chybějící položky. Následující příklad ukazuje mapu a její výsledky.  
  
 Mapu:  
  
- 0 starý posun, 0 nový posun  
  
- 5 starý posun, 10 nových offsetů  
  
- 9 starý posun, 20 nových offsetů  
  
 Výsledky:  
  
- Staré posun 0, 1, 2, 3 nebo 4 bude mapován na nový posun 0.  
  
- Starý posun 5, 6, 7 nebo 8 bude mapován na nové posun10.  
  
- Starý posun 9 nebo vyšší bude mapován na nový posun 20.  
  
- Nové posun0, 1, 2, 3, 4, 5, 6, 7, 8 nebo 9 bude mapován na staré posun0.  
  
- Nový posun 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 bude mapován na starý posun 5.  
  
- Nový posun 20 nebo vyšší bude mapován na staré posun 9.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro ladění](debugging-structures.md)
- [ladění](index.md)
