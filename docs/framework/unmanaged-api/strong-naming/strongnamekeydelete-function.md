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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17d35193f69966e02ac5e483924fcb3ee2e06758
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799029"
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

`true`Po úspěšném dokončení; v opačném případě. `false`

## <a name="remarks"></a>Poznámky

Pomocí funkce [StrongNameKeyInstall –](strongnamekeyinstall-function.md) importujte pár veřejného a privátního klíče do kontejneru.

Pokud se `StrongNameKeyDelete` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** StrongName. h

**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll

**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Viz také:

- [StrongNameKeyDelete – metoda](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall – metoda](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
