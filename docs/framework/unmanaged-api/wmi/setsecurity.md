---
title: Funkce SetSecurity (nespravovaný odkaz na rozhraní API)
description: Funkce SetSecurity načte token zosobnění aktuálního vlákna.
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 809f6a95fdd6854b3a591b496877838c48d52199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176731"
---
# <a name="setsecurity-function"></a>Funkce SetSecurity

Načte token zosobnění přidružený k aktuálnímu vláknu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset,
   [out] HANDLE* pCurrentThreadToken
);
```

## <a name="parameters"></a>Parametry

`pNeedToReset`\
[out] Když funkce vrátí, obsahuje ukazatel `boolean` na a, který označuje, zda token by měl být resetován voláním [funkce ResetSecurity.](resetsecurity.md)

`token`\
[out] Když funkce vrátí, obsahuje ukazatel na popisovač tokenu zosobnění přidružené ho aktuální vlákno. Jeho hodnota `null` může být, pokud neexistuje žádný token přidružený k aktuálnívlákno.

## <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, `S_OK` vrácená hodnota je (0).

Pokud funkce selže, vrácená hodnota je nenulový kód chyby. Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo.](geterrorinfo.md)

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).

 **Záhlaví:** WMINet_Utils.idl

 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
