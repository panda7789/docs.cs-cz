---
title: Metoda ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 190c9114cffa537ba162b19abdf30d5a6aee87f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788450"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="9eafd-102">Metoda ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="9eafd-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="9eafd-103">Načte základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="9eafd-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eafd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9eafd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9eafd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9eafd-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="9eafd-106">mimo Ukazatel na základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="9eafd-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9eafd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9eafd-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9eafd-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9eafd-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eafd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9eafd-109">Requirements</span></span>  
 <span data-ttu-id="9eafd-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eafd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eafd-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9eafd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9eafd-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9eafd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eafd-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eafd-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eafd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9eafd-114">See also</span></span>

- [<span data-ttu-id="9eafd-115">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9eafd-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="9eafd-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9eafd-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
