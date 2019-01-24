---
title: ICorDebugReferenceValue – rozhraní 1
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dbe5388d7c18202f4b89269141d33463edb07a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544270"
---
# <a name="icordebugreferencevalue-interface1"></a>ICorDebugReferenceValue – rozhraní 1
Poskytuje metody, které spravují hodnotu, která je odkaz na objekt. (To znamená, že toto rozhraní poskytuje metody, které spravují ukazatel.) Toto rozhraní implementuje "ICorDebugValue".  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Dereference – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Získá objekt, na který odkazuje.|  
|[DereferenceStrong – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Není implementováno. Nevolejte tuto metodu.|  
|[GetValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Získá aktuální adresu paměti odkazovaného objektu.|  
|[IsNull – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Získá hodnotu, která určuje, jestli to `ICorDebugReferenceValue` v takovém případě je hodnota null, `ICorDebugReferenceValue` neukazuje na objekt.|  
|[SetValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Nastaví aktuální adresu paměti. To znamená, že tato metoda nastaví tuto `ICorDebugReferenceValue` tak, aby odkazoval na objekt.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (CLR) může provádět uvolňování objektů při pokračování laděného procesu. Uvolnění paměti může pohyb objektů v paměti. `ICorDebugReferenceValue` Buď spolupracují s kolekcí uvolnění paměti tak, aby se informace aktualizují po uvolnění paměti nebo ho se implicitně zruší před uvolňování.  
  
 `ICorDebugReferenceValue` Objekt může být implicitně zneplatněné, po pokračuje laděného procesu. Odvozené icordebughandlevalue "–" není zrušena, dokud je explicitně vydání nebo vystavené.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:


- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
