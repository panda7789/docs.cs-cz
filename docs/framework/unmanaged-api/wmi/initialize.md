---
title: Initialize – funkce (referenční dokumentace nespravovaného rozhraní API)
description: Inicializační funkci provádí inicializace rozhraní WMI.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c71b2b6d6f102d19d30d480ee9bafcac3c204be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049294"
---
# <a name="initialize-function"></a>Initialize – funkce

Provede inicializaci služby WMI.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a>Parametry

`bAllowIManagementObjectQI`

[in] `true` k označení, že volání QueryInterface u objektů WMI jsou povoleny. `false` jinak.

## <a name="return-value"></a>Návratová hodnota

Funkce vždy vrátí `S_OK` (0).

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** WMINet_Utils.def

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
