---
title: ICorDebugSymbolProvider::GetMethodProps – metoda
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f6971c7991f5e54973d96d9b3f662b54be564d9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771331"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider::GetMethodProps – metoda
Vrátí informace o vlastnostech metody, jako je například token metadat a informace o obecných parametrů, metody-li zadána relativní virtuální adresu (RVA) v této metodě.  
  
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
 [in] Relativní virtuální adresu v metodě o tom, které má být načtena informace.  
  
 `pMethodToken`  
 [out] Ukazatel na metody token metadat.  
  
 `pcGenericParams`  
 [out] Ukazatel na počet obecných parametrů, které jsou přidružené k této metodě.  
  
 `cbSignature`  
 [in] Velikost `signature` pole. V části poznámky.  
  
 `pcbSignature`  
 [out] Ukazatel na velikost vráceného `signature` pole.  
  
 `signature`  
 [out] Vyrovnávací paměti, který obsahuje token typespec podpisy všechny obecné parametry.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat požadovaná velikost metody `signature` pole, nastavte `cbSignature` argumentu na hodnotu 0 a `signature` k **null**. Po návratu metody `pcbSignature` bude obsahovat počet bajtů potřebných pro `signature` pole.  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetTypeProps – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
