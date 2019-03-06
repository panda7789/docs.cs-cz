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
ms.openlocfilehash: dfc785a48d0cdf1cf2fdc0245a27b8ef35fd2d81
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364512"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete – funkce

Odstraní zadaný kontejner klíče.

Tato funkce je zastaralá. Použití [iclrstrongname::strongnamekeydelete –](../hosting/iclrstrongname-strongnamekeydelete-method.md) metoda místo.

## <a name="syntax"></a>Syntaxe

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>Parametry

`wszKeyContainer`\
[in] Název kontejneru klíčů pro odstranění.

## <a name="return-value"></a>Návratová hodnota

`true` Při úspěšném dokončení; v opačném případě `false`.

## <a name="remarks"></a>Poznámky

Použití [strongnamekeyinstall –](strongnamekeyinstall-function.md) k importu pár veřejného a privátního klíče do kontejneru.

Pokud `StrongNameKeyDelete` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** StrongName.h

**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Viz také:

- [StrongNameKeyDelete – metoda](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall – metoda](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)