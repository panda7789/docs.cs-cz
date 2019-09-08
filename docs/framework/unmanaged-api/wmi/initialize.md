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
# <a name="initialize-function"></a><span data-ttu-id="8763c-103">Initialize – funkce</span><span class="sxs-lookup"><span data-stu-id="8763c-103">Initialize function</span></span>

<span data-ttu-id="8763c-104">Provede inicializaci rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="8763c-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="8763c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8763c-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="8763c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8763c-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="8763c-107">pro `true` pro indikaci, že volání QueryInterface pro objekty WMI jsou povolena; `false` v opačném případě.</span><span class="sxs-lookup"><span data-stu-id="8763c-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="8763c-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8763c-108">Return value</span></span>

<span data-ttu-id="8763c-109">Funkce vždycky vrátí `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="8763c-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="8763c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8763c-110">Requirements</span></span>

<span data-ttu-id="8763c-111">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8763c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="8763c-112">**Hlaviček** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="8763c-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="8763c-113">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8763c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8763c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8763c-114">See also</span></span>

- [<span data-ttu-id="8763c-115">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="8763c-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
