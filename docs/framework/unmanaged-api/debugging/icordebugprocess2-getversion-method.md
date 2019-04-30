---
title: ICorDebugProcess2::GetVersion – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 interface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07f3be81431201a4bb6011ea9b8f973061d3d101
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948864"
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="779ce-102">ICorDebugProcess2::GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="779ce-102">ICorDebugProcess2::GetVersion Method</span></span>

<span data-ttu-id="779ce-103">Získá číslo verze common language runtime (CLR), na kterém běží v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="779ce-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>

## <a name="syntax"></a><span data-ttu-id="779ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="779ce-104">Syntax</span></span>

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a><span data-ttu-id="779ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="779ce-105">Parameters</span></span>

`version`\
<span data-ttu-id="779ce-106">[out] Ukazatel na cor_version – struktura, která ukládá číslo verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="779ce-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>

## <a name="remarks"></a><span data-ttu-id="779ce-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="779ce-107">Remarks</span></span>

<span data-ttu-id="779ce-108">`GetVersion` Metoda vrátí kód chyby, pokud žádný modul runtime byl načten v procesu.</span><span class="sxs-lookup"><span data-stu-id="779ce-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>

## <a name="requirements"></a><span data-ttu-id="779ce-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="779ce-109">Requirements</span></span>

<span data-ttu-id="779ce-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="779ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="779ce-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="779ce-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="779ce-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="779ce-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="779ce-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="779ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
