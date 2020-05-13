---
title: ICorDebugProcess6::DecodeEvent – metoda
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: 7c163311f9ce8f3d98ce72f45165a5e517c6c0aa
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205505"
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
 pro Počet prvků v `pRecord` bajtovém poli.  
  
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
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugProcess6](icordebugprocess6-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
