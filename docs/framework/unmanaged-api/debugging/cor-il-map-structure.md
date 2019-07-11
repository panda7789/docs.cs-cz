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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74f515626f5001cbea1a25e8268338c588524bde
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740543"
---
# <a name="corilmap-structure"></a>COR_IL_MAP – struktura
Určuje změny v relativním posunem funkce.  
  
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
|`oldOffset`|Stará Microsoft intermediate language (MSIL) posun vzhledem k začátku funkci.|  
|`newOffset`|Nový jazyk MSIL posun vzhledem k začátku funkci.|  
|`fAccurate`|`true` Pokud mapování je znám jako přesné; v opačném případě `false`.|  
  
## <a name="remarks"></a>Poznámky  
 Formát mapování je následujícím způsobem: Ladicí program se předpokládá, že `oldOffset` odkazuje na MSIL posun v rámci původní verzí bez úprav kódu MSIL. `newOffset` Parametr odkazuje na odpovídající jazyk MSIL posun v rámci nové instrumentované kódu.  
  
 Pro krokování fungovalo správně, musí být splněny následující požadavky:  
  
- Na mapě mají být řazeny ve vzestupném pořadí.  
  
- By neměl být přeuspořádány instrumentované kód jazyka MSIL.  
  
- Původní kód jazyka MSIL by se neměly odebírat.  
  
- Na mapě by měl obsahovat záznamy pro všechny body posloupnosti ze souboru databáze (PDB) programu mapování.  
  
 Mapa není interpolovat chybějící položky. Následující příklad ukazuje, mapy a jeho výsledky.  
  
 Mapy:  
  
- Posun 0 starý, nový posun 0  
  
- staré posun 5, 10 nových posun  
  
- staré posun 9, 20 nové posun  
  
 Počet výsledků:  
  
- Staré posun 0, 1, 2, 3 nebo 4 se namapují na nové posun 0.  
  
- Posun staré 5, 6, 7 nebo 8 se namapují na nové posun 10.  
  
- Staré posun 9 nebo vyšší se namapují na nové posun 20.  
  
- Nové posun 0, 1, 2, 3, 4, 5, 6, 7, 8 a 9 se namapují na staré posun 0.  
  
- Nové posun 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 se namapují na staré posun 5.  
  
- Nové posun 20 nebo vyšší se namapují na staré posun 9.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
