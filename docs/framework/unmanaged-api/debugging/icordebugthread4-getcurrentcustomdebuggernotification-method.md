---
title: ICorDebugThread4::GetCurrentCustomDebuggerNotification – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
ms.openlocfilehash: a8a377074ca1005ad8089dfd8e2a6a464bb86f60
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791356"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="fea94-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="fea94-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="fea94-103">Získá aktuální objekt [ICorDebugManagedCallback3 –:: CustomNotification –](icordebugmanagedcallback3-customnotification-method.md) v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="fea94-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="fea94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fea94-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="fea94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fea94-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="fea94-106">mimo Ukazatel na aktuální objekt `ICorDebugManagedCallback3::CustomNotification` v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="fea94-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="fea94-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fea94-107">Remarks</span></span>

<span data-ttu-id="fea94-108">Hodnota `ppNotificationObject` je null, pokud metoda není volána v rámci `ICorDebugManagedCallback3::CustomNotification` zpětného volání, nebo pokud neexistuje aktuální objekt oznámení.</span><span class="sxs-lookup"><span data-stu-id="fea94-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="fea94-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fea94-109">Requirements</span></span>

<span data-ttu-id="fea94-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fea94-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="fea94-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fea94-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="fea94-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fea94-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="fea94-113">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fea94-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fea94-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fea94-114">See also</span></span>

- [<span data-ttu-id="fea94-115">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fea94-115">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="fea94-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fea94-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fea94-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="fea94-117">Debugging</span></span>](index.md)
