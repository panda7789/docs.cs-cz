---
title: ICorDebugAssembly3::EnumerateContainedAssemblies – metoda
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54ccb52468a530280527252e0e0c43cc9edbb2c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080953"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="6b4ef-102">ICorDebugAssembly3::EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="6b4ef-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="6b4ef-103">Získá enumerátor pro sestaveních obsažených v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b4ef-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b4ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b4ef-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b4ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b4ef-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="6b4ef-106">[out] Ukazatel na adresu objektu icordebugassemblyenum – rozhraní, která je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="6b4ef-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b4ef-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6b4ef-107">Return Value</span></span>  
 <span data-ttu-id="6b4ef-108">`S_OK` Pokud tento `ICorDebugAssembly3` objektu je kontejner, jinak `S_FALSE`, a výčet není prázdný.</span><span class="sxs-lookup"><span data-stu-id="6b4ef-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b4ef-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b4ef-109">Remarks</span></span>  
 <span data-ttu-id="6b4ef-110">Symboly jsou potřebné k vytvoření výčtu obsažené sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b4ef-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="6b4ef-111">Pokud nejsou k dispozici, vrátí metoda `S_FALSE`, a je k dispozici žádné platným enumerátorem.</span><span class="sxs-lookup"><span data-stu-id="6b4ef-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b4ef-112">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6b4ef-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b4ef-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b4ef-113">Requirements</span></span>  
 <span data-ttu-id="6b4ef-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b4ef-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b4ef-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b4ef-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b4ef-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b4ef-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b4ef-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b4ef-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b4ef-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b4ef-118">See also</span></span>

- [<span data-ttu-id="6b4ef-119">ICorDebugAssembly3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b4ef-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="6b4ef-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6b4ef-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
