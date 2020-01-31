---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKeyToken – metoda'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 543083703cd0cbbce9dc0660383713202fa2f0b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793108"
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

- [ICorDebugMergedAssemblyRecord – rozhraní](icordebugmergedassemblyrecord-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
