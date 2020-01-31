---
title: 'ICorDebugMergedAssemblyRecord:: GetIndex – metoda'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: c8fb5ace27fbf7fbebdaca5822af99cd6673e8cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793130"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="73197-102">ICorDebugMergedAssemblyRecord:: GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="73197-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="73197-103">Získá index předpony sestavení.</span><span class="sxs-lookup"><span data-stu-id="73197-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73197-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73197-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73197-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73197-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="73197-106">mimo Ukazatel na index předpony.</span><span class="sxs-lookup"><span data-stu-id="73197-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73197-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73197-107">Remarks</span></span>  
 <span data-ttu-id="73197-108">Index předpony se používá k zamezení kolizí názvů v rámci sloučených názvů typů metadat.</span><span class="sxs-lookup"><span data-stu-id="73197-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73197-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="73197-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73197-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73197-110">Requirements</span></span>  
 <span data-ttu-id="73197-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73197-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73197-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73197-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73197-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73197-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73197-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73197-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73197-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73197-115">See also</span></span>

- [<span data-ttu-id="73197-116">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73197-116">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="73197-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="73197-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
