---
title: ICorDebugProcess6::DecodeEvent – metoda
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: be30b1ff79c2aceb97eb4ad42052da7dd162f5d3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792289"
---
# <a name="icordebugprocess6decodeevent-method"></a>ICorDebugProcess6::DecodeEvent – metoda
Dekóduje spravované události ladění, které byly zapouzdřeny v datové části speciálně vytvořené nativní výjimky ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRecord`  
 pro Ukazatel na pole bajtů z nativní události ladění výjimky, která obsahuje informace o spravované události ladění.  
  
 `countBytes`  
 pro Počet prvků v poli `pRecord` bajtů.  
  
 `format`  
 pro Člen výčtu [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) , který určuje formát nespravované události ladění.  
  
 `dwFlags`  
 pro Bitové pole, které závisí na cílové architektuře a které určuje další informace o události ladění. Pro systémy Windows může být členem výčtu [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) .  
  
 `dwThreadId`  
 pro Identifikátor operačního systému vlákna, na kterém byla výjimka vyvolána.  
  
 `ppEvent`  
 mimo Ukazatel na adresu objektu [ICorDebugDebugEvent](icordebugdebugevent-interface.md) , který představuje dekódovou spravovanou událost ladění.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess6 – rozhraní](icordebugprocess6-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
