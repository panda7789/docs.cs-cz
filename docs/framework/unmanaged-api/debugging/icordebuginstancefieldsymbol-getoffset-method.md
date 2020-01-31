---
title: 'ICorDebugInstanceFieldSymbol:: GetOffset – metoda'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: f7c13d397b39698bdf1a22f14820680e1fd0a25f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782290"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="e2c53-102">ICorDebugInstanceFieldSymbol:: GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="e2c53-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="e2c53-103">Získá posun v bajtech tohoto pole instance v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="e2c53-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2c53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2c53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2c53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2c53-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="e2c53-106">Ukazatel na počet bajtů, které jsou tímto polem instance posunuty v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="e2c53-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2c53-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2c53-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2c53-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e2c53-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2c53-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2c53-109">Requirements</span></span>  
 <span data-ttu-id="e2c53-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2c53-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2c53-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e2c53-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2c53-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e2c53-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2c53-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2c53-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2c53-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2c53-114">See also</span></span>

- [<span data-ttu-id="e2c53-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2c53-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="e2c53-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e2c53-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
