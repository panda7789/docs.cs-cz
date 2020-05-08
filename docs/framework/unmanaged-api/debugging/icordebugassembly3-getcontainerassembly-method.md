---
title: ICorDebugAssembly3::GetContainerAssembly – metoda
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 068a08d70f2443edfe0970ec1ffb8cba9953c6b9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894852"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="cccb2-102">ICorDebugAssembly3::GetContainerAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="cccb2-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="cccb2-103">Vrátí sestavení kontejneru tohoto `ICorDebugAssembly3` objektu.</span><span class="sxs-lookup"><span data-stu-id="cccb2-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cccb2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cccb2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cccb2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cccb2-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="cccb2-106">Ukazatel na adresu objektu ICorDebugAssembly, který představuje sestavení kontejneru, nebo **hodnotu null** , pokud volání metody se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="cccb2-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cccb2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cccb2-107">Return Value</span></span>  
 <span data-ttu-id="cccb2-108">`S_OK`Pokud je volání metody úspěšné; `S_FALSE`v opačném případě `ppAssembly` je **hodnota null**.</span><span class="sxs-lookup"><span data-stu-id="cccb2-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cccb2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cccb2-109">Remarks</span></span>  
 <span data-ttu-id="cccb2-110">Pokud bylo toto sestavení sloučeno s ostatními v rámci jednoho sestavení kontejneru, vrátí tato metoda sestavení kontejneru.</span><span class="sxs-lookup"><span data-stu-id="cccb2-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="cccb2-111">Další informace a terminologii naleznete v tématu [ICorDebugProcess6:: EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cccb2-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cccb2-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cccb2-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cccb2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cccb2-113">Requirements</span></span>  
 <span data-ttu-id="cccb2-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cccb2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cccb2-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cccb2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cccb2-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cccb2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cccb2-117">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cccb2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cccb2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="cccb2-118">See also</span></span>

- [<span data-ttu-id="cccb2-119">Rozhraní ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="cccb2-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="cccb2-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cccb2-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
