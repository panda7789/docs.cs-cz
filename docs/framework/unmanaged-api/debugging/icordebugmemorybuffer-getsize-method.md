---
title: 'ICorDebugMemoryBuffer:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 1bef2e2d0e1a1cef74c7568fdd2e9b7986500488
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212602"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="975f9-102">ICorDebugMemoryBuffer:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="975f9-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="975f9-103">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="975f9-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="975f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="975f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="975f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="975f9-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="975f9-106">mimo Ukazatel na velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="975f9-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="975f9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="975f9-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="975f9-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="975f9-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="975f9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="975f9-109">Requirements</span></span>  
 <span data-ttu-id="975f9-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="975f9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="975f9-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="975f9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="975f9-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="975f9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="975f9-113">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="975f9-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="975f9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="975f9-114">See also</span></span>

- [<span data-ttu-id="975f9-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="975f9-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="975f9-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="975f9-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
