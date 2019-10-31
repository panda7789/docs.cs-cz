---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageMetadata – metoda'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: fb08df3b594e0c34dfe4ca791983b0c111239b23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138902"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="dfe39-102">ICorDebugSymbolProvider:: GetAssemblyImageMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="dfe39-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="dfe39-103">Vrátí metadata ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfe39-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfe39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfe39-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfe39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfe39-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="dfe39-106">mimo Ukazatel na adresu objektu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) , který obsahuje informace o velikosti a adrese sloučených metadat sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfe39-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfe39-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfe39-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dfe39-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dfe39-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfe39-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dfe39-109">Requirements</span></span>  
 <span data-ttu-id="dfe39-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfe39-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfe39-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dfe39-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfe39-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dfe39-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfe39-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfe39-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfe39-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfe39-114">See also</span></span>

- [<span data-ttu-id="dfe39-115">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dfe39-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="dfe39-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dfe39-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
