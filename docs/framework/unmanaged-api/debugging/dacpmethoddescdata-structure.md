---
title: DacpMethodDescData – struktura
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
ms.openlocfilehash: d623fe862eaf5902fd89d0e512dd07f73a03246f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860814"
---
# <a name="dacpmethoddescdata-structure"></a>DacpMethodDescData – struktura

Definuje přenosovou vyrovnávací paměť pro běhové informace metody.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
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
| `bHasNativeCode`             | Určuje, zda má modul runtime pro danou instanci metody k dispozici nativní kód. |
| `bIsDynamic`                 | Určuje, zda je metoda generována dynamicky prostřednictvím zjednodušeného generování kódu.           |
| `wSlotNumber`                | Číslo pozice metody v tabulce metod.                                                   |
| `NativeCodeAddr`             | Počáteční nativní adresa metody                                                            |
| `data`                       | Ukazatel na vyrovnávací paměť použitou interně modulem runtime.                                             |
| `MethodDescPtr`              | Ukazatel na modul `MethodDesc` v modulu runtime.                                                     |
| `nativeCodeInfo`             | Ukazatel na vyrovnávací paměť použitou interně modulem runtime ke sledování metod.                            |
| `moduleInfo`                 | Ukazatel na vyrovnávací paměť použitou interně modulem runtime pro informace o modulu.                      |
| `MDToken`                    | Token přidružený k dané metodě                                                         |
| `payloadGC`                  | Ukazatel na vyrovnávací paměť pro uvolňování paměti, která se používá interně modulem runtime.                          |
| `payloadGC2`                 | Ukazatel na vyrovnávací paměť pro uvolňování paměti, která se používá interně modulem runtime.                          |
| `managedDynamicMethodObject` | Pokud je metoda dynamická, modul runtime tuto vyrovnávací paměť interně používá ke sledování informací.     |
| `requestedIP`                | Používá se k naplnění struktury na požadavek v případě, že se předává adresa nativního kódu.                    |
| `rejitDataCurrent`           | Informace o nejnovější instrumentované verzi metody.                                   |
| `rejitDataRequested`         | ReJIT informace o požadované nativní adrese.                                             |
| `cJittedRejitVersions`       | Počet pokusů, kolikrát se metoda rejitted prostřednictvím instrumentace.                           |

## <a name="remarks"></a>Poznámky

Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven. Pokud ho chcete použít, definujte strukturu, jak je uvedeno výše.

## <a name="requirements"></a>Požadavky
**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](index.md)
- [Struktury pro ladění](debugging-structures.md)
- [Běžné typy dat](../common-data-types-unmanaged-api-reference.md)
