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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4eaf426bc9c933de1d4b774928f2b0a54dfb472
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636957"
---
# <a name="imetadatatablesgetuserstring-method"></a>IMetaDataTables::GetUserString – metoda

Získá řetězec pevně zakódované v zadaném indexu ve sloupci řetězce v aktuálním oboru.

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
[in] Hodnota indexu, ze kterého se budou načítat pevně zakódované řetězce.

`pcbData`\
[out] Ukazatel na velikost `ppData`.

`ppData`\
[out] Ukazatel na ukazatel na vráceného řetězce.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** Cor.h

**Knihovna:** Použít jako prostředek v MsCorEE.dll

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [IMetaDataTables – rozhraní](imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](imetadatatables2-interface.md)
