---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageMetadata – metoda'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: 3ee80c18d3091406bf0bbd5b22c5f6021888906d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791660"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="5b5e0-102">ICorDebugSymbolProvider:: GetAssemblyImageMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="5b5e0-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="5b5e0-103">Vrátí metadata ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b5e0-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b5e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b5e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b5e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b5e0-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="5b5e0-106">mimo Ukazatel na adresu objektu [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) , který obsahuje informace o velikosti a adrese sloučených metadat sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b5e0-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b5e0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b5e0-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b5e0-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5b5e0-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b5e0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b5e0-109">Requirements</span></span>  
 <span data-ttu-id="5b5e0-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b5e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b5e0-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5b5e0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b5e0-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5b5e0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b5e0-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b5e0-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b5e0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b5e0-114">See also</span></span>

- [<span data-ttu-id="5b5e0-115">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b5e0-115">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="5b5e0-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5b5e0-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
