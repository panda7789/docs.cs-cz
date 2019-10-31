---
title: 'ICorDebugSymbolProvider:: GetTypeProps – metoda'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: c87d9f6d0a719dae5e532e9c0369a7f9fc03748a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133670"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>ICorDebugSymbolProvider:: GetTypeProps – metoda
Vrátí informace o vlastnostech typu, jako je například počet podpisů svých obecných parametrů, s ohledem na relativní virtuální adresu (RVA) v tabulce vtable.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tableRva`  
 pro Relativní virtuální adresa (RVA) v tabulce vtable.  
  
 `cbSignature`  
 pro Velikost pole `signature`. Viz část poznámky.  
  
 `pcbSignature`  
 mimo mimo Ukazatel na velikost vráceného pole `signature`.  
  
 `signature`  
 mimo Vyrovnávací paměť, která obsahuje token TypeSpec podpisy všech obecných parametrů.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat požadovanou velikost `signature` pole typu, nastavte argument `cbSignature` na hodnotu 0 a `signature` na **hodnotu null**. Když se metoda vrátí, `pcbSignature` bude obsahovat počet bajtů vyžadovaných pro pole `signature`.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetMethodProps – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
