---
title: 'ICorDebugInstanceFieldSymbol:: GetOffset – metoda'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 7d553c1a446e06f34c20da18c0edfe6773cfb597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209978"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="e89c5-102">ICorDebugInstanceFieldSymbol:: GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="e89c5-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="e89c5-103">Získá posun v bajtech tohoto pole instance v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="e89c5-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e89c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e89c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e89c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e89c5-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="e89c5-106">Ukazatel na počet bajtů, které jsou tímto polem instance posunuty v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="e89c5-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e89c5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e89c5-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e89c5-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e89c5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e89c5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e89c5-109">Requirements</span></span>  
 <span data-ttu-id="e89c5-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e89c5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e89c5-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e89c5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e89c5-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e89c5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e89c5-113">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e89c5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89c5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e89c5-114">See also</span></span>

- [<span data-ttu-id="e89c5-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e89c5-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="e89c5-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e89c5-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
