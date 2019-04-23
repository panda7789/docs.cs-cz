---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata Method
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0be0722db374ff49541b3c4b68f295774f34163e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104127"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="d8bba-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span><span class="sxs-lookup"><span data-stu-id="d8bba-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="d8bba-103">Vrátí metadata ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8bba-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8bba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8bba-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8bba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8bba-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="d8bba-106">[out] Ukazatel na adresu [icordebugmemorybuffer –](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje informace o velikosti a adresa sloučené sestavení metadat.</span><span class="sxs-lookup"><span data-stu-id="d8bba-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8bba-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8bba-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8bba-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d8bba-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8bba-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8bba-109">Requirements</span></span>  
 <span data-ttu-id="d8bba-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8bba-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8bba-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8bba-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8bba-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8bba-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8bba-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8bba-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8bba-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8bba-114">See also</span></span>

- [<span data-ttu-id="d8bba-115">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8bba-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="d8bba-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d8bba-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
