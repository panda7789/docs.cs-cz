---
title: ICorDebugMergedAssemblyRecord::GetIndex – metoda
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c869c829acbfb9b0281537c7355229acbf2c5a7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752720"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="7e602-102">ICorDebugMergedAssemblyRecord::GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="7e602-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="7e602-103">Získá sestavení prefix index.</span><span class="sxs-lookup"><span data-stu-id="7e602-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e602-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e602-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e602-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e602-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="7e602-106">[out] Ukazatel na prefix index.</span><span class="sxs-lookup"><span data-stu-id="7e602-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e602-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e602-107">Remarks</span></span>  
 <span data-ttu-id="7e602-108">Prefix index se používá k zabránění kolize názvů v názvy typů sloučené metadat.</span><span class="sxs-lookup"><span data-stu-id="7e602-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e602-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7e602-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e602-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e602-110">Requirements</span></span>  
 <span data-ttu-id="7e602-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e602-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e602-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e602-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e602-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e602-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e602-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e602-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e602-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e602-115">See also</span></span>

- [<span data-ttu-id="7e602-116">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e602-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="7e602-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7e602-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
