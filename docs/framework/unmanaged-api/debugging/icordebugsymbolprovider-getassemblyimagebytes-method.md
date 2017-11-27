---
title: "ICorDebugSymbolProvider::GetAssemblyImageBytes – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 127ebe82c32e9bf3d06c171d6cbf426d508eacaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="ac4f9-102">ICorDebugSymbolProvider::GetAssemblyImageBytes – metoda</span><span class="sxs-lookup"><span data-stu-id="ac4f9-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="ac4f9-103">Čte data z sloučené sestavení zadaný relativní virtuální adresy (RVA) v sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="ac4f9-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac4f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac4f9-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac4f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac4f9-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="ac4f9-106">[v] Relativní virtuální adresu (RVA) v sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="ac4f9-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="ac4f9-107">Počet bajtů ke čtení z sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="ac4f9-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="ac4f9-108">Ukazatel na adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje informace o vyrovnávací paměť s metadaty sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="ac4f9-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac4f9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac4f9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac4f9-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="ac4f9-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac4f9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac4f9-111">Requirements</span></span>  
 <span data-ttu-id="ac4f9-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac4f9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac4f9-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac4f9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac4f9-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac4f9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac4f9-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac4f9-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac4f9-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac4f9-116">See Also</span></span>  
 [<span data-ttu-id="ac4f9-117">ICorDebugSymbolProvider rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac4f9-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="ac4f9-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac4f9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
