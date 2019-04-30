---
title: ICorDebugMemoryBuffer::GetStartAddress – metoda
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58649a0fc12ce63a1307af5d831dbf5e0d5a776a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916523"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="2e989-102">ICorDebugMemoryBuffer::GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="2e989-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="2e989-103">Získá počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2e989-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e989-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e989-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e989-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e989-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="2e989-106">[out] Ukazatel na počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2e989-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e989-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e989-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="2e989-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2e989-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e989-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e989-109">Requirements</span></span>  
 <span data-ttu-id="2e989-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e989-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e989-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e989-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e989-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e989-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e989-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e989-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e989-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e989-114">See also</span></span>

- [<span data-ttu-id="2e989-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e989-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="2e989-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2e989-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
