---
title: ICorDebugGCReferenceEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: f01c27376191c3a2dddf56dae4b26c8b5193c73e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788645"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum – rozhraní
Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](icordebuggcreferenceenum-next-method.md)|Získá zadaný počet instancí [COR_GC_REFERENCE](cor-gc-reference-structure.md) , které obsahují informace o objektech, které budou uvolněny z paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugGCReferenceEnum` implementuje rozhraní "ICorDebugEnum".  
  
 Instance `ICorDebugGCReferenceEnum` se naplní pomocí [COR_GC_REFERENCE](cor-gc-reference-structure.md) instancí voláním metody [ICorDebugProcess5:: EnumerateGCReferences –](icordebugprocess5-enumerategcreferences-method.md) . Objekty [COR_GC_REFERENCE](cor-gc-reference-structure.md) lze vyčíslit voláním metody [ICorDebugGCReference:: Next](icordebuggcreferenceenum-next-method.md) .  
  
 Objekty [COR_GC_REFERENCE](cor-gc-reference-structure.md) v kolekci, které jsou vyplněny touto metodou, reprezentují tři druhy objektů:  
  
- Objekty ze všech spravovaných zásobníků. To zahrnuje živé odkazy ve spravovaném kódu a také objekty vytvořené modulem CLR (Common Language Runtime).  
  
- Objekty z tabulky popisovačů. To zahrnuje silné odkazy (`HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT`) a statické proměnné v modulu.  
  
- Objekty z fronty finalizační metody. Objekty kořene fronty finalizační metody, dokud není spuštěn finalizační metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
