---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKey – metoda'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: c8c6e9adcb9d29f5e234dd1b8dfd351fac575301
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793120"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a>ICorDebugMergedAssemblyRecord:: GetPublicKey – metoda
Získá veřejný klíč sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbPublicKey`  
 pro Maximální počet bajtů v poli `pbPublicKey`.  
  
 `pcbPublicKey`  
 mimo Ukazatel na skutečný počet bajtů zapsaných do pole `pbPublicKey`.  
  
 `pbPublicKey`  
 mimo Ukazatel na pole bajtů, které obsahuje veřejný klíč sestavení.  
  
## <a name="remarks"></a>Poznámky  
  
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
