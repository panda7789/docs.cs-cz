---
title: ICorDebugAssembly3::EnumerateContainedAssemblies – metoda
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa99e7289e0e86032f7bb85bbe209932f5c50d16
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627574"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="10126-102">ICorDebugAssembly3::EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="10126-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="10126-103">Získá enumerátor pro sestaveních obsažených v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="10126-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10126-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10126-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10126-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10126-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="10126-106">[out] Ukazatel na adresu objektu icordebugassemblyenum – rozhraní, která je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="10126-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10126-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="10126-107">Return Value</span></span>  
 <span data-ttu-id="10126-108">`S_OK` Pokud tento `ICorDebugAssembly3` objektu je kontejner, jinak `S_FALSE`, a výčet není prázdný.</span><span class="sxs-lookup"><span data-stu-id="10126-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10126-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10126-109">Remarks</span></span>  
 <span data-ttu-id="10126-110">Symboly jsou potřebné k vytvoření výčtu obsažené sestavení.</span><span class="sxs-lookup"><span data-stu-id="10126-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="10126-111">Pokud nejsou k dispozici, vrátí metoda `S_FALSE`, a je k dispozici žádné platným enumerátorem.</span><span class="sxs-lookup"><span data-stu-id="10126-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10126-112">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="10126-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10126-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10126-113">Requirements</span></span>  
 <span data-ttu-id="10126-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10126-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10126-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10126-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10126-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10126-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10126-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10126-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10126-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10126-118">See also</span></span>
- [<span data-ttu-id="10126-119">ICorDebugAssembly3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10126-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="10126-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="10126-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
