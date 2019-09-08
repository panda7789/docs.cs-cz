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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bc3688b30180bdcde0a87027955a789de749f90
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798438"
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

pro `true` pro indikaci, že volání QueryInterface pro objekty WMI jsou povolena; `false` v opačném případě.

## <a name="return-value"></a>Návratová hodnota

Funkce vždycky vrátí `S_OK` (0).

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** WMINet_Utils.def

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
