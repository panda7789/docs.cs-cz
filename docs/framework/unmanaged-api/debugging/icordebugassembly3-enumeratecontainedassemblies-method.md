---
title: "ICorDebugAssembly3::EnumerateContainedAssemblies – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b927d065f26a13d496aec8cd6c8cbc69cf3a8bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="e9f47-102">ICorDebugAssembly3::EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="e9f47-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="e9f47-103">Získá enumerátor pro sestavení obsažené v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9f47-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9f47-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9f47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9f47-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="e9f47-106">[out] Ukazatel na adresu ICorDebugAssemblyEnum rozhraní objekt, který je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="e9f47-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9f47-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e9f47-107">Return Value</span></span>  
 <span data-ttu-id="e9f47-108">`S_OK`Pokud `ICorDebugAssembly3` objektu je kontejner, jinak hodnota `S_FALSE`, a výčtu je prázdný.</span><span class="sxs-lookup"><span data-stu-id="e9f47-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9f47-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9f47-109">Remarks</span></span>  
 <span data-ttu-id="e9f47-110">Symboly jsou potřebné k vytvoření výčtu obsažené sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9f47-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="e9f47-111">Pokud nejsou přítomen, vrátí metoda `S_FALSE`, a je k dispozici žádné platné enumerátor.</span><span class="sxs-lookup"><span data-stu-id="e9f47-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9f47-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="e9f47-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9f47-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9f47-113">Requirements</span></span>  
 <span data-ttu-id="e9f47-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9f47-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9f47-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9f47-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9f47-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9f47-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9f47-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9f47-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f47-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9f47-118">See Also</span></span>  
 [<span data-ttu-id="e9f47-119">Rozhraní ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="e9f47-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="e9f47-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9f47-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
