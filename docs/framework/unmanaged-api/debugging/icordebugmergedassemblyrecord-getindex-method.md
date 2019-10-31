---
title: 'ICorDebugMergedAssemblyRecord:: GetIndex – metoda'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: 236bd8b22d6c3ec783d787f6c906ede3193cfc1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131409"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="0b0dd-102">ICorDebugMergedAssemblyRecord:: GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="0b0dd-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="0b0dd-103">Získá index předpony sestavení.</span><span class="sxs-lookup"><span data-stu-id="0b0dd-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b0dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b0dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b0dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b0dd-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="0b0dd-106">mimo Ukazatel na index předpony.</span><span class="sxs-lookup"><span data-stu-id="0b0dd-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b0dd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b0dd-107">Remarks</span></span>  
 <span data-ttu-id="0b0dd-108">Index předpony se používá k zamezení kolizí názvů v rámci sloučených názvů typů metadat.</span><span class="sxs-lookup"><span data-stu-id="0b0dd-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b0dd-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0b0dd-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b0dd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b0dd-110">Requirements</span></span>  
 <span data-ttu-id="0b0dd-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b0dd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b0dd-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0b0dd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b0dd-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0b0dd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b0dd-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b0dd-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b0dd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b0dd-115">See also</span></span>

- [<span data-ttu-id="0b0dd-116">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b0dd-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="0b0dd-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0b0dd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
