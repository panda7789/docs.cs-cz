---
title: ICorDebugNativeFrame::CanSetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: b3758ac1a84092b8bf2678f9cc2c19c9d9961690
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137315"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="876e3-102">ICorDebugNativeFrame::CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="876e3-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="876e3-103">Získá hodnotu HRESULT, která označuje, zda je bezpečné nastavit ukazatel na instrukce (IP) na zadané umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="876e3-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="876e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="876e3-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="876e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="876e3-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="876e3-106">pro Požadované nastavení pro ukazatel na instrukci.</span><span class="sxs-lookup"><span data-stu-id="876e3-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="876e3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="876e3-107">Remarks</span></span>  
 <span data-ttu-id="876e3-108">Použijte metodu `CanSetIP` před voláním metody [ICorDebugNativeFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="876e3-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="876e3-109">Pokud `CanSetIP` vrátí jakýkoli HRESULT jiný než S_OK, můžete přesto vyvolat `ICorDebugNativeFrame::SetIP`, ale není nijak zaručeno, že ladicí program bude pokračovat v bezpečném a správného spuštění kódu, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="876e3-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="876e3-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="876e3-110">Requirements</span></span>  
 <span data-ttu-id="876e3-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="876e3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="876e3-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="876e3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="876e3-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="876e3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="876e3-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="876e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="876e3-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="876e3-115">See also</span></span>
