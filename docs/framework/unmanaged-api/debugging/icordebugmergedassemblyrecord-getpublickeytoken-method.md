---
title: ICorDebugMergedAssemblyRecord::Metoda GetPublicKeyToken
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 79df5c3e8b07879a26272f595664abab011101bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178726"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>ICorDebugMergedAssemblyRecord::Metoda GetPublicKeyToken
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
 [v] Maximální počet bajtů v `pbPublicKeyToken` poli.  
  
 `pcbPublicKeyToken`  
 [out] Ukazatel na skutečný počet bajtů zapsaných do `pbPublicKeyToken` pole.  
  
 `pbPublicKeyToken`  
 [out] Ukazatel na bajtové pole, které obsahuje token veřejného klíče sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Token veřejného klíče sestavení je posledních osm bajtů sha1 hash jeho veřejného klíče.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s nativní .NET.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugMergedAssemblyRecord – rozhraní](icordebugmergedassemblyrecord-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
