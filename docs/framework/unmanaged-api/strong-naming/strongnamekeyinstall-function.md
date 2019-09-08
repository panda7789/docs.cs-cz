---
title: StrongNameKeyInstall – funkce
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 353898b72f41acd0c49a43ff05e54f61b99444c4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798991"
---
# <a name="strongnamekeyinstall-function"></a>StrongNameKeyInstall – funkce

Importuje pár veřejného a privátního klíče do kontejneru.

Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameKeyInstall –](../hosting/iclrstrongname-strongnamekeyinstall-method.md) .

## <a name="syntax"></a>Syntaxe

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a>Parametry

`wszKeyContainer`\
pro Název kontejneru klíčů. `wszKeyContainer`musí být neprázdný řetězec.

`pbKeyBlob`\
pro Dvojice binárních klíčů.

`cbKeyBlob`\
pro Velikost v bajtech `pbKeyBlob`.

## <a name="return-value"></a>Návratová hodnota

`true`Po úspěšném dokončení; v opačném případě. `false`

## <a name="remarks"></a>Poznámky

Pomocí funkce [StrongNameKeyDelete –](strongnamekeydelete-function.md) odstraňte kontejner klíčů.

Pokud se `StrongNameKeyInstall` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** StrongName. h

**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll

**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Viz také:

- [StrongNameKeyInstall – metoda](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete – metoda](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
