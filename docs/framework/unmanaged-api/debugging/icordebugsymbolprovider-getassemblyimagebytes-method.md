---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageBytes – metoda'
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: a555acb9e23098b0a0f70924032771b1ae18e88e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376119"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="f970c-102">ICorDebugSymbolProvider:: GetAssemblyImageBytes – metoda</span><span class="sxs-lookup"><span data-stu-id="f970c-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="f970c-103">Načte data ze sloučeného sestavení s ohledem na relativní virtuální adresu (RVA) ve sloučeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="f970c-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f970c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f970c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f970c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f970c-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="f970c-106">pro Relativní virtuální adresa (RVA) ve sloučeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="f970c-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="f970c-107">Počet bajtů, které mají být čteny ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="f970c-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="f970c-108">Ukazatel na adresu objektu [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) , který obsahuje informace o vyrovnávací paměti pro Sloučená metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="f970c-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f970c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f970c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f970c-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f970c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f970c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f970c-111">Requirements</span></span>  
 <span data-ttu-id="f970c-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f970c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f970c-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f970c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f970c-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f970c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f970c-115">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f970c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f970c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f970c-116">See also</span></span>

- [<span data-ttu-id="f970c-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f970c-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="f970c-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f970c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
