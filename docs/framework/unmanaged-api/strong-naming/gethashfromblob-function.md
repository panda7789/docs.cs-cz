---
title: GetHashFromBlob – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59b4df08157ce14a58393e54b671e8f41b8998ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799229"
---
# <a name="gethashfromblob-function"></a>GetHashFromBlob – funkce

Načte hodnotu hash sestavení v zadané adrese paměti pomocí zadaného algoritmu hash.

Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: GetHashFromBlob –](../hosting/iclrstrongname-gethashfromblob-method.md) .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a>Parametry

`pbBlob`\
pro Ukazatel na adresu bloku paměti, který má být použit jako hash.

`cchBlob`\
pro Délka bloku paměti (v bajtech).

`piHashAlg`\
[in, out] Konstanta, která určuje algoritmus hash. Pro výchozí algoritmus použijte nulu.

`pbHash`\
mimo Vrácená vyrovnávací paměť hash.

`cchHash`\
pro Požadovaná maximální velikost `pbHash`.

`pchHash`\
mimo Velikost vracené `pbHash`velikosti (v bajtech)

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** StrongName. h

**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll

**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Viz také:

- [GetHashFromBlob – metoda](../hosting/iclrstrongname-gethashfromblob-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
