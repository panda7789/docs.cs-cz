---
title: Metoda ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 6a1c8c94b3c45ac995501b84bb4a69d73e7db25b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209848"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="7d03b-102">Metoda ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="7d03b-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="7d03b-103">Získá velikost načteného modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="7d03b-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d03b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d03b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d03b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d03b-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="7d03b-106">mimo Ukazatel na počet bajtů v načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="7d03b-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d03b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d03b-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d03b-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7d03b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d03b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d03b-109">Requirements</span></span>  
 <span data-ttu-id="7d03b-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d03b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d03b-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d03b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d03b-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d03b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d03b-113">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d03b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d03b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d03b-114">See also</span></span>

- [<span data-ttu-id="7d03b-115">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="7d03b-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="7d03b-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d03b-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
