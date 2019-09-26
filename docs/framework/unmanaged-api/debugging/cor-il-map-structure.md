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
ms.openlocfilehash: 5ae4c5743b01c4a9087323678d315473631cb32f
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274041"
---
# <a name="cor_il_map-structure"></a>COR_IL_MAP – struktura
Určuje změny relativního posunu funkce.  
  
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
|`oldOffset`|Starý posun jazyka MSIL (Microsoft Intermediate Language) vzhledem k začátku funkce.|  
|`newOffset`|Nový posun MSIL vzhledem k začátku funkce.|  
|`fAccurate`|`true`je-li mapování známo, že je přesné; v opačném případě. `false`|  
  
## <a name="remarks"></a>Poznámky  
 Formát mapy je následující: Ladicí program bude předpokládat, `oldOffset` že odkazuje na posun MSIL v rámci původního nezměněného kódu jazyka MSIL. `newOffset` Parametr odkazuje na odpovídající posun MSIL v rámci nového, instrumentované kódu.  
  
 Aby krokování fungovalo správně, měli byste splnit následující požadavky:  
  
- Mapa by se měla seřadit ve vzestupném pořadí.  
  
- Instrumentované kódy MSIL by se neměly přeřadit.  
  
- Původní kód MSIL by neměl být odebrán.  
  
- Mapa by měla obsahovat položky pro mapování všech bodů sekvence ze souboru databáze programu (PDB).  
  
 Mapa neinterpoluje chybějící položky. Následující příklad ukazuje mapu a její výsledky.  
  
 Mapy  
  
- 0 staré odsazení, 0 nového posunu  
  
- 5 Old posun, 10 nových posunů  
  
- 9 staré posunutí, 20 nových posunů  
  
 Důsledk  
  
- Starý posun 0, 1, 2, 3 nebo 4 se namapuje na nový posun 0.  
  
- Starý posun z 5, 6, 7 nebo 8 se namapuje na nový posun 10.  
  
- Původní posun 9 nebo vyšší se namapuje na nový posun 20.  
  
- Nové odsazení 0, 1, 2, 3, 4, 5, 6, 7, 8 nebo 9 bude namapováno na starý posun 0.  
  
- Nové posuny 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 budou namapovány na starý posun 5.  
  
- Nový posun o hodnotě 20 nebo vyšší bude mapován na starý posun 9.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorProf. idl  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
