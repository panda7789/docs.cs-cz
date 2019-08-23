---
title: Metoda ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85748106edb34b98f975a40bcc2617401536e271
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910103"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="53e1b-102">Metoda ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="53e1b-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="53e1b-103">Načte základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="53e1b-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53e1b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53e1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53e1b-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="53e1b-106">mimo Ukazatel na základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="53e1b-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53e1b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53e1b-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53e1b-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="53e1b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53e1b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53e1b-109">Requirements</span></span>  
 <span data-ttu-id="53e1b-110">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53e1b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e1b-111">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="53e1b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53e1b-112">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53e1b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53e1b-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53e1b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e1b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53e1b-114">See also</span></span>

- [<span data-ttu-id="53e1b-115">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53e1b-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="53e1b-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="53e1b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
