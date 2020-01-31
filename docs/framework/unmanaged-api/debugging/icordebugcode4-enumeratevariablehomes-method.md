---
title: 'ICorDebugCode4:: EnumerateVariableHomes – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: ca452b230e2508f2d69c9aa38f274db506f3a906
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784092"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a>ICorDebugCode4:: EnumerateVariableHomes – metoda
Získá enumerátor pro místní proměnné a argumenty ve funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 Ukazatel na adresu objektu rozhraní [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) , který je enumerátorem pro místní proměnné a argumenty ve funkci.  
  
## <a name="remarks"></a>Poznámky  
 Objekt rozhraní [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) je standardní enumerátor odvozený z rozhraní ICorDebugEnum, které umožňuje vytvořit výčet objektů [ICorDebugVariableHome](icordebugvariablehome-interface.md) . Kolekce může obsahovat více objektů [ICorDebugVariableHome](icordebugvariablehome-interface.md) pro stejný slot nebo index argumentu, pokud mají různé domy v různých fázích funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugCode4 – rozhraní](icordebugcode4-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
