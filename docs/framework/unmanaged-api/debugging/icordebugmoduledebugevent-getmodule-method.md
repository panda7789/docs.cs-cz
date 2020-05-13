---
title: 'ICorDebugModuleDebugEvent:: GetModule – metoda'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 1df71ddbf1ee76cc8202d8f9e263b9d95b4aaa09
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213358"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="ada03-102">ICorDebugModuleDebugEvent:: GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="ada03-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="ada03-103">Získá sloučený modul, který byl právě načten nebo uvolněn.</span><span class="sxs-lookup"><span data-stu-id="ada03-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ada03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ada03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ada03-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="ada03-106">mimo Ukazatel na adresu ICorDebugModule objektu, který reprezentuje sloučený modul, který byl právě načten nebo uvolněn.</span><span class="sxs-lookup"><span data-stu-id="ada03-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ada03-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ada03-107">Remarks</span></span>  
 <span data-ttu-id="ada03-108">Můžete zavolat metodu [GetEventKind –](icordebugdebugevent-geteventkind-method.md) a zjistit, zda byl modul načten nebo uvolněn.</span><span class="sxs-lookup"><span data-stu-id="ada03-108">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ada03-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ada03-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ada03-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ada03-110">Requirements</span></span>  
 <span data-ttu-id="ada03-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ada03-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada03-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ada03-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ada03-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ada03-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ada03-114">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada03-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada03-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ada03-115">See also</span></span>

- [<span data-ttu-id="ada03-116">ICorDebugModuleDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ada03-116">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="ada03-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ada03-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
