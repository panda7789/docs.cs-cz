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
ms.openlocfilehash: 76ad1c0ac421f05cf30f6d3d1f3e65848796a0c7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378701"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="34cd0-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="34cd0-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="34cd0-103">Získá aktuální objekt [ICorDebugManagedCallback3 –:: CustomNotification –](icordebugmanagedcallback3-customnotification-method.md) v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="34cd0-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="34cd0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34cd0-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="34cd0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34cd0-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="34cd0-106">mimo Ukazatel na aktuální `ICorDebugManagedCallback3::CustomNotification` objekt v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="34cd0-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="34cd0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34cd0-107">Remarks</span></span>

<span data-ttu-id="34cd0-108">Hodnota má hodnotu `ppNotificationObject` null, pokud metoda není volána v rámci `ICorDebugManagedCallback3::CustomNotification` zpětného volání, nebo pokud neexistuje aktuální objekt oznámení.</span><span class="sxs-lookup"><span data-stu-id="34cd0-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="34cd0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34cd0-109">Requirements</span></span>

<span data-ttu-id="34cd0-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34cd0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="34cd0-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="34cd0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="34cd0-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="34cd0-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="34cd0-113">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34cd0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="34cd0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="34cd0-114">See also</span></span>

- [<span data-ttu-id="34cd0-115">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34cd0-115">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="34cd0-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34cd0-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="34cd0-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="34cd0-117">Debugging</span></span>](index.md)
