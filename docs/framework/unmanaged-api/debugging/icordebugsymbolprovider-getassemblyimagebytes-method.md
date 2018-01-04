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
ms.workload: dotnet
ms.openlocfilehash: 23c6dc836aefe1dd89431e003058ba2056eba3ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="267df-102">ICorDebugSymbolProvider::GetAssemblyImageBytes – metoda</span><span class="sxs-lookup"><span data-stu-id="267df-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="267df-103">Čte data z sloučené sestavení zadaný relativní virtuální adresy (RVA) v sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="267df-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="267df-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="267df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="267df-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="267df-106">[v] Relativní virtuální adresu (RVA) v sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="267df-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="267df-107">Počet bajtů ke čtení z sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="267df-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="267df-108">Ukazatel na adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje informace o vyrovnávací paměť s metadaty sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="267df-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="267df-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="267df-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="267df-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="267df-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="267df-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="267df-111">Requirements</span></span>  
 <span data-ttu-id="267df-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="267df-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="267df-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="267df-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="267df-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="267df-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="267df-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="267df-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="267df-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="267df-116">See Also</span></span>  
 [<span data-ttu-id="267df-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="267df-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="267df-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="267df-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
