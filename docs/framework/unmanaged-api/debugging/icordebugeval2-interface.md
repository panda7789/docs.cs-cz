---
title: ICorDebugEval2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
ms.openlocfilehash: b597d95b5b25e5ebf04fac48e4f3fda312a9594c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976119"
---
# <a name="icordebugeval2-interface"></a>ICorDebugEval2 – rozhraní

Rozšiřuje "ICorDebugEval", aby poskytovala podporu pro obecné typy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CallParameterizedFunction – metoda](icordebugeval2-callparameterizedfunction-method.md)|Nastaví volání zadaného "ICorDebugFunction", která může být vnořena do typu, jehož konstruktor přijímá parametry typu, nebo může sám převzít parametry typu.|  
|[CreateValueForType – metoda](icordebugeval2-createvaluefortype-method.md)|Získá ukazatel na nový "ICorDebugValue" zadaného typu s počáteční hodnotou null nebo nula.|  
|[NewParameterizedArray – metoda](icordebugeval2-newparameterizedarray-method.md)|Přidělí nové pole zadaného typu a dimenzí prvku.|  
|[NewParameterizedObject – metoda](icordebugeval2-newparameterizedobject-method.md)|Vytvoří instanci nového parametrizovaného typu objektu a zavolá metodu konstruktoru objektu.|  
|[NewParameterizedObjectNoConstructor – metoda](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Vytvoří instanci nového parametrizovaného typu objektu zadané třídy bez pokusu o volání metody konstruktoru.|  
|[NewStringWithLength – metoda](icordebugeval2-newstringwithlength-method.md)|Vytvoří nový řetězec o zadané délce se zadaným obsahem.|  
|[RudeAbort – metoda](icordebugeval2-rudeabort-method.md)|Přeruší výpočet, který `ICorDebugEval2` právě provádí.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
