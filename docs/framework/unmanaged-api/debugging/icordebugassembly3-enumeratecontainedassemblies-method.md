---
title: ICorDebugAssembly3::EnumerateContainedAssemblies – metoda
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: aebf499d7d25caef80782cc5661a57048dc5f6a9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894866"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="08070-102">ICorDebugAssembly3::EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="08070-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="08070-103">Získá enumerátor pro sestavení obsažená v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="08070-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08070-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08070-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08070-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08070-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="08070-106">mimo Ukazatel na adresu objektu rozhraní ICorDebugAssemblyEnum, který je enumerátorem.</span><span class="sxs-lookup"><span data-stu-id="08070-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08070-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="08070-107">Return Value</span></span>  
 <span data-ttu-id="08070-108">`S_OK`Pokud je `ICorDebugAssembly3` tento objekt kontejnerem; `S_FALSE`v opačném případě je výčet prázdný.</span><span class="sxs-lookup"><span data-stu-id="08070-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08070-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08070-109">Remarks</span></span>  
 <span data-ttu-id="08070-110">Pro zobrazení výčtu obsažených sestavení jsou vyžadovány symboly.</span><span class="sxs-lookup"><span data-stu-id="08070-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="08070-111">Pokud nejsou k dispozici, metoda vrátí `S_FALSE`hodnotu a není k dispozici žádný platný enumerátor.</span><span class="sxs-lookup"><span data-stu-id="08070-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08070-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="08070-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08070-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08070-113">Requirements</span></span>  
 <span data-ttu-id="08070-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08070-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08070-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08070-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08070-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="08070-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08070-117">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08070-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08070-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="08070-118">See also</span></span>

- [<span data-ttu-id="08070-119">Rozhraní ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="08070-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="08070-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08070-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
