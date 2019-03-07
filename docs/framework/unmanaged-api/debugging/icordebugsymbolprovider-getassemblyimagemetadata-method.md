---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata Method
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cb255330937b00a987ee0d07f0332d04fe1746d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489978"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="5a51a-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span><span class="sxs-lookup"><span data-stu-id="5a51a-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="5a51a-103">Vrátí metadata ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="5a51a-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a51a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a51a-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a51a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a51a-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="5a51a-106">[out] Ukazatel na adresu [icordebugmemorybuffer –](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje informace o velikosti a adresa sloučené sestavení metadat.</span><span class="sxs-lookup"><span data-stu-id="5a51a-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a51a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a51a-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a51a-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5a51a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a51a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a51a-109">Requirements</span></span>  
 <span data-ttu-id="5a51a-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a51a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a51a-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a51a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a51a-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a51a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a51a-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a51a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a51a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a51a-114">See also</span></span>
- [<span data-ttu-id="5a51a-115">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a51a-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="5a51a-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5a51a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
