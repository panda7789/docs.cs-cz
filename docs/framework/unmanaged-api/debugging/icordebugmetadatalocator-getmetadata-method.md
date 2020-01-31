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
ms.openlocfilehash: 43f3c1dd866b98bff51b375a11e28727e41d3ead
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793054"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData – metoda
Požádá ladicí program, aby vrátil úplnou cestu k modulu, jehož metadata jsou potřeba k dokončení operace, kterou ladicí program požaduje.  
  
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
 pro Řetězec zakončený hodnotou null, který představuje úplnou cestu k souboru. Pokud úplná cesta není k dispozici, název a Přípona souboru (*filename*. *rozšíření*).  
  
 `dwImageTimeStamp`  
 pro Časové razítko z hlaviček souboru v PE bitové kopie. Tento parametr může být potenciálně použit pro vyhledávání serveru symbolů ([SymSrv](/windows/desktop/debug/using-symsrv)).  
  
 `dwImageSize`  
 pro Velikost obrázku z hlavičky souboru PE. Tento parametr může být potenciálně použit pro SymSrv vyhledávání.  
  
 `cchPathBuffer`  
 pro Počet znaků v `wszPathBuffer`.  
  
 `pcchPathBuffer`  
 mimo Počet `WCHAR`s zapsaných do `wszPathBuffer`  
  
 Pokud metoda vrátí E_NOT_SUFFICIENT_BUFFER, obsahuje počet `WCHAR`potřebných k uložení cesty.  
  
 `wszPathBuffer`  
 mimo Ukazatel na vyrovnávací paměť, do které bude ladicí program kopírovat úplnou cestu k souboru, který obsahuje požadovaná metadata.  
  
 Příznak `ofReadOnly` z výčtu [CorOpenFlags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) se používá k vyžádání přístupu k metadatům v tomto souboru jen pro čtení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody. Všechny ostatní chyby HRESULT neznamenají, že soubor nelze načíst.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena. `wszPathBuffer` obsahuje úplnou cestu k souboru a je zakončený hodnotou null.|  
|E_NOT_SUFFICIENT_BUFFER|Aktuální velikost `wszPathBuffer` není dostačující pro uložení úplné cesty. V takovém případě `pcchPathBuffer` obsahuje potřebný počet `WCHAR`, včetně ukončujícího znaku null a `GetMetaData` je volána podruhé s požadovanou velikostí vyrovnávací paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `wszImagePath` obsahuje úplnou cestu pro modul z výpisu paměti, určuje cestu z počítače, ve kterém byl výpis paměti shromážděn. Soubor pravděpodobně v tomto umístění neexistuje nebo v cestě je uložen nesprávný soubor se stejným názvem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugThread4 – rozhraní](icordebugthread4-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
