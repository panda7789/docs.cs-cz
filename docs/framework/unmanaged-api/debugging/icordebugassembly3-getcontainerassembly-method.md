---
title: ICorDebugAssembly3::GetContainerAssembly – metoda
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9bd4cd44eca9b12ab8773fd75b6262579cfe8e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206080"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="cf765-102">ICorDebugAssembly3::GetContainerAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="cf765-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="cf765-103">Vrátí kontejner sestavení tohoto `ICorDebugAssembly3` objektu.</span><span class="sxs-lookup"><span data-stu-id="cf765-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf765-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf765-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf765-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf765-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="cf765-106">Ukazatel na adresu icordebugassembly – objekt, který představuje kontejner sestavení nebo **null** Pokud selže volání metody.</span><span class="sxs-lookup"><span data-stu-id="cf765-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf765-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cf765-107">Return Value</span></span>  
 <span data-ttu-id="cf765-108">`S_OK` Pokud volání metody, které úspěšně. v opačném případě `S_FALSE`, a `ppAssembly` je **null**.</span><span class="sxs-lookup"><span data-stu-id="cf765-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf765-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf765-109">Remarks</span></span>  
 <span data-ttu-id="cf765-110">Pokud toto sestavení bylo sloučeno s jinými uživateli uvnitř sestavení jednoho kontejneru, tato metoda vrátí sestavení kontejneru.</span><span class="sxs-lookup"><span data-stu-id="cf765-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="cf765-111">Další informace a terminologii, najdete v článku [icordebugprocess6::enablevirtualmodulesplitting –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="cf765-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf765-112">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cf765-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf765-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf765-113">Requirements</span></span>  
 <span data-ttu-id="cf765-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf765-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf765-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf765-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf765-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf765-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf765-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf765-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf765-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf765-118">See also</span></span>

- [<span data-ttu-id="cf765-119">ICorDebugAssembly3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf765-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="cf765-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cf765-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
