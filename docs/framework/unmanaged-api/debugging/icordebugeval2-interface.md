---
title: ICorDebugEval2 Interface1
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
ms.openlocfilehash: da4364e132e2a9d578a761eea77d0dfc8d0b92aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugeval2-interface1"></a>ICorDebugEval2 Interface1
Rozšiřuje "ICorDebugEval" kvůli zajištění podpory pro obecné typy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CallParameterizedFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|Nastaví volání zadaný "ICorDebugFunction", který může být vnořena ve typu jehož konstruktor přijímá parametry typu nebo sám přijmout parametry typu.|  
|[CreateValueForType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|Získá ukazatel nové "ICorDebugValue" zadaného typu, s počáteční hodnotou null nebo nula.|  
|[NewParameterizedArray – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|Přiděluje nový pole typu zadaného elementu a dimenze.|  
|[NewParameterizedObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|Vytvoří nový objekt parametrizované typu a volá konstruktor metodu objektu.|  
|[NewParameterizedObjectNoConstructor – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Vytvoří nový objekt parametrizované typ zadané třídy bez pokus o volání metody konstruktoru|  
|[NewStringWithLength – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|Vytvoří nový řetězec určené délky zadaný obsah.|  
|[RudeAbort – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|Zruší výpočet které tento `ICorDebugEval2` právě provádí.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
