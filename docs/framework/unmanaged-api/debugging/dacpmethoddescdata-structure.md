---
title: Struktura DacpMethodDescData
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: e9037fc035693e079e2471ad37263108656b8c01
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828527"
---
# <a name="dacpmethoddescdata-structure"></a>Struktura DacpMethodDescData

Definuje přenos vyrovnávací paměť pro informace o modulu runtime metody.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a>Členové

| Člen                       | Popis                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | Uvádí, zda modul runtime má nativní kód je k dispozici pro danou instanci metody. |
| `bIsDynamic`                 | Označuje, pokud je metoda dynamicky generované prostřednictvím generování lehký kód.           |
| `wSlotNumber`                | Číslo pozice metody v tabulce – metoda                                                   |
| `NativeCodeAddr`             | Počáteční adresa nativní metody.                                                            |
| `data`                       | Ukazatel do vyrovnávací paměti interně modulem runtime.                                             |
| `MethodDescPtr`              | Ukazatel `MethodDesc` v modulu runtime.                                                     |
| `nativeCodeInfo`             | Ukazatel do vyrovnávací paměti modulem runtime interně používá ke sledování metody.                            |
| `moduleInfo`                 | Ukazatel do vyrovnávací paměti interně modulem runtime pro informace o modulu.                      |
| `MDToken`                    | Token přidružený k dané metody.                                                         |
| `payloadGC`                  | Ukazatel do vyrovnávací paměti, uvolňování paměti kolekce interně modulem runtime.                          |
| `payloadGC2`                 | Ukazatel do vyrovnávací paměti, uvolňování paměti kolekce interně modulem runtime.                          |
| `managedDynamicMethodObject` | Pokud je dynamická metoda, modul runtime této vyrovnávací paměti interně používá pro informace o sledování.     |
| `requestedIP`                | Použít k naplnění struktura každý požadavek při adresu nativní kód.                    |
| `rejitDataCurrent`           | Informace o instrumentovanou verzí metody.                                   |
| `rejitDataRequested`         | Informace o Rejit pro požadovanou nativní adresu.                                             |
| `cJittedRejitVersions`       | Počet pokusů, které metoda byla rejitted prostřednictvím instrumentace.                           |


## <a name="remarks"></a>Poznámky

Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven. Pro použití je třeba definujte strukturu jak je uvedeno výše.

## <a name="requirements"></a>Požadavky
**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádná  
**Knihovna:** Žádná  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Běžné typy dat](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
