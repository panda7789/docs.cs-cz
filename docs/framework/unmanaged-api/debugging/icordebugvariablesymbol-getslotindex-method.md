---
title: ICorDebugVariableSymbol::GetSlotIndex – metoda
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: affe67006c9e37d55b0f9d107c92441da44c9ab8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138785"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="0a845-102">ICorDebugVariableSymbol::GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="0a845-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="0a845-103">Získá index spravované slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="0a845-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a845-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a845-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a845-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a845-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="0a845-106">[out] Ukazatel na lokální proměnná pozici indexu.</span><span class="sxs-lookup"><span data-stu-id="0a845-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a845-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0a845-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="0a845-108">v případě úspěšného ověření.</span><span class="sxs-lookup"><span data-stu-id="0a845-108">if successful.</span></span> `E_FAIL` <span data-ttu-id="0a845-109">Pokud je proměnná argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="0a845-109">if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a845-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a845-110">Remarks</span></span>  
 <span data-ttu-id="0a845-111">Spravované slotu index lokální proměnná slouží k načtení informací o metadatech proměnné</span><span class="sxs-lookup"><span data-stu-id="0a845-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a845-112">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0a845-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a845-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a845-113">Requirements</span></span>  
 <span data-ttu-id="0a845-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a845-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a845-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a845-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a845-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a845-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0a845-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0a845-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a845-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a845-118">See also</span></span>

- [<span data-ttu-id="0a845-119">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a845-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="0a845-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a845-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
