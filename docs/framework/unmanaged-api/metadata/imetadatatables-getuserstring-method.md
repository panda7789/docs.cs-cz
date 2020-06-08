---
title: IMetaDataTables::GetUserString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
ms.openlocfilehash: 21ce66722e069573b651ada950b64ef6d97220fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501141"
---
# <a name="imetadatatablesgetuserstring-method"></a>IMetaDataTables::GetUserString – metoda

Získá pevně zakódovaný řetězec na zadaném indexu ve sloupci řetězce v aktuálním oboru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a>Parametry

`ixUserString`\
pro Hodnota indexu, ze které budou načteny pevně zakódovaný řetězec.

`pcbData`\
mimo Ukazatel na velikost `ppData` .

`ppData`\
mimo Ukazatel na ukazatel na vrácený řetězec.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** Cor. h

**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.

**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [IMetaDataTables – rozhraní](imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](imetadatatables2-interface.md)
