---
title: 'ICorDebugSymbolProvider:: GetTypeProps – metoda'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: 5fa091eaf2cf93b0c645effeec3c959d42665fc9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791546"
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

- [GetMethodProps – metoda](icordebugsymbolprovider-getmethodprops-method.md)
- [ICorDebugSymbolProvider – rozhraní](icordebugsymbolprovider-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
