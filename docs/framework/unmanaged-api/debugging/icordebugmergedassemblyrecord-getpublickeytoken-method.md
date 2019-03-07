---
title: ICorDebugMergedAssemblyRecord::GetPublicKeyToken – metoda
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 726ded615fb6d1bcd0a3a4b92e93f3675d9ce8fa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484560"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>ICorDebugMergedAssemblyRecord::GetPublicKeyToken – metoda
Získá token veřejného klíče sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbPublicKeyToken`  
 [in] Maximální počet bajtů `pbPublicKeyToken` pole.  
  
 `pcbPublicKeyToken`  
 [out] Ukazatel na skutečný počet bajtů zapsaný na `pbPublicKeyToken` pole.  
  
 `pbPublicKeyToken`  
 [out] Ukazatel na bajtové pole, který obsahuje token veřejného klíče sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Token veřejného klíče sestavení je posledních osm bajtů hash SHA1 svůj veřejný klíč.  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugMergedAssemblyRecord – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
