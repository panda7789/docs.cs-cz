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
ms.openlocfilehash: d0c283232ff8eca1af9f3ff4448fb7f4c81d554f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789038"
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
pro Pole `SizeOfImage` uložené v hlavičce volitelného souboru PE souborů.

`hModule` \
mimo Popisovač pro požadovaný modul.

## <a name="return-value"></a>Návratová hodnota

Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.

|HRESULT|Popis|
|-------------|-----------------|
|S_OK|Metoda byla úspěšně dokončena.|

## <a name="exceptions"></a>Výjimky

## <a name="remarks"></a>Poznámky

`ProvideLibrary` umožňuje ladicímu programu poskytovat moduly, které jsou potřeba pro ladění specifických souborů CLR, jako je mscordbi. dll a Mscordacwks. dll. Obsluha modulu musí zůstat platná, dokud volání metody [ICLRDebugging:: CanUnloadNow –](iclrdebugging-canunloadnow-method.md) značí, že mohou být uvolněny, v takovém případě je povinností volajícího uvolnit obslužné rutiny.

Ladicí program může použít všechny dostupné prostředky k vyhledání nebo zpřístupnění modulu ladění.

> [!IMPORTANT]
> Tato funkce umožňuje volajícímu rozhraní API poskytovat moduly, které obsahují spustitelný soubor a potenciálně škodlivý kód. Jako bezpečnostní opatření by volající neměl používat `ProvideLibrary` k distribuci kódu, který není ochotn sám spustit.
>
> Pokud se závažná chyba zabezpečení zjistí v již vydané knihovně, například mscordbi. dll nebo Mscordacwks. dll, překrytí se dá opravit, aby se rozpoznaly chybné verze souborů. Překrytí pak může vydávat požadavky na opravené verze souborů a zamítnout chybné verze, pokud jsou k dispozici v reakci na libovolný požadavek. K tomu může dojít pouze v případě, že uživatel převedl opravu na novou verzi překrytí. Neopravené verze zůstanou v ohrožení.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlavička:** CorDebug. idl, CorDebug. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
