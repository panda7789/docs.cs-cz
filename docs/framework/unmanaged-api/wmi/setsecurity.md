---
title: SetSecurity – funkce (Reference nespravovaného rozhraní API)
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
ms.openlocfilehash: 6d27779bcfc97e1c4156b8782896e83d4754491b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120215"
---
# <a name="setsecurity-function"></a>SetSecurity – funkce

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
mimo Když funkce vrátí, obsahuje ukazatel na `boolean`, který označuje, zda má být token resetován voláním funkce [ResetSecurity](resetsecurity.md) .

`token`\
mimo Když funkce vrátí, obsahuje ukazatel na popisovač zosobněného tokenu přidruženého k aktuálnímu vláknu. Jeho hodnota může být `null`, pokud k aktuálnímu vláknu není přidružen žádný token. 

## <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je `S_OK` (0).

Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby. Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Hlavička:** WMINet_Utils. idl

 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
