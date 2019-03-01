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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4315c9f5296e8c3ffc9d8241b929c71c2448db6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965858"
---
# <a name="icordebugeval2-interface"></a>ICorDebugEval2 – rozhraní

Rozšiřuje "ICorDebugEval" k poskytování podpory pro obecné typy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CallParameterizedFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|Nastavuje volání zadaného "ICorDebugFunction", které mohou být vnořené uvnitř typu, jejíž konstruktor přijímá parametry typu nebo samotné trvat parametry typu.|  
|[CreateValueForType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|Získá ukazatel na novou "ICorDebugValue" zadaného typu, s počáteční hodnotou null nebo nula.|  
|[NewParameterizedArray – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|Přidělí nové pole typu zadaného elementu a dimenze.|  
|[NewParameterizedObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|Vytvoří nový objekt typ s parametry a volání metody konstruktoru objektu.|  
|[NewParameterizedObjectNoConstructor – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Vytvoří nový objekt typ s parametry ze zadané třídy bez pokusu o volání metody konstruktoru|  
|[NewStringWithLength – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|Vytvoří nového řetězce zadané délky se zadaným obsahem.|  
|[RudeAbort – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|Zruší výpočet, který tato `ICorDebugEval2` v tuto chvíli provádí.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
