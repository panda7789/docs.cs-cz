---
title: ICorDebugVariableHome::GetArgumentIndex – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2457dff3063e47f1fb9d040caac1bc08441e1739
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366826"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="32244-102">ICorDebugVariableHome::GetArgumentIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="32244-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="32244-103">Získá index argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="32244-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="32244-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32244-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="32244-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32244-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="32244-106">[out] Ukazatel na index argumentu.</span><span class="sxs-lookup"><span data-stu-id="32244-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="32244-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="32244-107">Return Value</span></span>

<span data-ttu-id="32244-108">Metoda vrátí následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="32244-108">The method returns the following values.</span></span>

|<span data-ttu-id="32244-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="32244-109">Value</span></span>|<span data-ttu-id="32244-110">Popis</span><span class="sxs-lookup"><span data-stu-id="32244-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="32244-111">Volání metody, které vrátí index platný argument.</span><span class="sxs-lookup"><span data-stu-id="32244-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="32244-112">Aktuální [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance představuje místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="32244-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="32244-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32244-113">Remarks</span></span>

<span data-ttu-id="32244-114">Argument index je možné načíst metadata pro tento argument.</span><span class="sxs-lookup"><span data-stu-id="32244-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="32244-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32244-115">Requirements</span></span>

<span data-ttu-id="32244-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32244-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="32244-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32244-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="32244-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32244-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="32244-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32244-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="32244-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32244-120">See also</span></span>

- [<span data-ttu-id="32244-121">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32244-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
