---
title: ICorDebugAssembly3::EnumerateContainedAssemblies – metoda
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54ccb52468a530280527252e0e0c43cc9edbb2c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080953"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="37d00-102">ICorDebugAssembly3::EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="37d00-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="37d00-103">Získá enumerátor pro sestaveních obsažených v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="37d00-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37d00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37d00-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37d00-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37d00-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="37d00-106">[out] Ukazatel na adresu objektu icordebugassemblyenum – rozhraní, která je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="37d00-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37d00-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37d00-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="37d00-108">Pokud tento `ICorDebugAssembly3` objektu je kontejner, jinak `S_FALSE`, a výčet není prázdný.</span><span class="sxs-lookup"><span data-stu-id="37d00-108">if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37d00-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37d00-109">Remarks</span></span>  
 <span data-ttu-id="37d00-110">Symboly jsou potřebné k vytvoření výčtu obsažené sestavení.</span><span class="sxs-lookup"><span data-stu-id="37d00-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="37d00-111">Pokud nejsou k dispozici, vrátí metoda `S_FALSE`, a je k dispozici žádné platným enumerátorem.</span><span class="sxs-lookup"><span data-stu-id="37d00-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37d00-112">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="37d00-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37d00-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37d00-113">Requirements</span></span>  
 <span data-ttu-id="37d00-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37d00-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37d00-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37d00-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37d00-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37d00-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="37d00-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="37d00-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="37d00-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37d00-118">See also</span></span>

- [<span data-ttu-id="37d00-119">Rozhraní ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="37d00-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="37d00-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37d00-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
