---
title: ICorDebugSymbolProvider::Metoda GetAssemblyImageBytes
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 6361b12802876ef480acbe1cc13f32b77ba0be49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178490"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="aeeee-102">ICorDebugSymbolProvider::Metoda GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="aeeee-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="aeeee-103">Čte data ze sloučeného sestavení dané relativní virtuální adresu (RVA) ve sloučeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="aeeee-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeeee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aeeee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aeeee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aeeee-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="aeeee-106">[v] Relativní virtuální adresa (RVA) ve sloučeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="aeeee-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="aeeee-107">Počet bajtů číst ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="aeeee-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="aeeee-108">Ukazatel na adresu objektu [ICorDebugMemoryBuffer,](icordebugmemorybuffer-interface.md) který obsahuje informace o vyrovnávací paměti se sloučenými metadaty sestavení.</span><span class="sxs-lookup"><span data-stu-id="aeeee-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aeeee-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aeeee-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aeeee-110">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="aeeee-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeeee-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aeeee-111">Requirements</span></span>  
 <span data-ttu-id="aeeee-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeeee-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeeee-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aeeee-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aeeee-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aeeee-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aeeee-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeeee-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeeee-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="aeeee-116">See also</span></span>

- [<span data-ttu-id="aeeee-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aeeee-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="aeeee-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aeeee-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
