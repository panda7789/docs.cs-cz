---
title: ICorDebugDataTarget2::EnumerateThreadIDs – metoda
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 120a970aac33b1ab06ae47335a959d2791f893ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178981"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a>ICorDebugDataTarget2::EnumerateThreadIDs – metoda
Vrátí seznam aktivních ID vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 cID vláken  
 [v] Maximální počet podprocesů, jejichž ID mohou být vráceny.  
  
 pcThreadIds  
 [out] Ukazatel na `ULONG32` a, který označuje skutečný počet ID `pThreadIds` podprocesů zapsaných do pole.  
  
 pThreadIDs  
 Pole identifikátorů vláken.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s nativní .NET.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md). **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugDataTarget2 – rozhraní](icordebugdatatarget2-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
