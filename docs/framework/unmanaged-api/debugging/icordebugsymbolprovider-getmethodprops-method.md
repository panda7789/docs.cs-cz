---
title: 'ICorDebugSymbolProvider:: Getmethodprops – – metoda'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 58642d0a9b1cfe1fd969f39fa7e5ab22a8dbfa05
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791583"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider:: Getmethodprops – – metoda
Vrátí informace o vlastnostech metody, jako je token metadat metody a informace o jeho obecných parametrech, s ohledem na relativní virtuální adresu (RVA) v této metodě.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `codeRVA`  
 pro Relativní virtuální adresa v metodě, o které se mají načíst informace  
  
 `pMethodToken`  
 mimo Ukazatel na token metadat metody.  
  
 `pcGenericParams`  
 mimo Ukazatel na počet obecných parametrů přidružených k této metodě.  
  
 `cbSignature`  
 pro Velikost pole `signature`. Viz část poznámky.  
  
 `pcbSignature`  
 mimo Ukazatel na velikost vráceného pole `signature`.  
  
 `signature`  
 mimo Vyrovnávací paměť, která obsahuje token TypeSpec podpisy všech obecných parametrů.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat požadovanou velikost `signature` pole metody, nastavte argument `cbSignature` na hodnotu 0 a `signature` na **hodnotu null**. Když se metoda vrátí, `pcbSignature` bude obsahovat počet bajtů vyžadovaných pro pole `signature`.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetTypeProps – metoda](icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider – rozhraní](icordebugsymbolprovider-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
