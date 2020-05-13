---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageMetadata – metoda'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: d118f0c984663e0844783ff52859698dd5335058
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376136"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="b70e9-102">ICorDebugSymbolProvider:: GetAssemblyImageMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="b70e9-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="b70e9-103">Vrátí metadata ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="b70e9-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b70e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b70e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b70e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b70e9-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="b70e9-106">mimo Ukazatel na adresu objektu [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) , který obsahuje informace o velikosti a adrese sloučených metadat sestavení.</span><span class="sxs-lookup"><span data-stu-id="b70e9-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b70e9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b70e9-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b70e9-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b70e9-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b70e9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b70e9-109">Requirements</span></span>  
 <span data-ttu-id="b70e9-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b70e9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b70e9-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b70e9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b70e9-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b70e9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b70e9-113">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b70e9-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b70e9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b70e9-114">See also</span></span>

- [<span data-ttu-id="b70e9-115">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b70e9-115">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="b70e9-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b70e9-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
