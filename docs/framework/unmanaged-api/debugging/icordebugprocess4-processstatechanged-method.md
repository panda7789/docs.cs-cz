---
title: ICorDebugProcess4::ProcessStateChanged Method
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b77dd1277e7d23729f30d9d495c5417055a22759
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378987"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="03c51-102">ICorDebugProcess4::ProcessStateChanged Method</span><span class="sxs-lookup"><span data-stu-id="03c51-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="03c51-103">Upozorní ICorDebug kanálu, že je vzdálený ladicí program procesu pokračovat v provádění od laděného objektu.</span><span class="sxs-lookup"><span data-stu-id="03c51-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="03c51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03c51-104">Syntax</span></span>

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="03c51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03c51-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="03c51-106">[in] Člen [výčet CorDebugStateChange](cordebugstatechange-enumeration.md) popisující změnu stavu spuštění procesu.</span><span class="sxs-lookup"><span data-stu-id="03c51-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="03c51-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03c51-107">Remarks</span></span>

<span data-ttu-id="03c51-108">Zadaná metoda je součástí `ICorDebugProcess4` rozhraní a odpovídá čtvrtý pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="03c51-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="03c51-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03c51-109">Requirements</span></span>

 <span data-ttu-id="03c51-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03c51-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="03c51-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="03c51-111">**Header:** None</span></span>

 <span data-ttu-id="03c51-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="03c51-112">**Library:** None</span></span>
 
 <span data-ttu-id="03c51-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03c51-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="03c51-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03c51-114">See also</span></span>

- [<span data-ttu-id="03c51-115">ICorDebugProcess4 Interface</span><span class="sxs-lookup"><span data-stu-id="03c51-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="03c51-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="03c51-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="03c51-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="03c51-117">Debugging</span></span>](index.md)