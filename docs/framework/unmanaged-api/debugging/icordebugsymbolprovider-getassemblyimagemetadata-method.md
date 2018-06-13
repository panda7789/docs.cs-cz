---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata – metoda
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bf032f3bf525d2dca535e6f62dd65d5acd8e7f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420986"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="1db5b-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="1db5b-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="1db5b-103">Vrátí metadata z sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="1db5b-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db5b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1db5b-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1db5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1db5b-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="1db5b-106">[out] Ukazatel na adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje informace o velikosti a adresu metadata sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="1db5b-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1db5b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1db5b-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1db5b-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="1db5b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1db5b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1db5b-109">Requirements</span></span>  
 <span data-ttu-id="1db5b-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1db5b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1db5b-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1db5b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1db5b-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1db5b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1db5b-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1db5b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db5b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1db5b-114">See Also</span></span>  
 [<span data-ttu-id="1db5b-115">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1db5b-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="1db5b-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1db5b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
