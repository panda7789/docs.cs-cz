---
title: IXCLRDataModule::Request – metoda
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 755063ca6da29a2e4733dd653306192ac0434ec0
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610597"
---
# <a name="ixclrdatamodulerequest-method"></a>IXCLRDataModule::Request – metoda

Požadavky k naplnění vyrovnávací paměť přidělená s daty modulu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a>Parametry

`reqCode`\
[in] Typ k odeslání žádosti.

`inBufferSize`\
[in] velikost vstupní vyrovnávací paměť musí být předány.

`inBuffer`\
[in, size_is(inBufferSize)] Ukazatele na vyrovnávací paměti pro nezpracovaná data se odešle požadavek.

`outBufferSize`\
[in] Velikost výstupní vyrovnávací paměť.

`outBuffer`\
[out, size_is(outBufferSize)] Ukazatel vyrovnávací paměť pro ukládání odpovědi na požadavek.

## <a name="remarks"></a>Poznámky

Zadaná metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 36 pozice tabulce virtuální metody.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).
**Záhlaví:** Žádný **knihovny:** Žádný **verze rozhraní .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
- [IXCLRDataModule Interface](ixclrdatamodule-interface.md)