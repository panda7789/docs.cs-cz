---
title: ICorDebugAssembly3::EnumerateContainedAssemblies – metoda
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb84efe78568bbae03f76efc456fc8ae605e4db9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404833"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="020b6-102">ICorDebugAssembly3::EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="020b6-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="020b6-103">Získá enumerátor pro sestavení obsažené v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="020b6-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="020b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="020b6-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="020b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="020b6-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="020b6-106">[out] Ukazatel na adresu ICorDebugAssemblyEnum rozhraní objekt, který je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="020b6-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="020b6-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="020b6-107">Return Value</span></span>  
 <span data-ttu-id="020b6-108">`S_OK` Pokud `ICorDebugAssembly3` objektu je kontejner, jinak hodnota `S_FALSE`, a výčtu je prázdný.</span><span class="sxs-lookup"><span data-stu-id="020b6-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="020b6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="020b6-109">Remarks</span></span>  
 <span data-ttu-id="020b6-110">Symboly jsou potřebné k vytvoření výčtu obsažené sestavení.</span><span class="sxs-lookup"><span data-stu-id="020b6-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="020b6-111">Pokud nejsou přítomen, vrátí metoda `S_FALSE`, a je k dispozici žádné platné enumerátor.</span><span class="sxs-lookup"><span data-stu-id="020b6-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="020b6-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="020b6-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="020b6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="020b6-113">Requirements</span></span>  
 <span data-ttu-id="020b6-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="020b6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="020b6-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="020b6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="020b6-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="020b6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="020b6-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="020b6-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="020b6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="020b6-118">See Also</span></span>  
 [<span data-ttu-id="020b6-119">ICorDebugAssembly3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="020b6-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="020b6-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="020b6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
