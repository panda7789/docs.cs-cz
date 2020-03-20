---
title: ICorDebugProcess6::DecodeEvent – metoda
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: a0b77724a5a70461073d554a9794c5a904f6a363
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178585"
---
# <a name="icordebugprocess6decodeevent-method"></a>ICorDebugProcess6::DecodeEvent – metoda
Dekóduje události spravovaného ladění, které byly zapouzdřeny v datové části speciálně vytvořených nativních událostí ladění výjimek.  
  
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
 [v] Ukazatel na bajtové pole z události ladění nativní výjimky, která obsahuje informace o události spravovaného ladění.  
  
 `countBytes`  
 [v] Počet prvků v `pRecord` poli bajtů.  
  
 `format`  
 [v] Člen výčtu [CorDebugRecordFormat,](cordebugrecordformat-enumeration.md) který určuje formát události nespravovaného ladění.  
  
 `dwFlags`  
 [v] Bitové pole, které závisí na cílové architektuře a určuje další informace o události ladění. Pro systémy Windows může být členem výčtu [CorDebugDecodeEventFlagsWindows.](cordebugdecodeeventflagswindows-enumeration.md)  
  
 `dwThreadId`  
 [v] Identifikátor operačního systému podprocesu, na kterém byla vyvolána výjimka.  
  
 `ppEvent`  
 [out] Ukazatel na adresu objektu [ICorDebugDebugEvent,](icordebugdebugevent-interface.md) který představuje dekódovanou událost spravovaného ladění.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s nativní .NET.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugProcess6](icordebugprocess6-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
