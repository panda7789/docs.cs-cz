---
title: ICorDebugProcess5::GetArrayLayout – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
ms.openlocfilehash: ea7630efedb7b667dc58174eda0cb98d9f382cfc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792389"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="86103-102">ICorDebugProcess5::GetArrayLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="86103-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="86103-103">Poskytuje informace o rozložení typů polí.</span><span class="sxs-lookup"><span data-stu-id="86103-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86103-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86103-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86103-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86103-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="86103-106">pro [COR_TYPEID](cor-typeid-structure.md) token, který určuje pole, jehož rozložení se požaduje.</span><span class="sxs-lookup"><span data-stu-id="86103-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="86103-107">mimo Ukazatel na strukturu [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) , která obsahuje informace o rozložení pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="86103-107">[out] A pointer to a [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86103-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86103-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86103-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86103-109">Requirements</span></span>  
 <span data-ttu-id="86103-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86103-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86103-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86103-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86103-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="86103-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86103-113">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86103-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86103-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86103-114">See also</span></span>

- [<span data-ttu-id="86103-115">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86103-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="86103-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="86103-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
