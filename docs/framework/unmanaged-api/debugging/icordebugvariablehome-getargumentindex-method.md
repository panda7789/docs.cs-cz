---
title: 'ICorDebugVariableHome:: GetArgumentIndex – metoda'
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
ms.openlocfilehash: 27a676fd1d2d7903943e44f8a7201b88af4fba89
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396996"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="298bf-102">ICorDebugVariableHome:: GetArgumentIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="298bf-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="298bf-103">Získá index argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="298bf-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="298bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="298bf-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="298bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="298bf-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="298bf-106">mimo Ukazatel na index argumentu.</span><span class="sxs-lookup"><span data-stu-id="298bf-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="298bf-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="298bf-107">Return Value</span></span>

<span data-ttu-id="298bf-108">Metoda vrací následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="298bf-108">The method returns the following values.</span></span>

|<span data-ttu-id="298bf-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="298bf-109">Value</span></span>|<span data-ttu-id="298bf-110">Popis</span><span class="sxs-lookup"><span data-stu-id="298bf-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="298bf-111">Volání metody vrátilo platný index argumentu.</span><span class="sxs-lookup"><span data-stu-id="298bf-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="298bf-112">Aktuální instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) představuje místní proměnnou.</span><span class="sxs-lookup"><span data-stu-id="298bf-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="298bf-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="298bf-113">Remarks</span></span>

<span data-ttu-id="298bf-114">Index argumentu lze použít k načtení metadat pro tento argument.</span><span class="sxs-lookup"><span data-stu-id="298bf-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="298bf-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="298bf-115">Requirements</span></span>

<span data-ttu-id="298bf-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="298bf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="298bf-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="298bf-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="298bf-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="298bf-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="298bf-119">**Verze .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="298bf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="298bf-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="298bf-120">See also</span></span>

- [<span data-ttu-id="298bf-121">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="298bf-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
