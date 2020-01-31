---
title: ICorDebugAssembly3::EnumerateContainedAssemblies – metoda
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 616675f839e562227558ece440bdfdf497747572
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784559"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="169d5-102">ICorDebugAssembly3::EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="169d5-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="169d5-103">Získá enumerátor pro sestavení obsažená v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="169d5-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="169d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="169d5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="169d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="169d5-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="169d5-106">mimo Ukazatel na adresu objektu rozhraní ICorDebugAssemblyEnum, který je enumerátorem.</span><span class="sxs-lookup"><span data-stu-id="169d5-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="169d5-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="169d5-107">Return Value</span></span>  
 <span data-ttu-id="169d5-108">`S_OK`, pokud je tento objekt `ICorDebugAssembly3` kontejnerem; v opačném případě `S_FALSE`a výčet je prázdný.</span><span class="sxs-lookup"><span data-stu-id="169d5-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="169d5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="169d5-109">Remarks</span></span>  
 <span data-ttu-id="169d5-110">Pro zobrazení výčtu obsažených sestavení jsou vyžadovány symboly.</span><span class="sxs-lookup"><span data-stu-id="169d5-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="169d5-111">Pokud nejsou k dispozici, metoda vrátí `S_FALSE`a není k dispozici žádný platný enumerátor.</span><span class="sxs-lookup"><span data-stu-id="169d5-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="169d5-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="169d5-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="169d5-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="169d5-113">Requirements</span></span>  
 <span data-ttu-id="169d5-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="169d5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="169d5-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="169d5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="169d5-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="169d5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="169d5-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="169d5-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="169d5-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="169d5-118">See also</span></span>

- [<span data-ttu-id="169d5-119">ICorDebugAssembly3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="169d5-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="169d5-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="169d5-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
