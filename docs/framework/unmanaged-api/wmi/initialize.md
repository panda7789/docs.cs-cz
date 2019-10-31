---
title: Initialize – funkce (Reference nespravovaného rozhraní API)
description: Funkce Initialize provádí inicializaci rozhraní WMI.
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b1f96b6285911b12d72ac136127d736b75d44023
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127395"
---
# <a name="initialize-function"></a>Initialize – funkce

Provede inicializaci rozhraní WMI.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a>Parametry

`bAllowIManagementObjectQI`

[in] `true` pro indikaci, že volání QueryInterface pro objekty WMI jsou povolena; `false` jinak.

## <a name="return-value"></a>Návratová hodnota

Funkce vždycky vrátí `S_OK` (0).

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** WMINet_Utils. def

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
