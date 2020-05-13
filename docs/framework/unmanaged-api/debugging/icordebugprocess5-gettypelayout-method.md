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
ms.openlocfilehash: 861af4ba9c6f4d4bdb16abb9d4e1fd79debac59b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205579"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="431a3-102">ICorDebugProcess5::GetTypeLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="431a3-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="431a3-103">Načte informace o rozložení objektu v paměti na základě jeho identifikátoru typu.</span><span class="sxs-lookup"><span data-stu-id="431a3-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="431a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="431a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="431a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="431a3-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="431a3-106">pro Token [COR_TYPEID](cor-typeid-structure.md) , který určuje typ, jehož rozložení se požaduje.</span><span class="sxs-lookup"><span data-stu-id="431a3-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="431a3-107">mimo Ukazatel na strukturu [COR_TYPE_LAYOUT](cor-type-layout-structure.md) , která obsahuje informace o rozložení objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="431a3-107">[out] A pointer to a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="431a3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="431a3-108">Remarks</span></span>  
 <span data-ttu-id="431a3-109">`ICorDebugProcess5::GetTypeLayout`Metoda poskytuje informace o objektu na základě jeho [COR_TYPEID](cor-typeid-structure.md), který je vrácen řadou dalších metod [ICorDebugProcess5](icordebugprocess5-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="431a3-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="431a3-110">Informace jsou poskytovány [COR_TYPE_LAYOUT](cor-type-layout-structure.md) strukturou, která je naplněna metodou.</span><span class="sxs-lookup"><span data-stu-id="431a3-110">The information is provided by a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="431a3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="431a3-111">Requirements</span></span>  
 <span data-ttu-id="431a3-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="431a3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="431a3-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="431a3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="431a3-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="431a3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="431a3-115">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="431a3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="431a3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="431a3-116">See also</span></span>

- [<span data-ttu-id="431a3-117">COR_TYPE_LAYOUT – struktura</span><span class="sxs-lookup"><span data-stu-id="431a3-117">COR_TYPE_LAYOUT Structure</span></span>](cor-type-layout-structure.md)
- [<span data-ttu-id="431a3-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="431a3-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="431a3-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="431a3-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
