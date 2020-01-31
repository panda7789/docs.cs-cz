---
title: 'ICorDebugCode4:: EnumerateVariableHomes – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: ca452b230e2508f2d69c9aa38f274db506f3a906
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784092"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="dd9dd-102">ICorDebugCode4:: EnumerateVariableHomes – metoda</span><span class="sxs-lookup"><span data-stu-id="dd9dd-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="dd9dd-103">Získá enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="dd9dd-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd9dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd9dd-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd9dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd9dd-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="dd9dd-106">Ukazatel na adresu objektu rozhraní [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) , který je enumerátorem pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="dd9dd-106">A pointer to the address of an [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd9dd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd9dd-107">Remarks</span></span>  
 <span data-ttu-id="dd9dd-108">Objekt rozhraní [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) je standardní enumerátor odvozený z rozhraní ICorDebugEnum, které umožňuje vytvořit výčet objektů [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="dd9dd-108">The [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="dd9dd-109">Kolekce může obsahovat více objektů [ICorDebugVariableHome](icordebugvariablehome-interface.md) pro stejný slot nebo index argumentu, pokud mají různé domy v různých fázích funkce.</span><span class="sxs-lookup"><span data-stu-id="dd9dd-109">The collection may include multiple [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd9dd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd9dd-110">Requirements</span></span>  
 <span data-ttu-id="dd9dd-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd9dd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd9dd-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dd9dd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd9dd-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dd9dd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd9dd-114">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd9dd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd9dd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd9dd-115">See also</span></span>

- [<span data-ttu-id="dd9dd-116">ICorDebugCode4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd9dd-116">ICorDebugCode4 Interface</span></span>](icordebugcode4-interface.md)
- [<span data-ttu-id="dd9dd-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dd9dd-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
