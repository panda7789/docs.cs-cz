---
title: 'ICorDebugMergedAssemblyRecord:: GetIndex – metoda'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: b13e589e32b3317b567a4a89a5b48fc1299a1a84
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206955"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="40c5f-102">ICorDebugMergedAssemblyRecord:: GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="40c5f-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="40c5f-103">Získá index předpony sestavení.</span><span class="sxs-lookup"><span data-stu-id="40c5f-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40c5f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40c5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40c5f-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="40c5f-106">mimo Ukazatel na index předpony.</span><span class="sxs-lookup"><span data-stu-id="40c5f-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40c5f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40c5f-107">Remarks</span></span>  
 <span data-ttu-id="40c5f-108">Index předpony se používá k zamezení kolizí názvů v rámci sloučených názvů typů metadat.</span><span class="sxs-lookup"><span data-stu-id="40c5f-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40c5f-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="40c5f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c5f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40c5f-110">Requirements</span></span>  
 <span data-ttu-id="40c5f-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40c5f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c5f-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40c5f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40c5f-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="40c5f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40c5f-114">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40c5f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c5f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="40c5f-115">See also</span></span>

- [<span data-ttu-id="40c5f-116">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40c5f-116">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="40c5f-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40c5f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
