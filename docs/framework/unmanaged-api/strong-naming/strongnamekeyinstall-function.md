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
ms.openlocfilehash: 6b3fc69b2edf611383402b13555cf33be10dbad3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000386"
---
# <a name="strongnamekeyinstall-function"></a>StrongNameKeyInstall – funkce

Importuje pár veřejného a privátního klíče do kontejneru.

Tato funkce je zastaralá. Použití [iclrstrongname::strongnamekeyinstall –](../hosting/iclrstrongname-strongnamekeyinstall-method.md) metoda místo.

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
[in] Název kontejneru klíčů. `wszKeyContainer` musí být neprázdný řetězec.

`pbKeyBlob`\
[in] Binární pár klíčů.

`cbKeyBlob`\
[in] Velikost v bajtech, z `pbKeyBlob`.

## <a name="return-value"></a>Návratová hodnota

`true` Při úspěšném dokončení; v opačném případě `false`.

## <a name="remarks"></a>Poznámky

Použití [strongnamekeydelete –](strongnamekeydelete-function.md) funkce pro odstranění kontejneru klíčů.

Pokud `StrongNameKeyInstall` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** StrongName.h

**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Viz také:

- [StrongNameKeyInstall – metoda](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete – metoda](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)