---
title: 'ICorDebugInstanceFieldSymbol:: GetOffset – metoda'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 3886e29a1c2fd44fbe50d1eef722f99da7abdbe5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139005"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="b1ba1-102">ICorDebugInstanceFieldSymbol:: GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="b1ba1-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="b1ba1-103">Získá posun v bajtech tohoto pole instance v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="b1ba1-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ba1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1ba1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1ba1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1ba1-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="b1ba1-106">Ukazatel na počet bajtů, které jsou tímto polem instance posunuty v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="b1ba1-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1ba1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1ba1-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1ba1-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b1ba1-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1ba1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1ba1-109">Requirements</span></span>  
 <span data-ttu-id="b1ba1-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1ba1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1ba1-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1ba1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1ba1-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b1ba1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1ba1-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1ba1-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ba1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1ba1-114">See also</span></span>

- [<span data-ttu-id="b1ba1-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1ba1-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="b1ba1-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b1ba1-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
