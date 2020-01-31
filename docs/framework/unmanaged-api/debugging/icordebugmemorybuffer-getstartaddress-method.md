---
title: 'ICorDebugMemoryBuffer:: GetStartAddress – metoda'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: f2b09c847a6bf577b78c8155f85f07b93877fbe9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793170"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="1ee76-102">ICorDebugMemoryBuffer:: GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="1ee76-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="1ee76-103">Získá počáteční adresu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1ee76-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ee76-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ee76-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ee76-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="1ee76-106">mimo Ukazatel na počáteční adresu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1ee76-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ee76-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ee76-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1ee76-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1ee76-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ee76-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ee76-109">Requirements</span></span>  
 <span data-ttu-id="1ee76-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ee76-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ee76-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1ee76-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ee76-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1ee76-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ee76-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ee76-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee76-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ee76-114">See also</span></span>

- [<span data-ttu-id="1ee76-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ee76-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="1ee76-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1ee76-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
