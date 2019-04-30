---
title: EnumImportTypes – metoda
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d0aefea7345bc3bf37bdb8d13cb2cda19cfe527
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789952"
---
# <a name="enumimporttypes-method"></a>EnumImportTypes – metoda

Vytvoří výčet jednotlivých typů v každém oboru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a>Parametry

`hEnum`\
Popisovač pro enumerátor.

`dwMax`\
Maximální počet typů, který chcete načíst.

`aTypeDefs`\
Přijímá typ tokeny, která nepřekročí `dwMax`.

`pdwCount`\
Přijímá skutečný počet typů v `aTypeDefs`.

## <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK.

## <a name="requirements"></a>Požadavky

Vyžaduje alink.h

## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)