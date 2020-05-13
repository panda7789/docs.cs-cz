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
ms.openlocfilehash: 5650a7e6e6cb0108f0d043914ea94debe2b703bf
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213098"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum – rozhraní
Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](icordebuggcreferenceenum-next-method.md)|Získá zadaný počet instancí [COR_GC_REFERENCE](cor-gc-reference-structure.md) , které obsahují informace o objektech, které budou uvolněny z paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugGCReferenceEnum`Rozhraní implementuje rozhraní "ICorDebugEnum".  
  
 `ICorDebugGCReferenceEnum`Instance je naplněna instancí [COR_GC_REFERENCE](cor-gc-reference-structure.md) voláním metody [ICorDebugProcess5:: EnumerateGCReferences –](icordebugprocess5-enumerategcreferences-method.md) . Objekty [COR_GC_REFERENCE](cor-gc-reference-structure.md) lze vyčíslit voláním metody [ICorDebugGCReference:: Next](icordebuggcreferenceenum-next-method.md) .  
  
 Objekty [COR_GC_REFERENCE](cor-gc-reference-structure.md) v kolekci, které jsou vyplněny touto metodou, reprezentují tři druhy objektů:  
  
- Objekty ze všech spravovaných zásobníků. To zahrnuje živé odkazy ve spravovaném kódu a také objekty vytvořené modulem CLR (Common Language Runtime).  
  
- Objekty z tabulky popisovačů. To zahrnuje silné odkazy ( `HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT` ) a statické proměnné v modulu.  
  
- Objekty z fronty finalizační metody. Objekty kořene fronty finalizační metody, dokud není spuštěn finalizační metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
