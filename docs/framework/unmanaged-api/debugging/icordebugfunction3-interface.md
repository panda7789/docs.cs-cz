---
title: Rozhraní ICorDebugFunction3
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: 71aa482cc2268da17f1376d8c305dd6a818d92d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213163"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="eae84-102">Rozhraní ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="eae84-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="eae84-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="eae84-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="eae84-104">Logicky rozšiřuje rozhraní ICorDebugFunction a poskytuje přístup k kódu z požadavku ReJIT.</span><span class="sxs-lookup"><span data-stu-id="eae84-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eae84-105">Metody</span><span class="sxs-lookup"><span data-stu-id="eae84-105">Methods</span></span>  
  
|<span data-ttu-id="eae84-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="eae84-106">Method</span></span>|<span data-ttu-id="eae84-107">Popis</span><span class="sxs-lookup"><span data-stu-id="eae84-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eae84-108">GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="eae84-108">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="eae84-109">Získá ukazatel rozhraní na [ICorDebugILCode](icordebugilcode-interface.md) , který obsahuje Il z aktivní žádosti ReJIT.</span><span class="sxs-lookup"><span data-stu-id="eae84-109">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eae84-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eae84-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eae84-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eae84-111">Requirements</span></span>  
 <span data-ttu-id="eae84-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eae84-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eae84-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eae84-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eae84-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eae84-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eae84-115">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eae84-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae84-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="eae84-116">See also</span></span>

- [<span data-ttu-id="eae84-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eae84-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="eae84-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="eae84-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="eae84-119">ReJIT: Průvodce</span><span class="sxs-lookup"><span data-stu-id="eae84-119">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
