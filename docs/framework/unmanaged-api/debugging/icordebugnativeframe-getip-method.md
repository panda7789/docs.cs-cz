---
title: ICorDebugNativeFrame::GetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71e9149bafc866f89253c4318ac69f2705431e48
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765302"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="99b9b-102">ICorDebugNativeFrame::GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="99b9b-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="99b9b-103">Získá kód nativní posun umístění, ke kterému je aktuálně nastavený ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="99b9b-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99b9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99b9b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99b9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99b9b-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="99b9b-106">[out] Ukazatel na umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="99b9b-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99b9b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99b9b-107">Remarks</span></span>  
 <span data-ttu-id="99b9b-108">Pokud je aktivní rámec zásobníku, která je reprezentována tento icordebugnativeframe "–", je posun adresa další instrukci, která má být proveden.</span><span class="sxs-lookup"><span data-stu-id="99b9b-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="99b9b-109">Pokud tento rámec zásobníku není aktivní, posun je adresa další instrukci, který se spustí při opětovné aktivaci rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="99b9b-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99b9b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99b9b-110">Requirements</span></span>  
 <span data-ttu-id="99b9b-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99b9b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99b9b-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99b9b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99b9b-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99b9b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99b9b-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99b9b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b9b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99b9b-115">See also</span></span>
