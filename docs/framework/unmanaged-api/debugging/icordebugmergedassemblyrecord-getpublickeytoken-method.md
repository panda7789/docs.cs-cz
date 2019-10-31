---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKeyToken – metoda'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 95ed1303b33b328d1f14ecea6cc318e14991cd54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129777"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>ICorDebugMergedAssemblyRecord:: GetPublicKeyToken – metoda
Získá token veřejného klíče sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbPublicKeyToken`  
 pro Maximální počet bajtů v poli `pbPublicKeyToken`.  
  
 `pcbPublicKeyToken`  
 mimo Ukazatel na skutečný počet bajtů zapsaných do pole `pbPublicKeyToken`.  
  
 `pbPublicKeyToken`  
 mimo Ukazatel na pole bajtů, které obsahuje token veřejného klíče sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Token veřejného klíče sestavení je posledních osm bajtů hodnoty hash SHA1 svého veřejného klíče.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMergedAssemblyRecord – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
