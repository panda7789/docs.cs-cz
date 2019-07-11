---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes – metoda
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaecbe3640e5da78c13a077611887c6b62d355a4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771514"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="8d87f-102">ICorDebugSymbolProvider::GetAssemblyImageBytes – metoda</span><span class="sxs-lookup"><span data-stu-id="8d87f-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="8d87f-103">Přečte data ze sloučeného sestavení sloučeného sestavení podle relativní virtuální adresu (RVA).</span><span class="sxs-lookup"><span data-stu-id="8d87f-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d87f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d87f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d87f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d87f-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="8d87f-106">[in] Relativní virtuální adresu (RVA) ve sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d87f-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="8d87f-107">Počet bajtů ke čtení ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d87f-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="8d87f-108">Ukazatel na adresu [icordebugmemorybuffer –](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje informace o vyrovnávací paměti s metadaty sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d87f-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d87f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d87f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d87f-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8d87f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d87f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d87f-111">Requirements</span></span>  
 <span data-ttu-id="8d87f-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d87f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d87f-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d87f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d87f-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d87f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d87f-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d87f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d87f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d87f-116">See also</span></span>

- [<span data-ttu-id="8d87f-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d87f-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8d87f-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8d87f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
