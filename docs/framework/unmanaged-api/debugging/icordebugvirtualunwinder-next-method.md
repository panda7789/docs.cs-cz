---
title: 'ICorDebugVirtualUnwinder:: Next – metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 06d5377ef123cc3f9c91fbfbcf0b0f17a14eb629
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790821"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="ec2b0-102">ICorDebugVirtualUnwinder:: Next – metoda</span><span class="sxs-lookup"><span data-stu-id="ec2b0-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="ec2b0-103">Přejde do kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="ec2b0-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec2b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec2b0-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec2b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec2b0-105">Parameters</span></span>  
 <span data-ttu-id="ec2b0-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="ec2b0-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec2b0-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ec2b0-107">Return Value</span></span>  
 <span data-ttu-id="ec2b0-108">`S_OK`, zda došlo k rewindu úspěšně, nebo `CORDBG_S_AT_END_OF_STACK`, Pokud unwind nelze dokončit, protože neexistují žádné další snímky.</span><span class="sxs-lookup"><span data-stu-id="ec2b0-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="ec2b0-109">Pokud je vrácena neúspěšná hodnota HRESULT, vrátí rozhraní API ICorDebug `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="ec2b0-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec2b0-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec2b0-110">Remarks</span></span>  
 <span data-ttu-id="ec2b0-111">Prohlížeč zásobníku by měl zajistit, že bude předávat pokrok, aby nakonec volání `Next` vrátilo neúspěch HRESULT nebo `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="ec2b0-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="ec2b0-112">Vrácení `S_OK` bez omezení může způsobit nekonečnou smyčku.</span><span class="sxs-lookup"><span data-stu-id="ec2b0-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec2b0-113">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ec2b0-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec2b0-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec2b0-114">Requirements</span></span>  
 <span data-ttu-id="ec2b0-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec2b0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec2b0-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ec2b0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec2b0-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ec2b0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec2b0-118">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec2b0-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec2b0-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec2b0-119">See also</span></span>

- [<span data-ttu-id="ec2b0-120">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ec2b0-120">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="ec2b0-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ec2b0-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
