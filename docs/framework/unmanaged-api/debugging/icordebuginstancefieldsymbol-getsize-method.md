---
title: 'ICorDebugInstanceFieldSymbol:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ff0ddc266ef9a3f5fabf56f43f1eba2c74e3a8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910178"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="e4f7b-102">ICorDebugInstanceFieldSymbol:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="e4f7b-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="e4f7b-103">Získá velikost pole instance v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e4f7b-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4f7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4f7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4f7b-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="e4f7b-106">mimo Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="e4f7b-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4f7b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4f7b-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4f7b-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e4f7b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4f7b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4f7b-109">Requirements</span></span>  
 <span data-ttu-id="e4f7b-110">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4f7b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4f7b-111">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e4f7b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4f7b-112">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4f7b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4f7b-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4f7b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f7b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4f7b-114">See also</span></span>

- [<span data-ttu-id="e4f7b-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4f7b-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="e4f7b-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e4f7b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
