---
title: StrongNameKeyDelete – funkce
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
ms.openlocfilehash: d37f990241ae704abef55d863da0f40a31284837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141596"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete – funkce

Odstraní zadaný kontejner klíčů.

Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameKeyDelete –](../hosting/iclrstrongname-strongnamekeydelete-method.md) .

## <a name="syntax"></a>Syntaxe

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>Parametry

`wszKeyContainer`\
pro Název kontejneru klíčů, který se má odstranit

## <a name="return-value"></a>Návratová hodnota

`true` po úspěšném dokončení; v opačném případě `false`.

## <a name="remarks"></a>Poznámky

Pomocí funkce [StrongNameKeyInstall –](strongnamekeyinstall-function.md) importujte pár veřejného a privátního klíče do kontejneru.

Pokud se funkce `StrongNameKeyDelete` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** StrongName. h

**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll

**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Viz také:

- [StrongNameKeyDelete – metoda](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall – metoda](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
