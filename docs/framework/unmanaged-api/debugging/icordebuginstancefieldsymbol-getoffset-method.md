---
title: 'ICorDebugInstanceFieldSymbol:: GetOffset – metoda'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 453f691f414050905f5d73e201ebeed79e2aaf50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910206"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="42b9b-102">ICorDebugInstanceFieldSymbol:: GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="42b9b-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="42b9b-103">Získá posun v bajtech tohoto pole instance v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="42b9b-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42b9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42b9b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42b9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42b9b-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="42b9b-106">Ukazatel na počet bajtů, které jsou tímto polem instance posunuty v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="42b9b-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42b9b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42b9b-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42b9b-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="42b9b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42b9b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42b9b-109">Requirements</span></span>  
 <span data-ttu-id="42b9b-110">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42b9b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42b9b-111">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="42b9b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42b9b-112">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42b9b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42b9b-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42b9b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42b9b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42b9b-114">See also</span></span>

- [<span data-ttu-id="42b9b-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42b9b-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="42b9b-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="42b9b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
