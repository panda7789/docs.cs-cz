---
title: ICorDebugAssembly3::EnumerateContainedAssemblies – metoda
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9120119056fda3f16b4a0bf8bad839b74463d633
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959331"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="45513-102">ICorDebugAssembly3::EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="45513-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="45513-103">Získá enumerátor pro sestavení obsažená v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="45513-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45513-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45513-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45513-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45513-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="45513-106">mimo Ukazatel na adresu objektu rozhraní ICorDebugAssemblyEnum, který je enumerátorem.</span><span class="sxs-lookup"><span data-stu-id="45513-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45513-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="45513-107">Return Value</span></span>  
 <span data-ttu-id="45513-108">`S_OK`Pokud je `ICorDebugAssembly3` tento objekt kontejner; `S_FALSE`v opačném případě je výčet prázdný.</span><span class="sxs-lookup"><span data-stu-id="45513-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45513-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45513-109">Remarks</span></span>  
 <span data-ttu-id="45513-110">Pro zobrazení výčtu obsažených sestavení jsou vyžadovány symboly.</span><span class="sxs-lookup"><span data-stu-id="45513-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="45513-111">Pokud nejsou k dispozici, metoda vrátí `S_FALSE`hodnotu a není k dispozici žádný platný enumerátor.</span><span class="sxs-lookup"><span data-stu-id="45513-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45513-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="45513-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45513-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45513-113">Requirements</span></span>  
 <span data-ttu-id="45513-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45513-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45513-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="45513-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45513-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45513-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45513-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45513-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45513-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45513-118">See also</span></span>

- [<span data-ttu-id="45513-119">ICorDebugAssembly3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45513-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="45513-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="45513-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
