---
title: ICorDebugMetaDataLocator::GetMetaData – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b761d31e640063e11c1e549966bb372449fe743
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762270"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData – metoda
Dotaz vrátí úplnou cestu k modulu, jehož metadat je potřeba k dokončení operace, které ladicí program požadovaný ladicí program.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
## <a name="parameters"></a>Parametry  
 `wszImagePath`  
 [in] Řetězec zakončený hodnotou null, který představuje úplnou cestu k souboru. Pokud je úplná cesta není k dispozici, název a příponu souboru (*filename*. *rozšíření*).  
  
 `dwImageTimeStamp`  
 [in] Časové razítko ze záhlaví PE souboru obrázku. Tento parametr může potenciálně použít pro server symbolů ([SymSrv](/windows/desktop/debug/using-symsrv)) vyhledávání.  
  
 `dwImageSize`  
 [in] Velikost bitové kopie ze záhlaví PE souboru. Tento parametr lze použít potenciálně pro vyhledávání SymSrv.  
  
 `cchPathBuffer`  
 [in] Počet znak za `wszPathBuffer`.  
  
 `pcchPathBuffer`  
 [out] Počet `WCHAR`s zapsána do `wszPathBuffer`.  
  
 Pokud metoda vrátí E_NOT_SUFFICIENT_BUFFER, obsahuje počet `WCHAR`s potřebné k uložení této cesty.  
  
 `wszPathBuffer`  
 [out] Ukazatel do vyrovnávací paměti, do které ladicí program se zkopírovat úplnou cestu souboru, který obsahuje požadovaná metadata.  
  
 `ofReadOnly` Příznak z [coropenflags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčet slouží k vyžádání přístup jen pro čtení metadat z tohoto souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda. Všechny ostatní HRESULT – selhání znamenat, že soubor není retrievable.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena. `wszPathBuffer` obsahuje úplnou cestu k souboru a je zakončený hodnotou null.|  
|E_NOT_SUFFICIENT_BUFFER|Aktuální velikost `wszPathBuffer` není dostatečná k uložení úplnou cestu. V takovém případě `pcchPathBuffer` obsahuje potřebný počet `WCHAR`s, včetně ukončujícího znaku null, a `GetMetaData` se volá jednou s velikost požadované vyrovnávací paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `wszImagePath` obsahuje úplnou cestu pro modul z výpis paměti, určuje cestu z počítače, kde byl výpis paměti shromážděn. Soubor neexistuje na tomto místě nebo nesprávný soubor se stejným názvem, mohou být uloženy v cestě.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugThread4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
