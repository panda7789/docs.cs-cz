---
title: "COR_IL_MAP – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_IL_MAP
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_IL_MAP
helpviewer_keywords: COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e2772833d75ced2209896ca37cf6cf37fb965f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corilmap-structure"></a>COR_IL_MAP – struktura
Určuje změny v relativní posun funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`oldOffset`|Staré Microsoft (MSIL intermediate language) posunuto vzhledem ke začátku funkce.|  
|`newOffset`|Nové MSIL posun vzhledem k začátku funkce.|  
|`fAccurate`|`true`Pokud mapování se označuje jako přesné; v opačném `false`.|  
  
## <a name="remarks"></a>Poznámky  
 Formát mapy je následující: ladicí program předpokládat, že `oldOffset` odkazuje na MSIL posun v rámci kód MSIL původní, beze změny. `newOffset` Parametr odkazuje na odpovídající posun MSIL nové, instrumentovaného kódu.  
  
 Pro krokování s fungovalo správně, musí být splněny následující požadavky:  
  
-   Mapy by měly být seřazeny ve vzestupném pořadí.  
  
-   Instrumentované MSIL kód by neměl přeuspořádány.  
  
-   Původní kód MSIL by se neměly odebírat.  
  
-   Mapy by měla obsahovat položky pro všechny body sekvence ze souboru databáze (PDB) program mapování.  
  
 Mapy není interpolovat položky. Následující příklad ukazuje mapu a jeho výsledky.  
  
 Mapování:  
  
-   původní posun 0, 0 nové posun  
  
-   původní offset 5, 10 nové posun  
  
-   9 staré offset, 20 nové posunutí  
  
 Výsledky:  
  
-   Původní posun 0, 1, 2, 3 nebo 4 budou mapována na nový posun 0.  
  
-   Původní posun 5, 6, 7 nebo 8 budou mapována na nový posun 10.  
  
-   Původní posun 9 nebo vyšší budou mapována na nový posun 20.  
  
-   Nové posun 0, 1, 2, 3, 4, 5, 6, 7, 8 nebo 9 budou mapována na staré posunu 0.  
  
-   Nové posun 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 budou mapována na staré posun 5.  
  
-   Nové posun 20 nebo vyšší budou mapována na staré posun 9.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
