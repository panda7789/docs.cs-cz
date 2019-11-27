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
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448731"
---
# <a name="enumimporttypes-method"></a>EnumImportTypes – metoda

Vytvoří výčet každého typu v jednotlivých oborech.

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
Popisovač pro enumerátor

`dwMax`\
Maximální počet typů, které se mají načíst

`aTypeDefs`\
Přijímá tokeny typu, nepřekročí `dwMax`.

`pdwCount`\
Přijímá skutečný počet typů v `aTypeDefs`.

## <a name="return-value"></a>Návratová hodnota

Vrátí S_OK, pokud je metoda úspěšná.

## <a name="requirements"></a>Požadavky

Vyžaduje ALink. h

## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)
