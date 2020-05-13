---
title: 'ICorDebugMemoryBuffer:: GetStartAddress – metoda'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: 47369c744ee42fb03857a3e69063a04e4f509d0d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212344"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="e5239-102">ICorDebugMemoryBuffer:: GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="e5239-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="e5239-103">Získá počáteční adresu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e5239-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5239-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5239-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5239-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5239-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="e5239-106">mimo Ukazatel na počáteční adresu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e5239-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5239-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5239-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="e5239-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e5239-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5239-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5239-109">Requirements</span></span>  
 <span data-ttu-id="e5239-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5239-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5239-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5239-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5239-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e5239-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5239-113">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5239-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5239-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5239-114">See also</span></span>

- [<span data-ttu-id="e5239-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5239-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="e5239-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5239-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
