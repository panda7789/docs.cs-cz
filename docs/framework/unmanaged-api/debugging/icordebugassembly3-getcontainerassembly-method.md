---
title: ICorDebugAssembly3::GetContainerAssembly – metoda
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acb34ac2568ac88797441306820e6e762b5ac46e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409724"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="d73c2-102">ICorDebugAssembly3::GetContainerAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="d73c2-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="d73c2-103">Vrátí kontejner sestavení tohoto `ICorDebugAssembly3` objektu.</span><span class="sxs-lookup"><span data-stu-id="d73c2-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d73c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d73c2-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d73c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d73c2-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="d73c2-106">Ukazatel na adresu ICorDebugAssembly objekt, který představuje kontejner sestavení nebo **null** Pokud selže volání metody.</span><span class="sxs-lookup"><span data-stu-id="d73c2-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d73c2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d73c2-107">Return Value</span></span>  
 <span data-ttu-id="d73c2-108">`S_OK` Pokud je úspěšné volání metody; v opačném `S_FALSE`, a `ppAssembly` je **null**.</span><span class="sxs-lookup"><span data-stu-id="d73c2-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d73c2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d73c2-109">Remarks</span></span>  
 <span data-ttu-id="d73c2-110">Pokud toto sestavení byl sloučen s ostatními uvnitř sestavení jediný kontejner, tato metoda vrátí kontejner sestavení.</span><span class="sxs-lookup"><span data-stu-id="d73c2-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="d73c2-111">Další informace a přehled terminologie, najdete v článku [icordebugprocess6::enablevirtualmodulesplitting –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="d73c2-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d73c2-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="d73c2-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d73c2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d73c2-113">Requirements</span></span>  
 <span data-ttu-id="d73c2-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d73c2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d73c2-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d73c2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d73c2-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d73c2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d73c2-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d73c2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d73c2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d73c2-118">See Also</span></span>  
 [<span data-ttu-id="d73c2-119">ICorDebugAssembly3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d73c2-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="d73c2-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d73c2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
