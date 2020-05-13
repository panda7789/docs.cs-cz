---
title: ICorDebugProcess5::EnableNGENPolicy – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: fa3cbfee0359b8477f9efe88fe72837b86611bf7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212799"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="df917-102">ICorDebugProcess5::EnableNGENPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="df917-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="df917-103">Nastaví hodnotu, která určuje, jak aplikace načítá nativní bitové kopie při spuštění pod spravovaným ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="df917-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df917-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df917-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df917-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df917-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="df917-106">pro Konstanta [CorDebugNGenPolicy –](cordebugngenpolicy-enumeration.md) , která určuje, jak aplikace načítá nativní bitové kopie při spuštění pod spravovaným ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="df917-106">[in] A [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df917-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df917-107">Remarks</span></span>  
 <span data-ttu-id="df917-108">Pokud je zásada nastavená na úspěšnou, vrátí metoda `S_OK` .</span><span class="sxs-lookup"><span data-stu-id="df917-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="df917-109">Pokud `ePolicy` je mimo rozsah hodnot výčtu definovaných v [CorDebugNGenPolicy –](cordebugngenpolicy-enumeration.md), metoda vrátí `E_INVALIDARG` a volání metody nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="df917-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="df917-110">Pokud nelze aktualizovat zásady generátoru nativních bitových kopií (Ngen. exe), metoda se vrátí `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="df917-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="df917-111">`ICorDebugProcess5::EnableNGenPolicy`Metodu lze volat kdykoli během životnosti procesu.</span><span class="sxs-lookup"><span data-stu-id="df917-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="df917-112">Zásada je platná pro všechny moduly, které jsou načtené po nastavení zásad.</span><span class="sxs-lookup"><span data-stu-id="df917-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df917-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df917-113">Requirements</span></span>  
 <span data-ttu-id="df917-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df917-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df917-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df917-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df917-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="df917-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df917-117">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df917-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df917-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="df917-118">See also</span></span>

- [<span data-ttu-id="df917-119">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="df917-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="df917-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="df917-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="df917-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="df917-121">Debugging</span></span>](index.md)
