---
title: 'IXCLRDataModule:: Request – metoda'
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
ms.openlocfilehash: 44ee4fc7fc2368b65f6f2fffe6ac239beddc6293
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395272"
---
# <a name="ixclrdatamodulerequest-method"></a>IXCLRDataModule:: Request – metoda

Žádosti o naplnění vyrovnávací paměti dané daty modulu.

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
pro Typ požadavku, který se má odeslat

`inBufferSize`\
[in] velikost vstupní vyrovnávací paměti, která má být předána.

`inBuffer`\
[in, size_is (inBufferSize)] Ukazatel vyrovnávací paměti pro nezpracovaná data, která se mají v žádosti odeslat.

`outBufferSize`\
pro Velikost výstupní vyrovnávací paměti.

`outBuffer`\
[out, size_is (outBufferSize)] Ukazatel vyrovnávací paměti, který se použije k uložení odpovědi na žádost

## <a name="remarks"></a>Poznámky

Poskytnutá metoda je součástí `IXCLRDataModule` rozhraní a odpovídá slotu 37th tabulky virtuálních metod.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).
**Hlavička:** Žádná **Knihovna:** žádné **.NET Framework verze:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Viz také

- [Ladění](index.md)
- [IXCLRDataModule – rozhraní](ixclrdatamodule-interface.md)
