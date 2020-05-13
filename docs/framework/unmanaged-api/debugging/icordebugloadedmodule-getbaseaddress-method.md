---
title: Metoda ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: d8c91c10577efd6a76af778cd01002de006df43a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209874"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="f496e-102">Metoda ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="f496e-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="f496e-103">Načte základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="f496e-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f496e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f496e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f496e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f496e-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="f496e-106">mimo Ukazatel na základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="f496e-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f496e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f496e-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f496e-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f496e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f496e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f496e-109">Requirements</span></span>  
 <span data-ttu-id="f496e-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f496e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f496e-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f496e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f496e-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f496e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f496e-113">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f496e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f496e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f496e-114">See also</span></span>

- [<span data-ttu-id="f496e-115">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="f496e-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="f496e-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f496e-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
