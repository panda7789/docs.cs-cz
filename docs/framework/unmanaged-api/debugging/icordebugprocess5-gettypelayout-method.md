---
title: ICorDebugProcess5::GetTypeLayout – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
ms.openlocfilehash: 306d881c05c2fcdb15a53a439bfce6eff3afffa8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792316"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="97548-102">ICorDebugProcess5::GetTypeLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="97548-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="97548-103">Načte informace o rozložení objektu v paměti na základě jeho identifikátoru typu.</span><span class="sxs-lookup"><span data-stu-id="97548-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97548-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97548-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97548-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97548-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="97548-106">pro Token [COR_TYPEID](cor-typeid-structure.md) , který určuje typ, jehož rozložení se požaduje.</span><span class="sxs-lookup"><span data-stu-id="97548-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="97548-107">mimo Ukazatel na strukturu [COR_TYPE_LAYOUT](cor-type-layout-structure.md) , která obsahuje informace o rozložení objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="97548-107">[out] A pointer to a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97548-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97548-108">Remarks</span></span>  
 <span data-ttu-id="97548-109">Metoda `ICorDebugProcess5::GetTypeLayout` poskytuje informace o objektu na základě jeho [COR_TYPEID](cor-typeid-structure.md), který je vrácen řadou dalších metod [ICorDebugProcess5](icordebugprocess5-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="97548-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="97548-110">Informace jsou poskytovány [COR_TYPE_LAYOUT](cor-type-layout-structure.md) strukturou, která je naplněna metodou.</span><span class="sxs-lookup"><span data-stu-id="97548-110">The information is provided by a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97548-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97548-111">Requirements</span></span>  
 <span data-ttu-id="97548-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97548-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97548-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="97548-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97548-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="97548-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97548-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97548-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97548-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97548-116">See also</span></span>

- [<span data-ttu-id="97548-117">COR_TYPE_LAYOUT – struktura</span><span class="sxs-lookup"><span data-stu-id="97548-117">COR_TYPE_LAYOUT Structure</span></span>](cor-type-layout-structure.md)
- [<span data-ttu-id="97548-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97548-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="97548-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="97548-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
