---
title: 'ICorDebugMergedAssemblyRecord:: GetIndex – metoda'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca304b90cee291ef86e225c2b0691631833e53a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917947"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="dacba-102">ICorDebugMergedAssemblyRecord:: GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="dacba-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="dacba-103">Získá index předpony sestavení.</span><span class="sxs-lookup"><span data-stu-id="dacba-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dacba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dacba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dacba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dacba-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="dacba-106">mimo Ukazatel na index předpony.</span><span class="sxs-lookup"><span data-stu-id="dacba-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dacba-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dacba-107">Remarks</span></span>  
 <span data-ttu-id="dacba-108">Index předpony se používá k zamezení kolizí názvů v rámci sloučených názvů typů metadat.</span><span class="sxs-lookup"><span data-stu-id="dacba-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dacba-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dacba-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dacba-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dacba-110">Requirements</span></span>  
 <span data-ttu-id="dacba-111">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dacba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dacba-112">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dacba-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dacba-113">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dacba-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dacba-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dacba-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dacba-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dacba-115">See also</span></span>

- [<span data-ttu-id="dacba-116">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dacba-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="dacba-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dacba-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
