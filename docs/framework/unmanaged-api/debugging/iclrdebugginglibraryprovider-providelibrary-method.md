---
title: ICLRDebuggingLibraryProvider::ProvideLibrary – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
ms.openlocfilehash: 7bbb49dc6ee9b1d29dd61ccdcfdacb62740133ed
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860275"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary – metoda

Získá rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje umístění a načtení knihoven ladění pro Common Language Runtime (CLR) pro konkrétní verzi na vyžádání.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a>Parametry

`pwszFilename` \
pro Název požadovaného modulu.

`dwTimestamp` \
pro Časové razítko data uložené v hlavičce souboru. COFF v hlavičce souborů PE.

`pLibraryProvider` \
pro `SizeOfImage` Pole uložené v hlavičce volitelného souboru PE souborů.

`hModule` \
mimo Popisovač pro požadovaný modul.

## <a name="return-value"></a>Návratová hodnota

Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.

|HRESULT|Popis|
|-------------|-----------------|
|S_OK|Metoda byla úspěšně dokončena.|

## <a name="exceptions"></a>Výjimky

## <a name="remarks"></a>Poznámky

`ProvideLibrary`umožňuje ladicímu programu poskytovat moduly, které jsou potřeba pro ladění specifických souborů CLR, jako je mscordbi. dll a Mscordacwks. dll. Obsluha modulu musí zůstat platná, dokud volání metody [ICLRDebugging:: CanUnloadNow –](iclrdebugging-canunloadnow-method.md) značí, že mohou být uvolněny, v takovém případě je povinností volajícího uvolnit obslužné rutiny.

Ladicí program může použít všechny dostupné prostředky k vyhledání nebo zpřístupnění modulu ladění.

> [!IMPORTANT]
> Tato funkce umožňuje volajícímu rozhraní API poskytovat moduly, které obsahují spustitelný soubor a potenciálně škodlivý kód. Jako bezpečnostní opatření by volající neměl použít `ProvideLibrary` k distribuci kódu, který není ochotn sám spustit.
>
> Pokud se závažná chyba zabezpečení zjistí v již vydané knihovně, například mscordbi. dll nebo Mscordacwks. dll, překrytí se dá opravit, aby se rozpoznaly chybné verze souborů. Překrytí pak může vydávat požadavky na opravené verze souborů a zamítnout chybné verze, pokud jsou k dispozici v reakci na libovolný požadavek. K tomu může dojít pouze v případě, že uživatel převedl opravu na novou verzi překrytí. Neopravené verze zůstanou v ohrožení.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** CorDebug. idl, CorDebug. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
